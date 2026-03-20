# Instruction 02 — Analysis of One Code

## Task
Проанализировать один корпоративный кодекс этики на предмет темы «Отношения с конкурентами».

## Goal
1. Определить, присутствует ли тема отношений с конкурентами.
2. Присвоить статус наличия темы.
3. Извлечь подтверждающие цитаты.
4. Отнести найденные положения к каноническим `principle_code`.
5. Сохранить карточку в `analysis/yaml/<document_id>.yaml`.
6. Обновить `registry/codes_status.csv`.

## Language rule
- Анализ ведётся по языку оригинала документа.
- Цитаты сохраняются в оригинале.
- Для каждой цитаты обязателен перевод на русский.
- Нормализация, статусы и выводы записываются на русском.

## Allowed values

### `competitor_relations_status`
- `explicit_section`
- `implicit_scattered`
- `brief_mention`
- `absent`
- `unclear`

### `evidence_quality`
- `high`
- `medium`
- `low`

### `review_status`
- `completed`
- `needs_human_review`

### `relevance_categories`
- `competition_law_compliance`
- `anti_collusion`
- `information_exchange_controls`
- `competitor_contacts_protocol`
- `competitor_information_integrity`
- `fair_competition_and_non_disparagement`
- `escalation_and_reporting`
- `other_competitor_related`

### `principle_code`
- `P01_follow_competition_laws`
- `P02_no_price_fixing`
- `P03_no_market_allocation`
- `P04_no_bid_rigging`
- `P05_no_sensitive_info_exchange`
- `P06_control_competitor_contacts`
- `P07_no_improper_competitor_intelligence`
- `P08_respect_confidential_info_of_competitors`
- `P09_compete_fairly_no_disparagement`
- `P10_escalate_to_legal_or_compliance`
- `P11_report_violations_or_concerns`
- `P12_keep_records_or_follow_internal_controls`
- `P99_other`

## Required procedure
1. Сначала ищи явный раздел по теме конкурентов.
2. Если его нет, ищи функциональные эквиваленты:
   - fair competition
   - antitrust
   - competition law
   - market conduct
   - dealings with competitors
   - competitor information
   - industry associations
3. Если положения разбросаны по нескольким разделам, используй `implicit_scattered`.
4. Не ставь `explicit_section`, если найдено только общее упоминание закона или честной конкуренции.
5. Не выдумывай положения, которых нет в тексте.
6. Строго отделяй цитату от нормализации.
7. Если используется `P99_other`, обязательно опиши новый принцип отдельно.
8. Если текст неполный, перевод сомнителен или доказательства слабые, понижай `evidence_quality` и используй `needs_human_review`.
9. итата в `key_excerpts.original` - не более 2-3 предложений. Если релевантный фрагмент длиннее, разбивай на отдельные записи в `key_excerpts`.
10. Каждая запись в `key_excerpts` должна содержать `supports_principles` со списком `principle_code`, которые эта цитата подтверждает. Итоговый `principle_codes_detected` формируется как объединение всех `supports_principles`.

## Required YAML structure
```yaml
document_id: ""
company_name: ""
country: ""
industry: ""
source_path: ""
source_language: ""
document_type: ""
competitor_relations_status: ""
evidence_quality: ""
review_status: ""
relevant_section_titles: []
relevance_categories: []
key_excerpts:
  - original: ""
    translated_ru: ""
    section_title: ""
    relevance_comment: ""
    supports_principles: []
principle_codes_detected: []
other_principles:
  - other_principle_label: ""
    other_principle_explanation: ""
notes: []
limitations: []
analyst_summary_ru: ""
```

## Required response
Кратко сообщи:
- какой документ обработан;
- какой статус присвоен;
- какие `principle_codes_detected` найдены;
- нужен ли `human review`.
