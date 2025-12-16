---
name: draft-article
description: Create article draft from content brief or topic, using tech-content-writer agent and storytelling skills.
---

# Draft Article Command

Focused command for creating article drafts when you already have a clear content direction.

## Usage

```bash
/draft-article [topic or brief file]
```

Or run interactively:

```bash
/draft-article
```

## What This Command Does

Invokes the **tech-content-writer** agent with **technical-writing-standards** and **enterprise-storytelling** skills to create complete article draft.

## When to Use This Command

- You have completed trend research and content brief
- You have a clear article concept and direction
- You want to skip research phase and start writing
- You need to create draft from existing outline

## Process

### Step 1: Input Gathering

You'll provide:

**Content Brief / Бриф контента**:
- Upload existing content brief file, OR
- Provide topic and key details interactively

**If Interactive, You'll Be Asked**:

1. **Article Topic / Тема статьи**:
   - What is the article about?
   - Working headline?

2. **Article Type / Тип статьи**:
   - Opinion piece / thought leadership
   - Technical tutorial / how-to guide
   - Case study / success story
   - Trend analysis / market commentary
   - Research report / whitepaper

3. **Target Audience / Целевая аудитория**:
   - C-level executives
   - Engineering leaders
   - Developers/engineers
   - Product managers
   - Business decision-makers

4. **Target Publication / Целевое издание**:
   - Forbes, HBR, MIT Tech Review (executive audience)
   - TechCrunch, The Verge, Wired (tech audience)
   - Vedomosti, RBC, Kommersant (Russian business)
   - Habr, VC.ru, CNews (Russian tech)
   - Company blog
   - Other (specify)

5. **Key Messages / Ключевые сообщения** (3-5):
   - What are the main points readers should take away?

6. **Evidence & Examples / Доказательства и примеры**:
   - Case studies to include?
   - Data/statistics available?
   - Expert quotes?
   - Code examples needed?

7. **Target Word Count / Целевой объем**:
   - 800-1,200 (short form)
   - 1,200-2,000 (standard article)
   - 2,000-3,000 (long form / deep dive)
   - 3,000+ (whitepaper / comprehensive guide)

8. **Constraints / Ограничения**:
   - Company messaging requirements?
   - Topics to avoid?
   - Competitors not to mention?
   - Technical details to include/exclude?

9. **Language / Язык**:
   - English (US)
   - English (UK)
   - Russian (Русский)

### Step 2: Outline Creation

Before full draft, writer creates **detailed outline** for approval:

**Outline Structure**:
```markdown
# [Working Headline]

## Opening Hook
[How article will begin - specific scenario, question, or data point]

## Introduction / Лид
[Key points to establish in opening 2-3 paragraphs]

## Section 1: [Heading]
- Main point
- Supporting evidence
- Example or illustration

## Section 2: [Heading]
- Main point
- Supporting evidence
- Example or illustration

[Continue for all sections...]

## Conclusion / Заключение
[How article will end - synthesis, implications, call-to-action]

## Supporting Materials Needed
- [ ] Data point X from source Y
- [ ] Case study from customer Z
- [ ] Code example demonstrating A
- [ ] Diagram showing B
```

**Your Review**:
- Approve outline, OR
- Request changes to structure, emphasis, or approach

### Step 3: Draft Creation

Writer creates complete first draft following approved outline.

**Drafting Standards Applied**:
- Clear, concise language
- Active voice predominant
- Concrete examples over abstractions
- Proper heading hierarchy
- Audience-appropriate technical depth
- Natural storytelling flow
- Evidence-backed claims

**For Technical Content**:
- Working code examples
- Proper syntax and formatting
- Version-specific accuracy
- Best practices followed

**For Russian Content / Для русского контента**:
- Appropriate formal register
- Correct technical terminology
- Cultural context awareness
- Natural idiomatic expressions

### Step 4: Self-Review

Writer conducts self-review against quality checklist:
- Compelling hook in opening
- Clear value proposition
- Logical flow and structure
- Evidence supports claims
- Examples clarify concepts
- Strong conclusion
- Target word count achieved
- Grammar and style polished

### Step 5: Delivery

**Draft Package Includes**:

1. **Complete Draft / Полный черновик**:
   - Saved to: `output/drafts/[date]-[slug]-draft-v1.md`

2. **Editorial Notes / Редакционные заметки**:
   - Facts requiring verification
   - Sources to cite
   - Suggested visuals/diagrams
   - Areas needing SME review
   - Alternative headlines
   - Questions for stakeholder feedback

3. **Metadata / Метаданные**:
   ```json
   {
     "title": "Working Headline",
     "author": "Author Name",
     "date": "2024-01-15",
     "wordCount": 1847,
     "targetAudience": "Engineering Leaders",
     "targetPublication": "TechCrunch",
     "language": "en-US",
     "articleType": "opinion-piece",
     "status": "draft-v1"
   }
   ```

## Output Structure

