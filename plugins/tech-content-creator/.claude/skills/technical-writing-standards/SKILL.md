---
name: technical-writing-standards
description: Comprehensive technical writing standards for creating clear, accurate, and professional content for technology publications in Russian and English. Use when drafting or editing technical articles, documentation, or educational content.
---

# Technical Writing Standards

## Обязательные правила вывода
- Всегда отвечай **на русском**.
- Сохраняй артефакты в `outputs/tech-content-creator/skills/technical-writing-standards/{timestamp}_{кратко}.md` через Write tool; обновляй один файл по итерациям.
- Формат: цель/аудитория → бриф → структура/стандарты → примеры/термины → вывод/CTA → TODO → изменения vs прошлой версии.

## When to Use This Skill

- Drafting technical articles and blog posts
- Writing product documentation or whitepapers
- Creating tutorials and how-to guides
- Editing technical content for clarity and accuracy
- Ensuring consistency in technical writing across content
- Training new technical writers

## 3-итерационный контур
1) **Диагностика (1 ч):** аудитория/цель/канал, уровень сложности, бренд/тон, источники/версии, ограничения (NDA/PII). Черновой бриф + risk/decision log.
2) **Дизайн (1–2 ч):** структура (SCQA/Problem-Solution/How-to), глоссарий/термины, примеры/код/скриншоты, форматирование (шаги/таблицы/блоки). Заполни чек-лист.
3) **Верификация (0.5–1 ч):** фактчек/версии/термины, ясность/сжатие, читабельность, легал/бренд. Зафиксируй изменения и TODO.

## Core Writing Principles

### The Three Cs: Clear, Concise, Correct

**Clear / Ясно**
- One idea per sentence
- Short sentences (15-20 words average)
- Active voice as default
- Concrete examples over abstractions
- Define jargon on first use

**Concise / Кратко**
- Every word earns its place
- Eliminate redundancy
- Remove filler phrases
- Tighten verb constructions
- Cut unnecessary modifiers

**Correct / Корректно**
- Technical accuracy paramount
- Verify all claims
- Test all code examples
- Check version compatibility
- Cite sources properly

## Входы (собери до старта)
- Аудитория (новички/эксперты), цель (обучить/референс/решить), канал (док/блог/API).
- Источники фактов/примеров/кода, бренд/тон, версии, ограничения (NDA/PII/комплаенс).

## Выходы (обязательно зафиксировать)
- Структура/черновик, глоссарий, примеры/код/шаги, чек-лист качества.
- Статусы фактчека/версий/легала/бренда, TODO с владельцами/датами, изменения vs прошлой версии.

## Метрики и алерты
- Ясность/успех: время до выполнения инструкции, кол-во support тикетов по теме, ошибки/правки после публикации.
- Engagement: дочитывание, копирование примеров, возвраты.
- Алерты: высокий bounce/неудачные шаги, жалобы на неточность/версии, несоответствие бренду/тону.

## Качество ответа (checklist)
- Структура ясна (SCQA/Problem-Solution/How-to), шаги проверены, примеры рабочие.
- Терминология единообразна, глоссарий есть, ссылки/версии актуальны.
- Факты/код проверены, тон/бренд соблюдены, CTA понятен.
- TODO и изменения зафиксированы, логи обновлены.

## Red Flags
- Нет аудитории/цели; смешение уровней сложности; нет проверенных примеров.
- Жаргон/абстракции без объяснений; несогласованные термины/версии.
- Нет фактчека/легала; отсутствуют метрики/алерты; нет владельцев/сроков.

## Шаблоны и справочники
- Assets: `howto-template.md`, `api-doc-template.md`, `glossary-template.md`.
- References: `writing-checklist.md`, `term-consistency-guide.md`.

## Language and Style Standards

### Sentence Construction

**Preferred Structures**

✅ **Active Voice**: "Engineers deploy code 10x daily"
❌ **Passive Voice**: "Code is deployed 10x daily by engineers"

