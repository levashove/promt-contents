---
name: trend-research
description: Conduct comprehensive technology trend research to identify content opportunities and inform strategy.
---

# Technology Trend Research Command

Dedicated command for comprehensive trend research and content opportunity identification.

## Usage

```bash
/trend-research [topic]
```

Or run interactively without arguments:

```bash
/trend-research
```

## What This Command Does

This command invokes the **tech-content-strategist** agent with the **tech-trends-research** skill to:

1. Research technology trends in specified domain
2. Analyze competitive content landscape
3. Identify content opportunities
4. Score trends using IMPACT framework
5. Generate actionable content recommendations

## Process

### Step 1: Define Research Scope

You'll be asked:

**Topic/Domain / Тема исследования**:
- What technology area? (e.g., "AI/ML", "Cloud Infrastructure", "DevOps", "Cybersecurity")
- Broad or narrow focus?
- Specific technologies to include/exclude?

**Target Audience / Целевая аудитория**:
- Who will read resulting content?
- C-level, engineering leaders, developers, product managers?
- Industry-specific audience (fintech, healthcare, etc.)?

**Geographic Scope / География**:
- Global trends?
- Russian market specific?
- Regional considerations?

**Timeframe / Временные рамки**:
- Current trends (last 3-6 months)?
- Emerging trends (next 12-24 months)?
- Historical analysis needed?

### Step 2: Research Execution

The agent will:

**Market Intelligence Gathering**:
- Search analyst reports (Gartner, Forrester, IDC)
- Review technology publications
- Monitor social discussions
- Analyze GitHub trends
- Check job posting trends
- Review Russian sources (CNews, Habr, VC.ru)

**Competitive Analysis**:
- Identify competitors creating content on topic
- Audit volume, formats, and quality
- Find content gaps and opportunities

**Audience Intelligence**:
- Research pain points and challenges
- Identify questions people are asking
- Map audience personas to trends

**Search Trend Analysis**:
- Keyword volume and trends (Google Trends, Yandex Wordstat)
- Related queries and topics
- Seasonal patterns

### Step 3: Trend Evaluation

Each identified trend scored using **IMPACT Framework**:

| Criterion | Weight | Evaluation |
|-----------|--------|------------|
| **I**nterest | 10 pts | Search volume, social discussion, media coverage |
| **M**arket Readiness | 10 pts | Technology maturity, available tools, vendor support |
| **P**roof Points | 10 pts | Case studies, customer success, benchmark data |
| **A**udience Alignment | 10 pts | Relevance to target personas and challenges |
| **C**ompetitive Advantage | 10 pts | Unique perspective or expertise to provide |
| **T**imeliness | 10 pts | Newsworthiness, events, seasonal relevance |

**Total: 60 points maximum**

**Priority Levels**:
- **50-60 points**: High priority - Execute immediately
- **40-49 points**: Medium priority - Plan for next quarter
- **Below 40**: Low priority - Monitor but deprioritize

### Step 4: Content Opportunity Identification

For each high-priority trend, generate:

**Content Angles** (3-5 per trend):
- Specific article concepts
- Recommended formats (opinion, tutorial, case study, etc.)
- Target publications
- Key messages and proof points
- Estimated effort and timeline

**Keyword Strategy**:
- Primary keywords
- Secondary keywords
- Long-tail variations
- Question-based queries

**Competitive Positioning**:
- What competitors have covered
- Content gaps we can fill
- Unique perspectives we can offer

## Output

### Comprehensive Trend Research Report

Saved to: `output/research/[date]-[topic-slug]-trend-research.md`

**Report Includes**:

1. **Executive Summary / Резюме**
   - Top 3-5 trends identified
   - Key recommendations
   - Priority actions

2. **Detailed Trend Analysis** (per trend)
   - Description and significance
   - IMPACT score breakdown with rationale
   - Data and statistics
   - Media coverage and social signals
   - Competitive landscape
   - Target audience mapping
   - Recommended content angles
   - Sources and references

3. **Content Opportunity Matrix**
   - Prioritized list of content ideas
   - Format, audience, effort estimates
   - Strategic rationale

4. **Keyword Research Summary**
   - Primary and secondary keywords per trend
   - Search volumes and difficulty
   - Question-based queries

5. **Next Steps & Timeline**
   - Immediate actions (next 2 weeks)
   - Short-term actions (1-2 months)
   - Long-term strategy (quarter)

### Supporting Materials

**Competitive Analysis**
Saved to: `output/research/[date]-competitive-analysis.md`

**Keyword Research Data**
Saved to: `output/research/[date]-keyword-research.md`

## Example Use Cases

