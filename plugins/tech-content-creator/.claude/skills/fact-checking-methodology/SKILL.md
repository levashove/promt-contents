---
name: fact-checking-methodology
description: Rigorous fact-checking methodology for technology content, ensuring accuracy, credibility, and journalistic standards. Use when verifying claims, statistics, technical assertions, or preparing content for publication.
---

# Fact-Checking Methodology

## Обязательные правила вывода
- Всегда отвечай **на русском**.
- Сохраняй артефакты в `outputs/tech-content-creator/skills/fact-checking-methodology/{timestamp}_{кратко}.md` через Write tool; обновляй один файл по итерациям.
- Формат: цель/аудитория → бриф → проверки/источники → выводы/решения → TODO → изменения vs прошлой версии.

## 3-итерационный контур
1) **Диагностика (0.5–1 ч):** собрать утверждения/данные/код, источники/версии, риски (легал/бренд/PII). Черновой бриф + риск/decision log.
2) **Проверка (1–2 ч):** иерархия источников (Tier1→Tier2→Tier3), технический прогон кода/команд, контекст/даты/версии, поиск контраргументов. Заполни чек-лист.
3) **Верификация (0.5–1 ч):** финальный статус (проверено/оспорено/удалено), список источников, дисклеймеры, алерты. Зафиксируй изменения и TODO.

## When to Use This Skill

- Verifying claims in draft articles before publication
- Checking technical accuracy of code examples and configurations
- Validating statistics, data, and research citations
- Reviewing competitor or third-party claims about technology
- Conducting pre-publication review for high-stakes content
- Training content creators on verification standards

## Fact-Checking Framework

### The Three-Layer Verification Model

**Layer 1: Source Verification / Проверка источников**
- Is the source authoritative and credible?
- Is the source primary, secondary, or tertiary?
- Does the source have potential bias or conflict of interest?
- Is the information current and still accurate?

**Layer 2: Claim Verification / Проверка утверждений**
- Can the claim be independently verified?
- Do multiple credible sources corroborate?
- Is necessary context provided?
- Are there counterexamples or exceptions?

**Layer 3: Technical Verification / Техническая проверка**
- Do code examples actually work?
- Are version numbers and compatibility accurate?
- Are configurations and commands correct?
- Are architecture descriptions technically sound?

## Source Hierarchy

### Tier 1: Primary Authoritative Sources (Highest Credibility)

**Official Technical Documentation**
- Vendor documentation (AWS, Azure, Google Cloud, etc.)
- Open source project official docs
- API references and specifications
- Release notes and changelogs

**Peer-Reviewed Research**
- Academic papers in reputable journals (IEEE, ACM)
- Conference proceedings (USENIX, SOSP, OSDI)
- arXiv preprints (with caution—not peer-reviewed)

**Original Research and Data**
- Primary research reports (Gartner, Forrester, IDC)
- Government and regulatory data
- Company financial reports and earnings calls
- Original survey data with methodology disclosed

**Direct Sources**
- Official company announcements and press releases
- Direct interviews with subject matter experts
- First-hand case studies and customer testimonials

## Входы (собери до старта)
- Перечень утверждений/данных/кодовых примеров, версии/окружения.
- Источники (Tier1/2/3), ограничения легал/бренд/PII, дедлайн.

## Выходы (обязательно зафиксировать)
- Статус по каждому утверждению (подтверждено/оспорено/удалено/дисклеймер).
- Список источников/ссылок, результаты прогонов кода, даты проверки.
- Дисклеймеры/легал примечания, TODO с владельцами/датами, изменения vs прошлой версии.

## Метрики и алерты
- Количество исправлений/ретрактов после публикации.
- Доля проверенных утверждений и кода, SLA на проверку.
- Алерты: сомнительные источники, устаревшие версии, PII/легал риск, несостыковки данных.

## Качество ответа (checklist)
- Источники ранжированы (Tier1→3), факты подтверждены ≥2 авторитетными, код прогнан.
- Даты/версии/контекст указаны, контраргументы рассмотрены.
- Дисклеймеры/ограничения присутствуют, логи обновлены, TODO/владельцы/сроки есть.