✅ **Strong Verbs**: "The service crashed"
❌ **Weak Verbs**: "The service experienced a failure event"

✅ **Specific**: "Reduced latency from 500ms to 50ms"
❌ **Vague**: "Significantly improved performance"

✅ **Concise**: "Use Kubernetes for orchestration"
❌ **Wordy**: "Utilize Kubernetes for the purpose of orchestration"

**Sentence Length Guidelines**

- **Short (5-10 words)**: Use for emphasis, after complex sentence, or to state key facts
- **Medium (15-20 words)**: Default target for most sentences
- **Long (25-30 words)**: Acceptable occasionally for explanatory content
- **Very Long (30+ words)**: Break into multiple sentences unless listing items

### Paragraph Structure

**Effective Paragraphs**

- **Topic sentence first**: State main idea clearly
- **Supporting sentences**: Develop idea with 2-4 sentences
- **One main idea**: Don't mix multiple concepts
- **Transition**: Connect to next paragraph

**Length Guidelines**

- **Russian / Русский**: 4-6 sentences (slightly longer acceptable)
- **English**: 3-5 sentences (brevity preferred)
- **Both**: Use short paragraphs (1-2 sentences) occasionally for emphasis

### Word Choice

**Precision Over Elegance**

✅ **Precise**: "The API returns a 404 error"
❌ **Elegant but vague**: "The system gracefully handles the absence"

**Common Word Choice Issues**

| Avoid / Избегать | Use / Использовать |
|-------------------|---------------------|
| utilize | use |
| in order to | to |
| due to the fact that | because |
| at this point in time | now |
| a number of | several, many |
| make a decision | decide |
| provide assistance | help |
| in the event that | if |
| has the ability to | can |
| it is important to note that | [often unnecessary, delete] |

### Technical Terminology

**Terminology Guidelines**

1. **Consistency**: Pick one term and stick with it
   - Container (not: pod, containerized unit, container instance—unless specifically referring to Kubernetes pods)

2. **Standard Terms**: Use industry-standard terminology
   - API (not: web service interface, unless contextually necessary)
   - CI/CD (not: continuous delivery pipeline, unless explaining)

3. **Define on First Use**: Explain acronyms and specialized terms
   - "Kubernetes (K8s), an open-source container orchestration system..."

4. **Appropriate Depth**: Match technical depth to audience
   - For developers: "Implemented exponential backoff with jitter"
   - For executives: "Implemented automatic retry logic"

## Technical Content Types

### Code Examples

**Best Practices**

✅ **Complete and Runnable**
```python
import requests

def fetch_user(user_id: int) -> dict:
    """Fetch user data from API."""
    response = requests.get(f"https://api.example.com/users/{user_id}")
    response.raise_for_status()
    return response.json()
```

❌ **Incomplete or Pseudo-code** (unless explicitly labeled as such)
```python
# Make API call
result = api.get(user)
```

**Code Example Guidelines**

- **Complete**: Include necessary imports and context
- **Tested**: Verify code actually works
- **Commented**: Explain non-obvious logic
- **Formatted**: Use proper indentation and style guides
- **Realistic**: Reflect real-world usage, not toy examples
- **Error Handling**: Show proper error handling when relevant
- **Language-Specific**: Follow language conventions (PEP 8 for Python, etc.)

**Code Block Formatting**

```markdown
### Syntax highlighting
```python
def example():
    pass
\```

### Inline code
Use `inline code` for short references like `kubectl apply` or `user_id`.

### Command line examples
```bash
$ kubectl get pods
NAME                     READY   STATUS
my-app-5d4b9c8f7-abc123  1/1     Running
\```
```

### API Documentation

**Endpoint Documentation Structure**

