---
name: article-workflow
description: Complete article creation workflow from research to publication-ready content, orchestrating all content creation agents.
---

# Article Creation Workflow / Рабочий процесс создания статьи

This command orchestrates the complete article creation process using specialized agents and skills.

## Workflow Overview / Обзор процесса

```
1. Research & Ideation → 2. Drafting → 3. Visual Planning → 4. Fact-Checking → 5. Editing → 6. SEO → 7. Social Amplification → 8. Publication
   (tech-content-strategist)  (tech-content-writer)  (visual-planning)  (tech-fact-checker)  (content-editor)  (seo-optimizer)  (social-amplification)  (final)
```

## Usage / Использование

```bash
/article-workflow
```

This will guide you through the complete process:

### Phase 1: Research & Strategy (Исследование и стратегия)

**Agent**: `tech-content-strategist`
**Skills**: `tech-trends-research`, `media-publishing-guidelines`

**Inputs / Входные данные**:
- Topic or business objective
- Target audience
- Target publications
- Business goals
- **Geographic focus** (Global / Russia / Mixed)

**Outputs / Результаты**:
- Trend research report
- 3-5 content idea briefs with IMPACT scores
- Keyword research
- Recommended angles and formats
- Saved to: `output/research/[date]-trend-research-brief.md`

**Questions You'll Be Asked**:
1. What topic or business objective are you focusing on?
2. Who is the target audience? (C-level, engineering leaders, developers, etc.)
3. Which publications are you targeting? (Forbes, TechCrunch, Habr, etc.)
4. What business goals drive this content? (thought leadership, lead gen, awareness)
5. **Geographic focus?** (Глобальный / Российский / Смешанный)

#### Исследование для российского рынка

При выборе российского рынка применяется расширенная методология:

**Источники исследования / Russian Research Sources**:
- **Отраслевые**: TAdviser, CNews Analytics, РУССОФТ, РАЭК
- **СМИ**: Habr, VC.ru, CNews, РБК, Коммерсантъ, Ведомости
- **Регуляторные**: Минцифры, ФСТЭК, ЦБ РФ, реестр ПО
- **Сообщества**: Highload++, DevOpsConf, TeamLead Conf

**Специфика российского исследования**:
- Yandex Wordstat вместо/вместе с Google Trends
- Анализ импортозамещения и реестра отечественного ПО
- Регуляторный контекст (152-ФЗ, 187-ФЗ, ГОСТ Р 57580)
- Сезонность: Q4 — бюджетирование, Q1 — освоение бюджетов

**Целевые публикации по аудиториям**:
| Аудитория | Издания |
|-----------|---------|
| CIO/ИТ-директора | CNews, TAdviser, Коммерсантъ |
| Разработчики | Habr, InfoQ Russia |
| Стартапы/продакты | VC.ru |
| Бизнес-лидеры | РБК, Ведомости, Forbes Russia |
| Финсектор | RBC Pro, Банковское обозрение |

### Phase 2: Content Ideation (Генерация идеи)

**Agent**: `tech-content-strategist`
**Skills**: `enterprise-storytelling`

Based on research, the strategist will:
- Generate 3-5 specific article concepts
- Score each using IMPACT framework
- Recommend format (opinion piece, tutorial, case study, etc.)
- Define key messages and proof points needed

**Outputs / Результаты**:
- Content idea briefs (one per concept)
- Recommended priority order
- Saved to: `output/ideas/[date]-content-brief-[title-slug].md`

**Your Decision**:
Select which content concept to develop into full article.

### Phase 3: Article Drafting (Создание черновика)

**Agent**: `tech-content-writer`
**Skills**: `technical-writing-standards`, `enterprise-storytelling`

**Inputs / Входные данные**:
- Selected content brief from Phase 2
- Supporting materials (case studies, data, quotes)
- Target word count
- Specific publication guidelines
- **Expert persona** (author voice)

#### Expert Personas / Персоны спикеров

Выберите роль автора для консистентного голоса статьи:

| Роль | Фокус | Темы |
|------|-------|------|
| **CEO / Генеральный директор** | Стратегическое видение | Бизнес-стратегия, рынок, импортозамещение |
| **CTO / VP Engineering** | Архитектура, масштаб | Infrastructure, DevOps, Platform engineering |
| **CPO / Директор по продукту** | Продуктовое развитие | Облачные продукты, Managed Services, PaaS |
| **CISO / Директор по ИБ** | Кибербезопасность | Security, Zero Trust, 152-ФЗ, ГОСТ Р 57580 |
| **CDO / Директор по данным** | Data Platform | Big Data, MLOps, Data Mesh, AI/ML |
| **CFO / Финансовый директор** | Cloud economics | FinOps, TCO, ROI, Budget optimization |
| **Engineering Lead** | Практический опыт | Разработка, архитектура, best practices |

**Persona Data**:
```yaml
persona:
  name: "[ФИО спикера]"
  title: "[Должность]"
  company: "[Компания]"
  expertise: "[Область экспертизы]"
  voice_traits:
    - [Характеристика 1]
    - [Характеристика 2]
```

**Влияние на контент**:
- **Тон**: Соответствует уровню и роли спикера
- **Глубина**: Техническая vs бизнес в зависимости от роли
- **Примеры**: Из области экспертизы спикера
- **Терминология**: Специфичная для домена

**Process**:
1. **Persona selection**: Choose or define expert persona
2. **Outline creation**: Writer creates detailed outline for approval
3. **First draft**: Complete draft following brief and persona voice
4. **Self-review**: Writer checks against quality checklist
5. **Delivery**: Draft with editorial notes

**Outputs / Результаты**:
- Article outline (for approval)
- Complete first draft
- Editorial notes (facts to verify, visuals needed, etc.)
- Saved to: `output/drafts/[date]-[title-slug]-draft-v1.md`

**Questions You'll Be Asked**:
1. Any specific examples or case studies to include?
2. Company messaging requirements or constraints?
3. Target word count and publication?
4. Deadline for draft?
5. **Language and publication style?** (EN / RU / publication-specific)

#### Drafting for Russian Publications / Написание для российских СМИ

При создании контента для российских изданий применяются специфические гайдлайны:

**Habr** (`columnist-wizard/skills/media/tech/habr.md`):
- Объём: 1,500-3,000 слов
- Технический уровень: 60-80%
- Обязательно: код, примеры, метрики
- Запрещено: маркетинг, пресс-релизный стиль
- Формат: `<cut/>` для превью

**VC.ru** (`columnist-wizard/skills/media/tech/vc-ru.md`):
- Объём: 800-2,000 слов
- Тон: разговорный, личный опыт
- Приветствуется: истории неудач, цифры, дискуссии
- Время публикации: Пн 16-18

**CNews** (`columnist-wizard/skills/media/tech/cnews.md`):
- Аудитория: CIO, ИТ-директора
- Форматы: экспертные цитаты (400-800 слов), колонки (1,500-2,500)
- Фокус: enterprise IT, госсектор

**РБК** (`columnist-wizard/skills/media/business/rbc.md`):
- Объём: 1,000-1,500 слов
- Требуется: данные в первых абзацах, 3+ источника
- Контринтуитивные углы приветствуются

**Ведомости** (`columnist-wizard/skills/media/business/vedomosti.md`):
- Аудитория: топ-менеджмент
- Стиль: аналитический, взвешенный
- Требуется: экспертный статус автора

### Phase 4: Visual Planning (Визуальное планирование)

**Purpose**: Определить визуальные элементы для усиления контента

**Inputs / Входные данные**:
- Draft article from Phase 3
- Target publication requirements

**Visual Elements Types / Типы визуальных элементов**:

| Тип | Когда использовать | Пример |
|-----|-------------------|--------|
| **Диаграмма архитектуры** | Объяснение системы | Cloud architecture, data flow |
| **Схема процесса** | Пошаговые инструкции | CI/CD pipeline, deployment flow |
| **Сравнительная таблица** | Сравнение опций | Feature comparison, pricing |
| **График/Chart** | Данные и статистика | Growth trends, performance metrics |
| **Инфографика** | Сложные концепции | Security layers, timeline |
| **Скриншот** | UI/UX демонстрация | Dashboard, configuration |
| **Code snippet** | Технические примеры | Implementation, config files |