## Red Flags
- Опора на Tier3 без Tier1/2, отсутствие контекста/дат/версий.
- Непроверенный код/команды, нет подтверждений или ссылок.
- Легал/бренд/PII не проверены; нет алертов/чек-листа.

## Шаблоны и справочники
- Assets: `fact-check-worksheet.md`, `source-log-template.md`.
- References: `source-reliability-tiers.md`, `fact-check-checklist.md`.

### Tier 2: Secondary Authoritative Sources (Good Credibility)

**Reputable News Organizations**
- Reuters, Bloomberg, Wall Street Journal, Financial Times
- Technology-focused: The Information, Protocol
- Russian: РБК, Коммерсантъ, Ведомости

**Established Technology Publications**
- IEEE Spectrum, Communications of ACM
- InfoQ, The New Stack
- Well-edited tech media with fact-checking: Ars Technica, Wired

**Industry Analyst Commentary**
- Analyst interpretations and predictions (Gartner, Forrester)
- Market research firms
- Technology advisory firms

**Expert Perspectives**
- Recognized industry experts with track record
- University faculty in relevant specialization
- Book authors with credentials

### Tier 3: Use with Caution (Verify Independently)

**Vendor Marketing Materials**
- Whitepapers (check for bias)
- Case studies (verify if possible)
- Product comparison documents
- Blog posts from vendors

**General Technology Media**
- News aggregators and general tech blogs
- Unedited contributed content
- Press release republishing

**Community Sources**
- Stack Overflow (good for how-to, not for claims)
- Reddit, HackerNews (useful for discussion, not facts)
- Personal blogs (unless from recognized expert)

### Tier 4: Red Flags (Require Extensive Verification)

**Questionable Sources**
- Anonymous sources without corroboration
- Sources with clear conflicts of interest
- Clickbait or sensationalist publications
- Circular citations (A cites B, B cites A)
- Outdated information presented as current
- Unsourced statistics ("studies show...")

## Verification Checklists

### Statistics and Data Checklist

When encountering any statistic, verify:

- [ ] **Source identified**: Where does this number come from?
- [ ] **Original source accessed**: Not cited secondhand
- [ ] **Methodology disclosed**: How was data collected?
- [ ] **Sample size adequate**: Large enough to be meaningful?
- [ ] **Date confirmed**: When was data collected/published?
- [ ] **Context provided**: What do these numbers actually mean?
- [ ] **Definitions clear**: What exactly is being measured?
- [ ] **Limitations acknowledged**: What doesn't this data tell us?

**Example: Verifying "67% of AI projects fail"**

