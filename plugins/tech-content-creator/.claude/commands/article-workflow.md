---
name: article-workflow
description: Complete article creation workflow from research to publication-ready content, orchestrating all content creation agents.
---

# Article Creation Workflow / Рабочий процесс создания статьи

This command orchestrates the complete article creation process using specialized agents and skills.

## Workflow Overview / Обзор процесса

```
1. Research & Ideation → 2. Drafting → 3. Fact-Checking → 4. Editing → 5. SEO Optimization
   (tech-content-strategist)  (tech-content-writer)  (tech-fact-checker)  (content-editor)  (seo-content-optimizer)
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

**Process**:
1. **Outline creation**: Writer creates detailed outline for approval
2. **First draft**: Complete draft following brief
3. **Self-review**: Writer checks against quality checklist
4. **Delivery**: Draft with editorial notes

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

### Phase 4: Fact-Checking (Проверка фактов)

**Agent**: `tech-fact-checker`
**Skills**: `fact-checking-methodology`

**Inputs / Входные данные**:
- Draft article from Phase 3

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

### Phase 5: Editing (Редактирование)

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

### Phase 6: SEO & Distribution Optimization (SEO и оптимизация)

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

### Phase 7: Publication Preparation (Подготовка к публикации)

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
    ├── reviews/
    │   ├── [date]-[slug]-fact-check-report.md
    │   ├── [date]-[slug]-editorial-report.md
    │   └── [date]-[slug]-seo-report.md
    ├── edited/
    │   └── [date]-[slug]-edited-v1.md
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

---

**Ready to start? Run `/article-workflow` and let's create exceptional content!**