**Process**:
1. **Scan draft**: Identify places that need visual support
2. **Prioritize**: Mark must-have vs nice-to-have visuals
3. **Describe**: Create detailed briefs for each visual
4. **Specify**: Define dimensions, style, format requirements

**Visual Brief Template**:
```yaml
visual:
  id: "visual-01"
  type: "architecture-diagram"
  location: "Section 2, after paragraph 3"
  purpose: "Show data flow between components"
  description: |
    Diagram showing:
    - User request flow
    - Load balancer distribution
    - Database replication
  style: "Clean, minimal, brand colors"
  dimensions: "1200x800px"
  format: "SVG preferred, PNG fallback"
  priority: "must-have"
  notes: "Include legend for icons"
```

**Outputs / Результаты**:
- Visual content plan with prioritized list
- Detailed briefs for each visual element
- Specifications for designer/illustrator
- Saved to: `output/visuals/[date]-[title-slug]-visual-plan.md`

**For Russian Publications / Для российских изданий**:
- **Habr**: Обязательны схемы и код для технических статей
- **VC.ru**: Инфографика повышает engagement
- **CNews**: Диаграммы архитектуры для enterprise-контента
- **РБК**: Графики с данными обязательны

---

### Phase 5: Fact-Checking (Проверка фактов)

**Agent**: `tech-fact-checker`
**Skills**: `fact-checking-methodology`

**Inputs / Входные данные**:
- Draft article from Phase 3
- Visual plan from Phase 4

**Process**:
1. **Identify claims**: Extract all factual claims
2. **Verify sources**: Trace statistics to primary sources
3. **Check technical accuracy**: Validate code, commands, configurations
4. **Test links**: Ensure all URLs work
5. **Document findings**: Create detailed fact-check report

**Outputs / Результаты**:
- Fact-check report with verification status
- List of corrections needed
- Source links for all verified claims
- Saved to: `output/reviews/[date]-[title-slug]-fact-check-report.md`

**Typical Timeline**: 1-2 days for thorough verification

### Phase 6: Editing (Редактирование)

**Agent**: `content-editor`
**Skills**: `editorial-excellence`, `technical-writing-standards`

**Inputs / Входные данные**:
- Fact-checked draft
- Fact-check report with corrections

**Process**:
1. **Structural edit**: Evaluate organization, flow, completeness
2. **Paragraph edit**: Improve clarity, transitions, development
3. **Sentence edit**: Strengthen language, voice, rhythm
4. **Quality review**: Check against editorial standards
5. **Provide feedback**: Detailed editorial report with tracked changes

**Outputs / Результаты**:
- Editorial review report
- Edited version with tracked changes
- Line-by-line edit notes
- Publication readiness assessment
- Saved to: `output/edited/[date]-[title-slug]-edited-v1.md`

**Typical Timeline**: 1-2 days for thorough edit

### Phase 7: SEO Optimization (SEO-оптимизация)

**Agent**: `seo-content-optimizer`
**Skills**: `media-publishing-guidelines`

**Inputs / Входные данные**:
- Edited article from Phase 5

**Process**:
1. **Keyword optimization**: Ensure natural keyword integration
2. **Headline optimization**: Create multiple headline options
3. **Meta description**: Write compelling meta description
4. **Readability check**: Verify scannability and structure
5. **Social optimization**: Prepare social media metadata
6. **Distribution strategy**: Recommend timing and platforms

**Outputs / Результаты**:
- SEO optimization report
- 3-5 headline options
- Meta description
- Social media copy and hashtags
- Distribution recommendations
- Final optimized article
- Saved to: `output/final/[date]-[title-slug]-final.md`

#### SEO для российского рынка / Russian Market SEO

**Поисковые системы**:
- Yandex: ~50% поиска в России
- Google: ~45% поиска в России
- Оптимизация под оба поисковика

**Yandex-специфика**:
- ИКС (Индекс качества сайта) важнее PageRank
- Региональность: учитывать геопривязку контента
- Яндекс.Вебмастер для мониторинга
- Турбо-страницы для ускорения

