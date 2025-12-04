# CLAUDE.md - AI Assistant Guide

## Repository Overview

This repository (`promt-contents`) is a collection of **YAML-based AI prompt templates** designed for SEO content generation and text optimization. The prompts are written in Russian and follow a structured, parameterized approach to content creation.

**Primary Use Cases:**
- SEO-optimized article generation
- Landing page and presentation text optimization
- Text editing while preserving structure (infostyle transformation)

## Repository Structure

```
promt-contents/
├── README.md                                    # Documentation (Russian)
├── prompt_seo_1_analyze_and_build_params.yaml   # Parameter analysis prompt
├── prompt_seo_2_generate_article.yaml           # Article generation prompt
├── prompt_seo_3_infostyle_transformer_2_0.yaml  # Text transformation prompt
└── CLAUDE.md                                    # This file
```

## File Descriptions

### `prompt_seo_1_analyze_and_build_params.yaml`
**Purpose:** Analyst → Parameter Architect prompt

This is the first step in the SEO article workflow. It takes raw input (topic, plan, keywords, brand positioning) and:
- Refines the topic and plan
- Auto-detects target audience
- Generates LSI keywords
- Maps keyword intents (informational/navigational/transactional)
- Clusters keywords (core/subtopics/longtails)
- Outputs `FINAL_GENERATION_PARAMS` for use in Prompt 2

**Key Parameters to Configure:**
- `MODE`: deep_expert | balanced | light | strict_seo | brand_heavy
- `RISK_PROFILE`: safe | neutral | bold
- `STRUCTURE_LEVEL`: strict | guided | flexible
- `UNIQUENESS_LEVEL`: 1 | 2 | 3
- `FACT_SOURCE_BEHAVIOR`: no_invented_facts | allow_generalized | allow_noncritical
- `COVERAGE_DEPTH`: core_only | broad_context | related_domains
- `SERP_COMPETITOR_LOGIC`: enabled | disabled

### `prompt_seo_2_generate_article.yaml`
**Purpose:** Article generation based on parameters

Takes `FINAL_GENERATION_PARAMS` from Prompt 1 and generates:
- meta_title, meta_description, seo_url
- h1_variants (5 options)
- Full article text
- alt_texts for images
- Used keywords/LSI list
- Editor notes

### `prompt_seo_3_infostyle_transformer_2_0.yaml`
**Purpose:** Text transformation with structure preservation (Infostyle 2.0)

A separate workflow for editing existing text while **strictly preserving structure**:
- Improves style, removes filler content, eliminates duplicates
- Adapts tone (expert | neutral | corporate)
- Integrates keywords naturally
- Creates meta tags (if needed)
- Optimizes for AI search (SGE/Y1/AI Overviews)

**Critical Constraint:** `KEEP_STRUCTURE: true` - the structure (headings, order, paragraphs) must NEVER be modified.

## Workflow Patterns

### Pattern 1: Full SEO Article Generation
```
1. Fill INPUT section in prompt_seo_1_analyze_and_build_params.yaml
2. Run Prompt 1 → Get FINAL_GENERATION_PARAMS
3. Insert params into prompt_seo_2_generate_article.yaml
4. Run Prompt 2 → Get complete article
```

### Pattern 2: Existing Text Optimization
```
1. Insert source text into prompt_seo_3_infostyle_transformer_2_0.yaml
2. Configure SEO_PARAMETERS and STYLE_PARAMETERS
3. Run → Get optimized text with preserved structure
```

## Key Concepts

### YAML Prompt Format
All prompts use YAML structure with:
- `ROLE:` - AI persona(s) to embody
- `INPUT:` - User-provided data
- `TASKS:` - Processing steps
- `OUTPUT:` - Expected results format

### SEO Parameters
- **KEYWORDS_MAIN**: Primary target keywords
- **KEYWORDS_LSI**: Latent Semantic Indexing keywords (topically related)
- **DENSITY**: Keyword density control (low | moderate | neutral | flexible)
- **AI_SEARCH_OPTIMIZATION**: Flags for Google SGE, Yandex Y1, AI Overviews compatibility

### Editorial Rules
Standard rules applied across prompts:
- `no_water` - Remove filler content
- `no_cliches` - Avoid cliche phrases
- `clarity_first` - Prioritize clarity
- `lead_with_value` - Put important info first
- `avoid_repetition` - No redundant content

## Conventions for AI Assistants

### When Modifying Prompts:
1. Preserve YAML structure and indentation
2. Keep Russian language for user-facing text
3. Maintain comment style using `#`
4. Test parameter combinations for consistency
5. Document any new parameters in comments

### When Creating New Prompts:
1. Follow the established YAML structure (ROLE → INPUT → TASKS → OUTPUT)
2. Include parameter explanations as inline comments
3. Use consistent parameter naming (CAPS_WITH_UNDERSCORES)
4. Define clear value options for enumerable parameters

### Language:
- Prompts and documentation: **Russian**
- Parameter names and values: **English**
- File names: **English with underscores**

## Development Notes

- No build system or dependencies - pure YAML files
- Version control via Git
- No automated testing - manual prompt testing required
- Telegram channel for updates: https://t.me/proitru

## Common Tasks

### Adding a New Prompt
1. Create file: `prompt_[category]_[number]_[name].yaml`
2. Follow existing structure patterns
3. Update README.md with description and link
4. Document all configurable parameters

### Modifying Existing Prompts
1. Preserve backward compatibility for parameters
2. Add new options rather than replacing existing ones
3. Update inline comments for any changes
4. Test with various input combinations
