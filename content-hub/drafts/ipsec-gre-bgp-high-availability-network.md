---
title: "IPsec, GRE, BGP и автоматизация для отказоустойчивой сети"
description: "Практическое руководство по созданию отказоустойчивого гибридного соединения между on-premise и облаком VK Cloud с IPsec, GRE и BGP."
url: /blog/ipsec-gre-bgp-high-availability-network/
keywords:
  - ipsec vpn облако
  - гибридное подключение к облаку
  - отказоустойчивая сеть
  - gre туннель
  - bgp маршрутизация
audience: developers
tone: technological
mode: deep_expert
status: draft
source: https://habr.com/ru/companies/vktech/articles/972496/
created: 2025-12-25
---

# IPsec, GRE, BGP и немного автоматизации для высокой доступности вашей сети

Это практическое руководство по созданию отказоустойчивого гибридного соединения между локальной инфраструктурой и облаком VK Cloud. Не теория — готовые конфигурации и работающая архитектура.

## Проблематика

При миграции инфраструктуры в облако встаёт вопрос связности: как соединить локальную площадку с облачными ресурсами надёжно и безопасно. Стандартные подходы упираются в ограничения:

- SDN-технологии облаков не позволяют использовать привычные протоколы отказоустойчивости напрямую
- Требования к пропускной способности и безопасности различаются от проекта к проекту
- Привязка к одному провайдеру связи создаёт единую точку отказа
- Архитектура должна расти вместе с бизнесом без переделки с нуля

## Сценарий

Рассмотрим типичный кейс: промышленный объект, где выделенный канал до облака недоступен из-за географии или стоимости. Есть два интернет-провайдера — и это всё, с чем можно работать.

**Требования:**

- Использовать оба интернет-канала для резервирования
- Автоматически переключаться при отказе любого провайдера
- Сохранять работоспособность при сбое оборудования в облаке
- Шифровать весь трафик между площадками

## Архитектурное решение

Топология построена на избыточности каждого компонента:

- **On-Premise:** один маршрутизатор с двумя WAN-интерфейсами (по одному на каждого провайдера)
- **Облако:** два маршрутизатора в разных зонах доступности
- **Связность:** четыре GRE-туннеля (каждый облачный маршрутизатор соединён с on-premise через оба провайдера)
- **Внутренняя сеть облака:** VRRP между маршрутизаторами для единого виртуального IP

```
On-Premise Router
    ├── WAN1 (ISP1) ──► GRE1 ──► Cloud Router-1 (AZ-1)
    ├── WAN1 (ISP1) ──► GRE3 ──► Cloud Router-2 (AZ-2)
    ├── WAN2 (ISP2) ──► GRE2 ──► Cloud Router-1 (AZ-1)
    └── WAN2 (ISP2) ──► GRE4 ──► Cloud Router-2 (AZ-2)

Cloud Router-1 ◄──VRRP──► Cloud Router-2
        │                        │
        └────────┬───────────────┘
                 │ VIP: 10.200.0.1
                 ▼
          Private Network
           10.200.0.0/24
```

## Технологический стек

| Компонент | Назначение |
|-----------|------------|
| Ubuntu 24.04 LTS | ОС маршрутизаторов |
| Keepalived | VRRP для отказоустойчивости внутренней сети |
| Netplan | Декларативная конфигурация сети |
| IPtables | NAT и MSS clamping для GRE |
| GRE | Point-to-point туннели |
| StrongSwan | IPsec в транспортном режиме |
| FRR | BGP-маршрутизация |
| Terraform | Создание облачной инфраструктуры |
| Ansible | Конфигурация сервисов |

## Настройка инфраструктуры

### IP-адресация

| Сегмент | Подсеть |
|---------|---------|
| Локальная сеть | 192.168.1.0/24 |
| GRE-туннель 1 | 172.17.1.0/30 |
| GRE-туннель 2 | 172.17.2.0/30 |
| GRE-туннель 3 | 172.17.3.0/30 |
| GRE-туннель 4 | 172.17.4.0/30 |
| Облачная сеть | 10.200.0.0/24 |

### Процесс развёртывания

#### Этап 1: Terraform

Terraform создаёт облачное окружение:

- Приватная сеть и подсеть
- Security Group с правилами для GRE (протокол 47) и IPsec (UDP 500, 4500)
- Виртуальные машины маршрутизаторов с отключённой проверкой source/destination
- Cloud-init скрипт для начальной настройки сети

Скрипт cloud-init автоматически определяет WAN и LAN интерфейсы и генерирует статическую конфигурацию Netplan:

```bash
#!/bin/bash
WAN_IF=$(ip route | grep default | awk '{print $5}')
LAN_IF=$(ip -o link show | grep -v lo | grep -v $WAN_IF | awk -F': ' '{print $2}')

WAN_IP=$(ip addr show $WAN_IF | grep 'inet ' | awk '{print $2}')
WAN_GW=$(ip route | grep default | awk '{print $3}')
LAN_IP=$(ip addr show $LAN_IF | grep 'inet ' | awk '{print $2}')

cat > /etc/netplan/50-cloud-init.yaml <<EOF
network:
  version: 2
  ethernets:
    $WAN_IF:
      addresses: [$WAN_IP]
      routes:
        - to: default
          via: $WAN_GW
    $LAN_IF:
      addresses: [$LAN_IP]
EOF

netplan apply
```