**Инструменты исследования ключевых слов**:
- Yandex Wordstat (wordstat.yandex.ru) — основной инструмент
- Яндекс.Вебмастер — запросы, по которым показывается сайт
- Serpstat — конкурентный анализ RU-сегмента
- Keys.so — кластеризация запросов

**Особенности русскоязычного SEO**:
- Морфология: учитывать склонения и падежи
- Транслитерация: английские термины на кириллице
- Локальные синонимы: «облако» vs «cloud», «кубернетес» vs «kubernetes»

**Социальные сети для дистрибуции**:
- Telegram-каналы — основной канал IT-аудитории
- Habr — кросс-постинг и обсуждения
- VC.ru — бизнес и продуктовая аудитория
- VK — охват широкой аудитории
- LinkedIn — международная экспертиза

### Phase 8: Social Amplification (Подготовка к дистрибуции)

**Purpose**: Подготовить контент для максимального охвата в социальных сетях

**Inputs / Входные данные**:
- Final optimized article from Phase 7
- SEO report with headlines and meta

**Social Platforms Strategy / Стратегия по платформам**:

#### Telegram (Основной канал для RU IT-аудитории)

```markdown
**Формат поста**:
- Hook (1-2 предложения) — цепляющее начало
- Key insight (2-3 предложения) — главный тезис
- Bullet points (3-5) — ключевые выводы
- CTA + ссылка

**Пример**:
🔥 [Провокационный факт или вопрос]

[Краткое раскрытие темы]

Что внутри:
• [Пункт 1]
• [Пункт 2]
• [Пункт 3]

👉 Читать: [ссылка]

**Timing**: Вт-Чт, 10:00-12:00 или 18:00-20:00 МСК
```

#### LinkedIn

```markdown
**Формат**:
- Professional hook
- Personal perspective (1st person)
- 3-5 key takeaways
- Question for engagement
- Link in comments (better reach)

**Timing**: Вт-Чт, 9:00-11:00 local time
**Hashtags**: 3-5 relevant (#CloudComputing #DevOps #TechLeadership)
```

#### Twitter/X Thread

```markdown
**Формат**:
1/ Hook tweet (compelling question or stat)
2-8/ Key points (one per tweet)
9/ Summary + CTA
10/ Link to full article

**Best practices**:
- Use numbered format (1/, 2/, etc.)
- Include visuals in 2-3 tweets
- End with engagement question
```

#### Habr (Cross-posting)

```markdown
- Полная версия или сокращённая с ссылкой на оригинал
- Адаптация под Habr-аудиторию (больше техники)
- Canonical URL на оригинал
```

#### VC.ru (Cross-posting)

```markdown
- Адаптация под бизнес/продуктовый угол
- Личный опыт и истории
- Более разговорный тон
```

**Process**:
1. **Adapt content**: Create platform-specific versions
2. **Create visuals**: Prepare social media images (1200x630 OG, 1080x1080 square)
3. **Schedule posts**: Plan publication timing for each platform
4. **Prepare responses**: Draft answers for expected questions/comments

**Outputs / Результаты**:
- Telegram post (RU)
- LinkedIn post (EN/RU)
- Twitter/X thread (EN)
- Cross-posting versions for Habr/VC.ru
- Social media images
- Publication schedule
- Saved to: `output/social/[date]-[title-slug]-social-kit.md`

**Social Kit Template**:
```yaml
social_kit:
  article_title: "[Title]"
  publication_date: "YYYY-MM-DD"

  telegram:
    post_text: "[Full post]"
    scheduled: "YYYY-MM-DD HH:MM"
    channel: "@channel_name"

  linkedin:
    post_text: "[Full post]"
    hashtags: ["#tag1", "#tag2"]
    scheduled: "YYYY-MM-DD HH:MM"

  twitter:
    thread:
      - "1/ [Tweet 1]"
      - "2/ [Tweet 2]"
    scheduled: "YYYY-MM-DD HH:MM"

  images:
    - og_image: "1200x630px"
    - square: "1080x1080px"
    - twitter_card: "1200x675px"
```

---

### Phase 9: Publication Preparation (Подготовка к публикации)