```markdown
### GET /api/users/{user_id}

Retrieves detailed information for a specific user.

**Parameters**

| Name | Type | Required | Description |
|------|------|----------|-------------|
| user_id | integer | Yes | Unique user identifier |
| include_posts | boolean | No | Include user's posts (default: false) |

**Request Example**

\```bash
curl -X GET "https://api.example.com/users/12345?include_posts=true" \
  -H "Authorization: Bearer YOUR_TOKEN"
\```

**Response**

Status: `200 OK`

\```json
{
  "id": 12345,
  "name": "Jane Smith",
  "email": "jane@example.com",
  "posts": [...]
}
\```

**Error Responses**

| Status | Description |
|--------|-------------|
| 400 | Invalid user_id format |
| 404 | User not found |
| 401 | Unauthorized |
```

### Architecture Diagrams and Descriptions

**Describing Technical Architecture**

1. **Start High-Level**: Overall system context
2. **Layer by Layer**: Decompose into components
3. **Interactions**: Explain data flows and APIs
4. **Rationale**: Why this architecture? Trade-offs?

**Example Structure**

```markdown
## Architecture Overview / Архитектура системы

Our microservices architecture consists of three layers:

**Presentation Layer**
- React SPA served via CDN
- API Gateway (Kong) for request routing
- OAuth2 authentication

**Application Layer**
- 12 microservices (Node.js, Go, Python)
- Event-driven communication via Kafka
- gRPC for synchronous service-to-service calls

**Data Layer**
- PostgreSQL for transactional data
- Redis for caching and sessions
- Elasticsearch for search

**Why This Architecture**

We chose microservices over a monolith because:
1. Team autonomy: 8 independent teams deploy separately
2. Technology flexibility: Use best tool for each service
3. Scaling: Scale individual services based on load

**Trade-offs**

- Increased operational complexity
- Distributed system challenges (consistency, debugging)
- Requires mature DevOps practices
```

## Russian Language Standards / Стандарты русского языка

### Формальность регистра / Formality Register

**Деловой стиль / Business Style**
- Использовать вежливую форму
- Избегать разговорных выражений
- Предпочитать полные формы слов

**Технический стиль / Technical Style**
- Термины на английском в скобках: "контейнер (container)"
- Аббревиатуры с расшифровкой: "REST (Representational State Transfer)"
- Принятые заимствования: "кластер", "инстанс", "воркер"

### Терминология / Terminology

**Устоявшиеся термины / Established Terms**

| English | Русский | Notes |
|---------|---------|-------|
| Container | Контейнер | Не "контейнеризованное приложение" |
| API | API (не переводится) | Интерфейс программирования приложений |
| Cloud | Облако, облачная среда | В зависимости от контекста |
| Deploy | Развернуть, деплой | "Деплой" как существительное |
| Kubernetes | Kubernetes, K8s | Не переводится |
| Microservice | Микросервис | Единая форма |
| Pipeline | Конвейер, пайплайн | В CI/CD — чаще "пайплайн" |
| Backend | Бэкенд | Не "серверная часть" в неформальном контексте |
| Frontend | Фронтенд | Не "клиентская часть" |

**Выбор между заимствованием и переводом / Borrowing vs. Translation**

- **Заимствование**: Когда термин устоялся в индустрии (Docker, Git, JSON)
- **Перевод**: Когда есть точный эквивалент (обработка ошибок, масштабирование)
- **Смешанная форма**: "REST API", "CI/CD pipeline"

### Структура предложений / Sentence Structure

**Длина предложения / Sentence Length**

В русском языке приемлемы более длинные предложения, но стремиться к:
- Короткие (до 15 слов): Для ключевых утверждений
- Средние (15-25 слов): Стандарт
- Длинные (25-35 слов): Для пояснительного контента

**Порядок слов / Word Order**

- Тема-рема: Известная информация → новая информация
- Важные слова — ближе к концу предложения
- Избегать сложных вложенных конструкций

## Style Guides to Follow

### Industry Standards

**For English Content**
- Microsoft Writing Style Guide (technical content)
- Google Developer Documentation Style Guide
- Chicago Manual of Style (long-form articles)
- AP Stylebook (journalism/news articles)