✅ **Proper Verification**:
1. Find original source: [Gartner research, July 2022]
2. Check methodology: [Survey of 2,500 enterprises]
3. Verify definition of "failure": [Didn't reach production within 2 years]
4. Add context: "According to Gartner's 2022 survey of 2,500 enterprises, 67% of AI initiatives failed to reach production within two years of starting development."

❌ **Insufficient Verification**:
"67% of AI projects fail [source: TechBlog.com article]"
- Secondary source, no methodology, no date, no context

### Technical Claims Checklist

For any technical assertion:

- [ ] **Test it**: If possible, reproduce the claim
- [ ] **Check versions**: Version-specific features accurately stated?
- [ ] **Verify compatibility**: Integrations work as described?
- [ ] **Validate best practices**: Is this actually recommended?
- [ ] **Check deprecations**: Is feature still supported?
- [ ] **Confirm limits**: Are performance/scale claims accurate?
- [ ] **Review security**: Are security implications correct?

**Example: Verifying "Kubernetes automatically scales pods"**

✅ **Accurate with Context**:
"Kubernetes can automatically scale pods using Horizontal Pod Autoscaler (HPA), which adjusts replica count based on CPU utilization, memory, or custom metrics. However, this requires configuration—autoscaling is not enabled by default."

❌ **Misleading**:
"Kubernetes automatically scales pods" (implies it's automatic without setup)

### Code Examples Checklist

For any code snippet in content:

- [ ] **Actually run it**: Execute code to verify it works
- [ ] **Complete**: Includes necessary imports and context
- [ ] **Correct syntax**: No syntax errors
- [ ] **Version-specific**: Works with versions mentioned
- [ ] **Best practices**: Follows language/framework conventions
- [ ] **Error handling**: Handles errors appropriately
- [ ] **Security**: No vulnerabilities or insecure practices
- [ ] **Tested**: Ideally with automated tests

**Example: Python Code Verification**

```python
# ❌ UNVERIFIED - May not work
import requests
data = requests.get("https://api.example.com").json()

# ✅ VERIFIED - Complete and working
import requests
from typing import Dict, Optional

def fetch_api_data() -> Optional[Dict]:
    """Fetch data from API with proper error handling."""
    try:
        response = requests.get(
            "https://api.example.com/data",
            timeout=10
        )
        response.raise_for_status()
        return response.json()
    except requests.RequestException as e:
        print(f"API request failed: {e}")
        return None
```

### Quote and Attribution Checklist

For any quote or attribution:

- [ ] **Exact wording**: Quote is word-for-word accurate
- [ ] **Proper attribution**: Correct name, title, company
- [ ] **Context preserved**: Quote meaning not distorted
- [ ] **Recent and relevant**: Quote is from appropriate timeframe
- [ ] **Paraphrasing accurate**: If paraphrased, meaning preserved
- [ ] **Credentials verified**: Person's expertise confirmed
- [ ] **Permission obtained**: If needed for case studies

### Company and Product Claims Checklist

For claims about companies, products, or market:

- [ ] **Company name correct**: Proper spelling and capitalization
- [ ] **Product name current**: Not outdated or rebranded
- [ ] **Leadership current**: Titles and positions up-to-date
- [ ] **Financials accurate**: Revenue, valuation, funding verified
- [ ] **Market position verified**: "Leading," "first," "largest" claims checked
- [ ] **Product capabilities accurate**: Features exist as described

## Common Fact-Checking Scenarios

### Scenario 1: Vague Statistics

**Claim**: "Most companies are adopting Kubernetes"

**Issues**:
- "Most" is undefined (>50%? >75%?)
- "Companies" is vague (all companies? Fortune 500? Tech companies?)
- No timeframe
- No source

**Fact-Checked Version**:
"According to the CNCF's 2023 annual survey, 66% of respondents reported using Kubernetes in production, up from 58% in 2022. The survey included 4,800 respondents primarily from technology and cloud-native companies."

### Scenario 2: Outdated Information

**Claim**: "Docker is the only way to run containers"

**Issues**:
- Was never fully accurate
- Increasingly outdated (containerd, CRI-O, Podman)
- Doesn't account for OCI standards

**Fact-Checked Version**:
"While Docker pioneered container tooling and remains widely used, modern container ecosystems support OCI-standard runtimes like containerd (used by Kubernetes), CRI-O, and Podman, giving teams multiple options."

### Scenario 3: Misleading Comparisons

**Claim**: "Our service is 10x faster than the competition"

**Issues**:
- Which competitor?
- Under what conditions?
- What metric (latency, throughput)?
- Benchmark methodology?

**Fact-Checked Version**:
"In our benchmark tests using Apache JMeter with 1,000 concurrent users, our service achieved median response times of 45ms compared to 450ms for Service X and 380ms for Service Y. Full methodology and results: [link]"

### Scenario 4: Circular Citations

**Claim**: "95% of data breaches are caused by human error"

**Investigation Reveals**:
- TechBlog A cites Industry Report B
- Industry Report B cites News Article C
- News Article C cites TechBlog A (circular!)
- Original primary source cannot be found

**Fact-Checking Action**:
- Flag as unverifiable
- Search for actual research on topic
- Either find credible source or remove claim
- Lesson: Always trace to primary source

## International and Russian Market Fact-Checking

### Verifying Russian Market Data

**Trusted Russian Sources / Надежные российские источники**:

**Official Statistics**
- Росстат (Federal State Statistics Service)
- Банк России (Central Bank)
- Минцифры (Ministry of Digital Development)

**Market Research**
- РУССОФТ reports
- iKS-Consulting
- CNews Analytics
- Data Insight

**News and Analysis**
- РБК, Коммерсантъ, Ведомости (business press)
- Habr (tech community, verify claims)
- VC.ru (startup ecosystem)

**Challenges**:
- Less transparency than Western markets in some areas
- Russian vs. international methodology differences
- Currency and economic data requires careful dating
- Regulatory environment changes require recency checks

### Cross-Border Verification

When writing for both Russian and international audiences:

- Verify statistics apply to claimed geography
- Check if international trends mirror Russian market
- Note regional differences when relevant
- Use locale-appropriate sources for each market

## Fact-Checking Tools and Techniques

### Search Techniques

**Finding Original Sources**:
- Put statistic in quotes: "67% of AI projects fail"
- Search with "original report" or "methodology"
- Use site-specific search: `site:gartner.com kubernetes adoption`
- Try date range limits: `after:2023-01-01`
- Reverse image search for charts/infographics

**Verifying Claims**:
- Search for contradictory information
- Look for expert commentary or analysis
- Check fact-checking sites (Snopes, FactCheck.org)
- Verify through multiple independent sources

### Documentation Verification

**Official Docs**:
- Always check official documentation for technical claims
- Verify version-specific features
- Check deprecation notices
- Review release notes for changes

**GitHub and Open Source**:
- Check repository for features claimed
- Review issues for known problems
- Verify version tags and release notes
- Check community discussions

### Expert Consultation

When claims are hard to verify:
- Consult internal subject matter experts
- Reach out to technology experts in network
- Ask in professional communities (with discretion)
- Interview original researchers or practitioners

## Handling Unverifiable Claims

### When Verification Fails

**Option 1: Remove the Claim**
If claim is central but unverifiable, consider removing or replacing.

**Option 2: Add Qualifier**
"According to [source], ..." or "Based on limited available data..."

**Option 3: Acknowledge Limitations**
"While comprehensive data isn't available, industry observations suggest..."

**Option 4: Request Original Source**
Ask content creator or SME for original source and verification.

### Flagging Uncertainty

Be transparent about confidence levels:

✅ **High Confidence**: "According to AWS documentation..."
✅ **Medium Confidence**: "Industry analysts estimate..."
✅ **Low Confidence**: "While exact figures aren't public, estimates range from..."
❌ **Unverifiable**: [Remove or add strong qualifier]

## Fact-Checking Report Template

See `references/fact-check-report-template.md` for comprehensive bilingual template.

**Quick Format**:

```markdown
# Fact-Check: [Article Title]

## Summary
- Claims checked: [X]
- Verified: [Y] ✅
- Need correction: [Z] ⚠️
- Unverifiable: [W] ❌

## Critical Issues
1. [Claim] - [Issue] - [Suggested fix]

## Verification Notes
[Detailed findings and sources]
```

## Best Practices

### Fact-Checking Workflow

1. **First read**: Mark all factual claims requiring verification
2. **Prioritize**: Start with statistics, technical claims, quotes
3. **Trace sources**: Always go to primary source
4. **Document**: Record verification process and sources
5. **Flag issues**: Clearly mark problems with severity
6. **Suggest fixes**: Provide corrected versions with sources
7. **Follow up**: Verify corrections implemented

### Quality Standards

- **Multi-source rule**: Key claims require 2-3 independent sources
- **Recency rule**: Data should be from last 12-24 months (tech moves fast)
- **Primary source rule**: Always verify against original, not secondary citation
- **Context rule**: Provide enough context for readers to interpret claims correctly
- **Transparency rule**: Cite sources so readers can verify themselves

### Ethical Considerations

- **Intellectual honesty**: Present data fairly, acknowledge limitations
- **Avoid cherry-picking**: Don't ignore contradictory evidence
- **Transparent sourcing**: Always cite where information comes from
- **Respect copyright**: Don't plagiarize, always attribute
- **Protect sources**: Handle confidential information appropriately

---

**References**
- `references/fact-check-report-template.md` - Detailed fact-checking report structure
- `references/source-evaluation-guide.md` - Guide to evaluating source credibility
- `assets/fact-checking-examples.md` - Real examples with explanations

**Related Skills**
- `tech-trends-research` - Finding reliable sources during research
- `technical-writing-standards` - Writing accurately verified claims