**Final Checklist**:
- [ ] All fact-check issues resolved
- [ ] Editorial feedback incorporated
- [ ] SEO optimization applied
- [ ] Headline finalized
- [ ] Meta description written
- [ ] Author bio prepared
- [ ] Disclosures added (if needed)
- [ ] Internal approvals obtained
- [ ] Images sourced and rights cleared
- [ ] Publication-specific formatting applied
- [ ] Final proofread complete

**Deliverables Package / Пакет материалов**:
```
output/final/[article-slug]/
├── [article-slug]-final.md          # Final article
├── metadata.json                     # Title, description, tags, author
├── images/                           # Article images
│   ├── hero-image.jpg
│   └── diagram-1.png
├── social/                           # Social media assets
│   ├── linkedin-post.md
│   ├── twitter-thread.md
│   └── og-image.jpg
└── reports/                          # Process documentation
    ├── trend-research-brief.md
    ├── content-brief.md
    ├── fact-check-report.md
    ├── editorial-report.md
    └── seo-report.md
```

## Workflow Options / Варианты рабочего процесса

### Fast Track (1 week)

For timely/news-driven content:
- **Day 1**: Research & ideation (Phases 1-2)
- **Day 2-3**: Drafting (Phase 3)
- **Day 4**: Fact-checking (Phase 4)
- **Day 5**: Editing (Phase 5)
- **Day 6**: SEO & finalization (Phase 6)
- **Day 7**: Publication

### Standard (2 weeks)

For thought leadership and complex content:
- **Week 1**: Research, ideation, drafting
- **Week 2**: Fact-checking, editing, optimization, publication

### Deep-Dive (4 weeks)

For major reports, whitepapers, or research-heavy content:
- **Week 1**: Extensive research and data gathering
- **Week 2**: Detailed drafting with multiple sections
- **Week 3**: Thorough fact-checking and technical review
- **Week 4**: Multi-round editing and finalization

## Output Directory Structure / Структура директорий

All content saved to workspace:

```
content-projects/
└── [project-name]/
    ├── research/
    │   ├── [date]-trend-research-brief.md
    │   └── [date]-competitive-analysis.md
    ├── ideas/
    │   ├── [date]-content-brief-idea-1.md
    │   ├── [date]-content-brief-idea-2.md
    │   └── [date]-content-brief-idea-3.md
    ├── drafts/
    │   ├── [date]-[slug]-draft-v1.md
    │   ├── [date]-[slug]-draft-v2.md
    │   └── [date]-[slug]-outline.md
    ├── visuals/                              # NEW: Visual Planning
    │   ├── [date]-[slug]-visual-plan.md
    │   └── briefs/
    │       ├── visual-01-architecture.md
    │       └── visual-02-chart.md
    ├── reviews/
    │   ├── [date]-[slug]-fact-check-report.md
    │   ├── [date]-[slug]-editorial-report.md
    │   └── [date]-[slug]-seo-report.md
    ├── edited/
    │   └── [date]-[slug]-edited-v1.md
    ├── social/                               # NEW: Social Amplification
    │   ├── [date]-[slug]-social-kit.md
    │   ├── telegram-post.md
    │   ├── linkedin-post.md
    │   ├── twitter-thread.md
    │   └── images/
    │       ├── og-image-1200x630.png
    │       └── square-1080x1080.png
    └── final/
        └── [slug]/
            ├── [slug]-final.md
            ├── metadata.json
            ├── images/
            ├── social/
            └── reports/
```

## Customization Options / Настройки

### Skip Phases

If you already have research or a draft:

```
/article-workflow --start-from=drafting
/article-workflow --start-from=fact-checking
/article-workflow --start-from=editing
```

### Agent Override

Use different agents if needed:

```
/article-workflow --writer=tech-content-writer --editor=content-editor
```

### Output Format

Specify output format preferences:

```
/article-workflow --format=markdown  # Default
/article-workflow --format=google-docs
/article-workflow --format=medium
```

### Geographic Focus / География

Specify market focus for research and optimization:

```bash
/article-workflow --geography=global   # International sources, English SEO
/article-workflow --geography=russia   # Russian sources, Yandex SEO, RU publications
/article-workflow --geography=mixed    # Both markets, bilingual approach
```

### Russian Publication Presets / Пресеты для российских СМИ