```
output/drafts/[article-slug]/
├── [date]-[slug]-draft-v1.md      # Main draft
├── outline.md                      # Approved outline
├── editorial-notes.md              # Writer's notes
├── metadata.json                   # Article metadata
└── brief.md                        # Original brief (if provided)
```

## Next Steps After Drafting

Draft is ready for:

1. **Fact-Checking**: `/fact-check output/drafts/[date]-[slug]-draft-v1.md`
2. **Internal Review**: Share with stakeholders and SMEs
3. **Continue Workflow**: `/article-workflow --start-from=fact-checking --draft=output/drafts/[date]-[slug]-draft-v1.md`

## Options / Параметры

### --brief

Use existing content brief:

```bash
/draft-article --brief=output/research/[date]-content-brief.md
```

### --outline-only

Create outline without full draft:

```bash
/draft-article --outline-only
```

### --word-count

Specify target word count:

```bash
/draft-article --word-count=1500
```

### --language

Specify output language:

```bash
/draft-article --language=russian
/draft-article --language=english
```

### --format

Specify article format:

```bash
/draft-article --format=tutorial
/draft-article --format=opinion
/draft-article --format=case-study
/draft-article --format=analysis
```

### --publication

Target specific publication:

```bash
/draft-article --publication=forbes
/draft-article --publication=techcrunch
/draft-article --publication=habr
```

## Example Use Cases

### Use Case 1: From Existing Brief

```bash
/draft-article --brief=output/research/2024-01-15-kubernetes-finops-brief.md
```

**Result**: Complete draft following detailed brief from trend research.

### Use Case 2: Quick Opinion Piece

```bash
/draft-article --format=opinion --word-count=1000 --publication=linkedin
```

Then provide topic interactively.

**Result**: Concise opinion piece optimized for LinkedIn audience.

### Use Case 3: Technical Tutorial

```bash
/draft-article --format=tutorial --word-count=2500 --publication=habr --language=russian
```

Then provide technical topic and key steps.

**Result**: Detailed Russian-language tutorial with code examples for Habr.

### Use Case 4: Executive Case Study

```bash
/draft-article --format=case-study --publication=forbes --word-count=1200
```

Then provide customer success story details.

**Result**: Executive-friendly case study emphasizing business outcomes.

## Best Practices

**Before Drafting**:
- Have clear content brief (even if informal)
- Gather supporting materials (data, quotes, examples)
- Confirm target audience and publication
- Get stakeholder alignment on key messages

**During Drafting**:
- Approve outline before full draft (saves time)
- Provide feedback clearly and specifically
- Share relevant case studies and data
- Be available for writer questions

**After Drafting**:
- Review draft holistically first (structure, flow, narrative)
- Then review details (facts, examples, language)
- Provide consolidated feedback (not piecemeal)
- Proceed to fact-checking phase

## Tips for Better Drafts

1. **Specific Brief = Better Draft**: More detail in brief leads to better first draft
2. **Examples Early**: Share case studies and examples during brief discussion
3. **Approve Outline**: Outline approval prevents major rewrites
4. **Trust the Writer**: Avoid over-specifying language; focus on content and structure
5. **Iterate Efficiently**: One round of consolidated feedback better than many small rounds
6. **Set Realistic Timeline**: 2-3 days for standard article, 1 week for comprehensive piece
7. **Plan for Iteration**: First draft is foundation; editing improves it
8. **Include SMEs**: Involve technical experts early for accuracy

## Common Issues and Solutions

**Problem**: Draft doesn't match expectations
**Solution**: Review content brief with writer; provide specific examples of desired approach

**Problem**: Technical accuracy concerns
**Solution**: Involve SME in review; use fact-checking phase to verify details

**Problem**: Wrong tone for publication
**Solution**: Share example articles from target publication; writer will adjust tone

**Problem**: Draft too long or too short
**Solution**: Identify sections to expand/cut; writer will revise in next draft

**Problem**: Missing key message
**Solution**: Clarify key messages in brief; writer will incorporate in revision

## Quality Indicators

**Good First Draft**:
- Follows approved outline structure
- Includes concrete examples and evidence
- Appropriate tone for audience and publication
- Clear narrative flow
- Within ±10% of target word count
- 70-80% publication-ready (needs editing, not rewriting)

**Needs Significant Revision**:
- Major structural issues
- Missing key sections or messages
- Wrong audience level
- Lack of examples or evidence
- Significantly over/under word count
- Requires rewriting, not just editing

## Metrics to Track

**Drafting Efficiency**:
- Time from brief to draft
- Number of revision rounds
- Word count accuracy
- Outline approval rate

**Draft Quality**:
- Fact-checking issue rate
- Editorial issue rate
- Stakeholder approval rate
- Publication acceptance rate (after full workflow)

## Related Commands

- `/article-workflow` - Complete workflow including research
- `/trend-research` - Research trends before drafting
- `/fact-check` - Verify facts in draft
- `/seo-optimize` - Optimize draft for SEO

---

**Ready to draft? Run `/draft-article` to start writing!**
