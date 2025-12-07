---
name: seo-knowledge
description: База знаний для генерации SEO-контента
activation:
  - всегда активен для seo-wizard
---

# SEO Knowledge Skill

База знаний и правила для генерации SEO-контента.

---

## GENERATION RULES

### Обязательные правила

```yaml
STRICT_NO_PROMO: true
  - Никакой рекламы
  - Никаких призывов к покупке
  - Только полезный экспертный контент

NO_WATER: true
  - Без воды и пустых фраз
  - Каждое предложение несёт смысл
  - Конкретика вместо абстракций

NO_CLICHES: true
  - Без штампов ("в современном мире", "как известно")
  - Без канцеляризмов
  - Живой язык
```

### Редакционные правила

| Правило | Описание |
|---------|----------|
| `lead_with_value` | Начинать с пользы для читателя |
| `avoid_repetition` | Не повторять одни мысли |
| `avoid_long_nesting` | Короткие предложения |
| `logic_first` | Логика важнее стиля |
| `paragraphs_dense` | Плотные абзацы без воды |

---

## MODE CONFIGURATIONS

### balanced (по умолчанию)
```yaml
description: Стандартный сбалансированный режим
settings:
  depth: medium
  complexity: medium
  creativity: medium
  seo_focus: high
  readability: high
```

### deep_expert
```yaml
description: Для сложных технических тем
settings:
  depth: high
  complexity: high
  creativity: low
  seo_focus: medium
  readability: medium
  additional:
    - include_code_examples
    - technical_terminology
    - detailed_explanations
```

### light
```yaml
description: Упрощённая подача для широкой аудитории
settings:
  depth: low
  complexity: low
  creativity: medium
  seo_focus: high
  readability: very_high
  additional:
    - simple_language
    - many_examples
    - short_paragraphs
```

### strict_seo
```yaml
description: Максимальная SEO-оптимизация
settings:
  depth: medium
  complexity: low
  seo_focus: very_high
  readability: high
  additional:
    - keyword_density_1.5_2%
    - structured_snippets
    - faq_section
    - table_of_contents
```

### brand_heavy
```yaml
description: Акцент на тональность бренда
settings:
  depth: medium
  seo_focus: medium
  brand_voice: priority
  additional:
    - consistent_tone
    - brand_values_integration
    - positioning_aware
```

---

## TONE CONFIGURATIONS

### expert
```yaml
characteristics:
  - Профессиональный язык
  - Авторитетные утверждения
  - Ссылки на исследования
  - Экспертные оценки
example: >
  Выбор CRM-системы — стратегическое решение, влияющее на 
  эффективность всего отдела продаж. Согласно исследованиям, 
  компании с внедрённой CRM увеличивают конверсию на 29%.
```

### neutral
```yaml
characteristics:
  - Нейтральная подача
  - Без оценочных суждений
  - Фактологический стиль
  - Объективность
example: >
  CRM-системы помогают организовать работу с клиентами. 
  Существует несколько типов CRM, каждый из которых 
  подходит для определённых задач.
```

### technological
```yaml
characteristics:
  - Технические детали
  - Точная терминология
  - Примеры кода/конфигов
  - Архитектурные аспекты
example: >
  CRM-система использует реляционную базу данных для 
  хранения информации о клиентах. REST API позволяет 
  интегрировать её с внешними сервисами через webhooks.
```

---

## SEGMENT CONFIGURATIONS

### SMB (Малый и средний бизнес)
```yaml
characteristics:
  - Простой язык
  - Практические примеры
  - Акцент на ROI и экономию
  - Бюджетные решения
  - Быстрое внедрение
word_choice:
  prefer: ["простой", "быстрый", "выгодный", "понятный"]
  avoid: ["enterprise", "корпоративный", "сложный"]
```

### enterprise
```yaml
characteristics:
  - Формальный стиль
  - Кейсы крупных компаний
  - TCO и ROI расчёты
  - Масштабируемость
  - Безопасность и compliance
word_choice:
  prefer: ["масштабируемый", "надёжный", "интеграция", "SLA"]
  avoid: ["дешёвый", "простой", "быстрый старт"]
```

### developers
```yaml
characteristics:
  - Технический язык
  - Примеры кода
  - API и интеграции
  - Архитектурные паттерны
  - Производительность
word_choice:
  prefer: ["API", "SDK", "webhook", "REST", "документация"]
  avoid: ["простыми словами", "для чайников"]
```

### marketers
```yaml
characteristics:
  - Фокус на метриках
  - Конверсии и воронки
  - Аналитика
  - A/B тесты
  - Customer journey
word_choice:
  prefer: ["конверсия", "ROI", "воронка", "лид", "сегмент"]
```

### general
```yaml
characteristics:
  - Универсальный язык
  - Объяснение терминов
  - Широкий охват тем
  - Доступность
```

---

## CONSTRAINT RULES

### no_promo
```yaml
forbidden:
  - "Попробуйте наш продукт"
  - "Закажите прямо сейчас"
  - "Скидка", "акция", "бесплатно"
  - Любые призывы к покупке
  - Упоминание конкретного продукта как решения
```