Quick start with publication-specific settings:

```bash
# Technical audience (developers, architects)
/article-workflow --publication=habr
# → Язык: RU, 1500-3000 слов, технический стиль, код обязателен

# Business/startup audience
/article-workflow --publication=vc-ru
# → Язык: RU, 800-2000 слов, личный опыт, разговорный стиль

# Enterprise IT (CIO, IT directors)
/article-workflow --publication=cnews
# → Язык: RU, 400-2500 слов, экспертный тон, enterprise фокус

# Business leaders
/article-workflow --publication=rbc
# → Язык: RU, 1000-1500 слов, данные обязательны, аналитический стиль

# Executive audience
/article-workflow --publication=vedomosti
# → Язык: RU, 1000-1500 слов, взвешенный тон, статусный автор
```

### Language / Язык

Specify content language:

```bash
/article-workflow --language=en-US     # American English
/article-workflow --language=en-UK     # British English
/article-workflow --language=ru        # Russian
```

### Expert Persona / Персона автора

Specify author voice for consistent tone:

```bash
/article-workflow --persona=cto        # CTO / VP Engineering voice
/article-workflow --persona=ciso       # Security expert voice
/article-workflow --persona=cpo        # Product leader voice
/article-workflow --persona=cdo        # Data leader voice
/article-workflow --persona=ceo        # Executive/strategic voice
/article-workflow --persona=engineer   # Hands-on engineering voice
```

### Social Amplification / Дистрибуция

Control social media preparation:

```bash
/article-workflow --social=full        # All platforms (default)
/article-workflow --social=ru-only     # Telegram + Habr + VC.ru only
/article-workflow --social=intl-only   # LinkedIn + Twitter only
/article-workflow --social=none        # Skip social phase
```

### Visual Planning / Визуальные материалы

Control visual content planning:

```bash
/article-workflow --visuals=full       # Full visual planning (default)
/article-workflow --visuals=minimal    # Only must-have visuals
/article-workflow --visuals=none       # Skip visual planning
```

## Success Metrics / Метрики успеха

Track these metrics for continuous improvement:

**Process Efficiency**:
- Time from start to publication-ready
- Number of revision cycles
- Fact-checking issues per article

**Content Quality**:
- Editorial acceptance rate
- Fact-check issue rate
- Readability scores

**Publication Success**:
- Acceptance rate by target publications
- Social shares and engagement
- Lead generation attribution
- Backlinks acquired

## Tips for Best Results / Советы для лучших результатов

1. **Invest in Research**: Quality research in Phase 1 saves time in all subsequent phases
2. **Clear Briefs**: Detailed content briefs lead to better first drafts
3. **Iterate**: Don't expect perfection in first draft—that's what editing is for
4. **Trust the Process**: Each phase adds value; resist temptation to skip
5. **Document Learnings**: Review what works and continuously improve
6. **Build Relationships**: Establish connections with target publications early
7. **Plan Ahead**: Start 2-4 weeks before desired publication date
8. **Engage Experts**: Involve technical SMEs early for accuracy
9. **Test Headlines**: Create multiple options and test with stakeholders
10. **Measure Results**: Track performance to inform future content strategy

## Troubleshooting / Решение проблем

**Problem**: Draft doesn't match brief
**Solution**: Review content brief with writer, provide specific examples of desired approach

**Problem**: Fact-checking reveals major issues
**Solution**: May need to revise draft significantly or even restart with corrected information

**Problem**: Article rejected by target publication
**Solution**: Review feedback, adapt for different publication, or revise and resubmit

**Problem**: Taking too long
**Solution**: Evaluate which phase is bottleneck, consider whether fast-track is more appropriate

## Related Commands / Связанные команды

- `/trend-research` - Run just research phase independently
- `/draft-article` - Start from drafting with existing brief
- `/fact-check` - Verify facts in existing content
- `/seo-optimize` - Optimize existing article for SEO
- `/write-column` - **[NEW]** Wizard for Russian business media (Forbes, RBC, Vedomosti, Habr, VC.ru)
- `/seo-create-article` - SEO-first article creation with keyword research

---

**Ready to start? Run `/article-workflow` and let's create exceptional content!**
