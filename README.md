# promt-contents

## Для создания SEO-статей

**[ПРОМТ 1 — Аналитик → Архитектор параметров → выдаёт FINAL_GENERATION_PARAMS](https://github.com/levashove/promt-contents/blob/main/prompt_seo_1_analyze_and_build_params.yaml)**

На входе заполняем: тему, план, ключевые слова, позиционирование, тональность и остальные параметры:

- нужно выбирать вручную — MODE, RISK_PROFILE, STRUCTURE_LEVEL, UNIQUENESS_LEVEL, FACT_SOURCE_BEHAVIOR, COVERAGE_DEPTH, SERP_COMPETITOR_LOGIC. 
- можно оставить по умолчанию — AI_SEARCH_OPTIMIZATION, EDITORIAL_RULES.

Самостоятельно нейросеть: анализирует, улучшает, дополняет, выбирает аудиторию, генерирует LSI. 

На выходе: получаем полный набор итоговых параметров, которые позволят генерировать безошибочные и предсказуемо качественные статьи.

**[ПРОМТ 2 — Генерация статьи по параметрам](https://github.com/levashove/promt-contents/blob/main/prompt_seo_2_generate_article.yaml)**

Этот промт принимает параметры из первого и на их основе создаёт статью.

## Для лендингов и презентаций

**[ПРОМТ](https://github.com/levashove/promt-contents/blob/main/prompt_seo_3_infostyle_transformer_2_0.yaml)**

Решаем задачу редактуры и SEO-оптимизации текстов без изменения блоков и структуры. Все заголовки, порядок блоков и параграфы остаются на месте — переписывается только содержание.

Что умеет:

- улучшает стиль, сокращает воду, убирает дубли;
- адаптирует тон (expert / neutral / corporate);
- встраивает ключевые слова;
- создаёт метатеги (если нужно);
- оптимизирует под нейропоиск (SGE/Y1/AI Overviews).