### no_comparison
```yaml
forbidden:
  - "Лучше чем X"
  - "В отличие от конкурентов"
  - Прямые сравнения с конкурентами
  - Таблицы "мы vs они"
```

### no_hype
```yaml
forbidden:
  - "Революционный"
  - "Уникальный"
  - "Лучший на рынке"
  - "Инновационный"
  - Любые преувеличения
```

### no_pricing
```yaml
forbidden:
  - Конкретные цены
  - "От X рублей"
  - "Стоимость составляет"
  - Тарифные планы
```

---

## FACT BEHAVIOR

### strict (no_invented_facts)
```yaml
rules:
  - Только проверяемые факты
  - Ссылки на источники (где возможно)
  - Без выдуманных статистик
  - Без примеров-фантазий
```

### moderate (allow_generalized)
```yaml
rules:
  - Можно "обычно", "как правило", "часто"
  - Можно обобщённые утверждения
  - Без конкретных выдуманных цифр
```

### flexible (allow_noncritical)
```yaml
rules:
  - Можно примеры-иллюстрации
  - Можно гипотетические сценарии
  - Можно "представьте, что..."
```

---

## SEO REQUIREMENTS

### Keyword Usage
```yaml
density: 1-2%
placement:
  - Title tag (в начале)
  - H1 (основной ключ)
  - Первый абзац (первые 100 слов)
  - H2 заголовки (основные + LSI)
  - Alt-тексты изображений
  - Meta description
  - URL
distribution: равномерно по тексту
variation: использовать синонимы и словоформы
```

### Structure for Snippets
```yaml
elements:
  - Списки (маркированные и нумерованные)
  - Таблицы сравнения
  - Определения терминов (микроопределения)
  - Прямые ответы на вопросы
  - FAQ секция (для статей 2000+ слов)
```

### AI Search Optimization
```yaml
microdefinitions: true
  - Краткие определения в тексте
  - Формат: **Термин** — определение

extractive_friendly: true
  - Первое предложение раздела = ответ
  - Списки для перечислений
  - Чёткие утверждения

structured_blocks: true
  - Таблицы для сравнений
  - Пошаговые инструкции
  - Чек-листы

fact_assertions: true
  - Конкретные цифры и факты
  - Короткие предложения
  - Без вводных конструкций
```

---

## CONTENT STRUCTURE

### Введение (6-8% объёма)
```yaml
components:
  - Hook (цепляющее начало)
  - Проблема/контекст
  - Что получит читатель
  - Краткое содержание (для статей 2000+)
length: 150-200 слов
```

### Основная часть (75-80% объёма)
```yaml
structure:
  - H2 для главных разделов
  - H3 для подразделов
  - Визуальные разделители каждые 300-400 слов
components:
  - Определения
  - Примеры и кейсы
  - Списки и таблицы
  - Цитаты экспертов (если уместно)
```

### Заключение (4-6% объёма)
```yaml
components:
  - Резюме ключевых мыслей
  - Практические выводы
  - Call-to-action (информационный, НЕ рекламный)
length: 100-150 слов
```

---

## LSI GENERATION

Для темы генерировать 15-25 LSI-ключей:

```yaml
categories:
  synonyms: синонимы основных ключей
  related: связанные понятия
  actions: действия пользователя
  problems: проблемы, которые решает
  benefits: выгоды и преимущества
  features: характеристики и функции
```

### Пример для "CRM для малого бизнеса"
```yaml
lsi_keywords:
  - автоматизация продаж
  - управление клиентами
  - воронка продаж
  - клиентская база
  - лид-менеджмент
  - интеграция crm
  - облачная crm
  - отчёты по продажам
  - история взаимодействий
  - сегментация клиентов
  - email рассылки
  - мобильная crm
```

---

## OUTPUT FORMAT

```json
{
  "meta_title": "до 60 символов, ключ в начале",
  "meta_description": "150-160 символов, с ключом и CTA",
  "seo_url": "ключ-транслитом-через-дефис",
  "h1_variants": [
    "Вариант 1 с основным ключом",
    "Вариант 2 с вопросом",
    "Вариант 3 с числом/годом"
  ],
  "article_full_text": "Markdown текст статьи",
  "alt_texts": [
    "Описательный alt для изображения 1"
  ],
  "used_keywords": ["список", "использованных", "ключей"],
  "used_lsi": ["список", "lsi", "ключей"],
  "word_count": 2500,
  "reading_time": "10 мин",
  "editor_notes": [
    "Рекомендация 1 для редактора",
    "Рекомендация 2"
  ]
}
```

---

## FORBIDDEN PHRASES

Всегда заменять или удалять:

| Плохо | Замена |
|-------|--------|
| "В современном мире" | Удалить или "В 2024 году" |
| "Как известно" | Удалить, перейти к факту |
| "Не секрет, что" | Удалить |
| "Следует отметить" | Удалить |
| "Важно понимать" | Удалить или конкретизировать |
| "На сегодняшний день" | "Сейчас" или удалить |
| "Является" | Заменить на "—" |
| "Осуществлять" | "Делать", "проводить" |
| "В рамках" | Удалить или переформулировать |