### Use Case 1: Quarterly Content Planning

```bash
/trend-research "Cloud Native Technologies"
```

**Result**: Comprehensive analysis of Kubernetes, serverless, service mesh, eBPF, and other cloud-native trends for Q1 content planning.

### Use Case 2: Rapid Response to Industry News

```bash
/trend-research "AI Code Generation" --timeframe=current
```

**Result**: Fast analysis of recent AI coding tool developments (GitHub Copilot updates, new competitors) for timely opinion piece.

### Use Case 3: Russian Market Specific

```bash
/trend-research "Import Substitution in Enterprise Software" --geography=russia
```

**Result**: Analysis of Russian market trends in domestic software alternatives with local sources and examples.

### Use Case 4: Deep Technical Dive

```bash
/trend-research "eBPF and Observability" --depth=technical
```

**Result**: Technical analysis targeting developer audience for Habr or InfoQ article.

## Options / Параметры

### --timeframe

Specify temporal focus:

```bash
/trend-research "AI Infrastructure" --timeframe=current  # Last 3-6 months
/trend-research "AI Infrastructure" --timeframe=emerging  # Next 12-24 months
/trend-research "AI Infrastructure" --timeframe=historical  # Historical context
```

### --geography

Focus on specific market:

```bash
/trend-research "Cloud Adoption" --geography=global
/trend-research "Cloud Adoption" --geography=russia
/trend-research "Cloud Adoption" --geography=europe
```

### --audience

Target specific audience:

```bash
/trend-research "Kubernetes" --audience=executives
/trend-research "Kubernetes" --audience=developers
/trend-research "Kubernetes" --audience=architects
```

### --depth

Control analysis depth:

```bash
/trend-research "Microservices" --depth=quick  # 1-2 hours, high-level
/trend-research "Microservices" --depth=standard  # 1-2 days, thorough
/trend-research "Microservices" --depth=comprehensive  # 1 week, exhaustive
```

### --format

Output format preferences:

```bash
/trend-research "DevOps" --format=brief  # Executive summary only
/trend-research "DevOps" --format=full  # Complete detailed report (default)
/trend-research "DevOps" --format=presentation  # Slide-friendly format
```

## Integration with Article Workflow

Research outputs integrate seamlessly with article creation:

```bash
# Step 1: Research
/trend-research "AI Observability"

# Step 2: Review output, select content idea

# Step 3: Start article workflow from ideation
/article-workflow --start-from=ideation --brief=output/research/[date]-ai-observability-trend-research.md
```

## Best Practices

**Before Starting**:
- Define clear business objectives for research
- Identify target audiences upfront
- Understand publication priorities
- Set realistic timeline based on depth needed

**During Research**:
- Focus on primary sources when possible
- Cross-reference multiple data points
- Document all sources for fact-checking
- Note any assumptions or limitations

**After Research**:
- Share findings with stakeholders
- Get alignment on priorities
- Plan content calendar based on results
- Schedule follow-up research (quarterly recommended)

## Tips for Better Results

1. **Be Specific**: "AI/ML" is too broad; "Large Language Models for Code Generation" is better
2. **Consider Audience First**: Research questions differ for C-level vs. developers
3. **Check Timing**: Some trends are seasonal (cloud costs spike in Q4 budget planning)
4. **Look for Intersections**: "AI + Security" or "Kubernetes + FinOps" often yield unique angles
5. **Don't Ignore Negative Trends**: "Why X Failed" or "The Dark Side of Y" can be compelling
6. **Validate with Experts**: Review findings with internal SMEs before proceeding
7. **Update Regularly**: Technology moves fast; refresh research quarterly

## Metrics to Track

**Research Quality**:
- Source diversity (how many authoritative sources?)
- Data recency (average age of cited data?)
- Competitive coverage (gaps identified vs. total landscape?)

**Research Impact**:
- Articles published from research
- Acceptance rate by target publications
- Social engagement on published pieces
- Lead attribution from content

## Troubleshooting

**Problem**: Too many trends identified, can't prioritize
**Solution**: Use IMPACT scoring strictly; focus only on scores >45

**Problem**: Can't find enough data on niche topic
**Solution**: Consider if topic is too new/narrow; expand scope or focus on adjacent established topic

**Problem**: Research taking too long
**Solution**: Use --depth=quick flag; focus on specific trend rather than broad domain

**Problem**: Russian market data limited
**Solution**: Combine Russian sources with international trends, note where data is limited, conduct informal expert interviews

## Related Commands

- `/article-workflow` - Complete article creation process (includes research)
- `/draft-article` - Skip research, start with drafting using existing brief

---

**Ready to research? Run `/trend-research` to start!**