#### Этап 2: Ansible

Ansible применяет роли для настройки каждого компонента:

**Роль base** — установка пакетов, включение IP forwarding

**Роль gre** — создание туннельных интерфейсов:

```yaml
# Netplan конфигурация GRE
network:
  version: 2
  tunnels:
    gre1:
      mode: gre
      local: <WAN_IP>
      remote: <ON_PREMISE_ISP1_IP>
      addresses:
        - 172.17.1.2/30
      mtu: 1400
```

**Роль ipsec** — защита GRE-туннелей через StrongSwan:

```
conn gre-tunnel-1
    left=<CLOUD_ROUTER_IP>
    right=<ON_PREMISE_IP>
    type=transport
    esp=aes256-sha256-modp2048
    ike=aes256-sha256-modp2048
    auto=start
```

**Роль frr** — BGP-маршрутизация с приоритизацией путей:

```
router bgp 65002
 bgp router-id 10.200.0.2
 neighbor 172.17.1.1 remote-as 65001
 neighbor 172.17.2.1 remote-as 65001

 address-family ipv4 unicast
  network 10.200.0.0/24
  neighbor 172.17.1.1 route-map PRIMARY in
  neighbor 172.17.2.1 route-map SECONDARY in

route-map PRIMARY permit 10
 set local-preference 200

route-map SECONDARY permit 10
 set local-preference 100
```

**Роль keepalived** — VRRP для внутренней сети облака:

```
vrrp_instance VI_1 {
    state MASTER
    interface eth1
    virtual_router_id 51
    priority 100
    virtual_ipaddress {
        10.200.0.1/24
    }
}
```

## Логика маршрутизации

BGP выбирает лучший путь на основе Local Preference. Чем выше значение — тем приоритетнее маршрут.

**Cloud Router-1 (master):**

| Приоритет | Туннель | Путь | Local Pref |
|-----------|---------|------|------------|
| 1 | GRE1 | через ISP1 | 200 |
| 2 | GRE2 | через ISP2 | 100 |

**Cloud Router-2 (backup):**

| Приоритет | Туннель | Путь | Local Pref |
|-----------|---------|------|------------|
| 1 | GRE3 | через ISP1 | 150 |
| 2 | GRE4 | через ISP2 | 50 |

При отказе ISP1 трафик автоматически переключается на туннели через ISP2. При отказе Cloud Router-1 — VRRP переносит VIP на Router-2, и трафик идёт через его туннели.

## Расширяемость решения

Архитектура масштабируется без переделки:

- **Выделенный канал:** добавляется как ещё один BGP-сосед с высшим приоритетом. Интернет-туннели становятся резервом автоматически.
- **Новые площадки:** подключаются по той же схеме с собственными туннелями.
- **Увеличение пропускной способности:** ECMP балансирует нагрузку между несколькими туннелями.

## Настройка On-Premise

Пример конфигурации для MikroTik RouterOS:

**GRE-интерфейсы:**

```routeros
/interface gre
add name=gre-cloud1-isp1 remote-address=<ROUTER1_IP> local-address=<ISP1_IP>
add name=gre-cloud1-isp2 remote-address=<ROUTER1_IP> local-address=<ISP2_IP>
add name=gre-cloud2-isp1 remote-address=<ROUTER2_IP> local-address=<ISP1_IP>
add name=gre-cloud2-isp2 remote-address=<ROUTER2_IP> local-address=<ISP2_IP>

/ip address
add address=172.17.1.1/30 interface=gre-cloud1-isp1
add address=172.17.2.1/30 interface=gre-cloud1-isp2
add address=172.17.3.1/30 interface=gre-cloud2-isp1
add address=172.17.4.1/30 interface=gre-cloud2-isp2
```

**IPsec:**

```routeros
/ip ipsec profile
add name=cloud dh-group=modp2048 enc-algorithm=aes-256 hash-algorithm=sha256

/ip ipsec peer
add name=router1 address=<ROUTER1_IP> profile=cloud exchange-mode=ike2
add name=router2 address=<ROUTER2_IP> profile=cloud exchange-mode=ike2

/ip ipsec identity
add peer=router1 secret="<PSK>"
add peer=router2 secret="<PSK>"
```

**BGP:**

```routeros
/routing bgp connection
add name=cloud1-gre1 remote.address=172.17.1.2 remote.as=65002 local.role=ebgp
add name=cloud1-gre2 remote.address=172.17.2.2 remote.as=65002 local.role=ebgp
add name=cloud2-gre3 remote.address=172.17.3.2 remote.as=65002 local.role=ebgp
add name=cloud2-gre4 remote.address=172.17.4.2 remote.as=65002 local.role=ebgp
```

## Выводы

Решение обеспечивает:

- **Высокую доступность** — избыточность на уровне каналов связи и оборудования
- **Безопасность** — IPsec шифрует весь межплощадочный трафик
- **Гибкость** — открытые стандарты, совместимость с любым оборудованием
- **Масштабируемость** — архитектура растёт без переделки базовых компонентов

Terraform и Ansible позволяют воспроизвести инфраструктуру за минуты и поддерживать её как код. Подход работает не только с VK Cloud, но и с любой облачной платформой, поддерживающей публичные IP и отключение source/destination check.