**For Russian Content**
- Справочник издателя и автора А. Э. Мильчина
- Правила русской орфографии и пунктуации
- Стандарты технической документации (ГОСТ)

### Publication-Specific Styles

Different publications have different preferences:

**Forbes, HBR** (Formal business)
- Serial comma (Oxford comma)
- Spell out numbers under 10
- Formal tone
- Minimal contractions

**TechCrunch, The Verge** (Tech journalism)
- Conversational tone acceptable
- Contractions OK
- Active voice strongly preferred
- News writing pyramid (most important first)

**Habr, VC.ru** (Russian tech)
- Деловой, но не слишком формальный стиль
- Англицизмы приемлемы
- Личный опыт и "мы" форма приветствуются

## Formatting and Presentation

### Headings and Hierarchy

**Heading Levels**

```markdown
# H1: Article Title (only one per document)

## H2: Major Sections

### H3: Subsections

#### H4: Minor Subsections (use sparingly)
```

**Heading Guidelines**

- Parallel structure (all questions, all statements, etc.)
- Descriptive (tell what section covers)
- Consistent capitalization (Title Case or Sentence case, pick one)
- Include keywords for SEO

### Lists and Bullets

**When to Use Bullets**

- Three or more related items
- Parallel items of equal weight
- Steps in a process (consider numbered list)
- Breaking up dense text

**Bullet List Guidelines**

- Parallel grammatical structure
- Consistent capitalization and punctuation
- 3-7 items ideal (consider subgrouping if more)
- Introduce with colon or complete sentence

**Numbered Lists**

Use for:
- Sequential steps
- Ranked items
- Items that will be referenced by number

### Tables

**Effective Table Usage**

✅ **Good table usage**: Comparing multiple items across dimensions

| Feature | Plan A | Plan B | Plan C |
|---------|--------|--------|--------|
| Storage | 10 GB | 100 GB | 1 TB |
| Users | 5 | 50 | Unlimited |
| Price | $10 | $50 | $200 |

❌ **Poor table usage**: Simple list better as bullets

| Item |
|------|
| First thing |
| Second thing |

### Emphasis and Formatting

**Bold**: Key terms, important warnings, emphasis
**Italic**: Publication names, introducing new terms, light emphasis
`Code`: Technical terms, file names, commands, code snippets

**Avoid**:
- EXCESSIVE CAPS
- Underlining (confuses with links)
- Multiple emphasis types on same text
- Overuse of bold (if everything is emphasized, nothing is)

## Quality Checklist

### Pre-Publication Review / Проверка перед публикацией

**Content Accuracy / Точность содержания**
- [ ] All technical claims verified
- [ ] Code examples tested and runnable
- [ ] Version numbers and compatibility checked
- [ ] Links tested and functional
- [ ] Statistics sourced and current

**Language Quality / Качество языка**
- [ ] Grammar and spelling checked
- [ ] Active voice predominant
- [ ] Jargon defined or avoided
- [ ] Sentence length varied
- [ ] Transitions smooth

**Structure / Структура**
- [ ] Clear heading hierarchy
- [ ] Logical flow
- [ ] Paragraphs focused (one idea each)
- [ ] Lists formatted properly
- [ ] Code blocks syntax-highlighted

**Style Consistency / Согласованность стиля**
- [ ] Terminology consistent
- [ ] Tone appropriate for audience
- [ ] Formatting consistent
- [ ] Publication style guide followed

**Readability / Читаемость**
- [ ] Scannable (headings, bullets, white space)
- [ ] Examples and illustrations included
- [ ] Concrete over abstract
- [ ] Value clear to reader

---

**References**
- `references/style-guide-checklist.md` - Comprehensive style guide
- `references/terminology-glossary.md` - Russian-English tech terms
- `assets/example-annotated-articles.md` - Examples with commentary

**Related Skills**
- `enterprise-storytelling` - Narrative techniques for technical content
- `editorial-excellence` - Advanced editing and refinement
