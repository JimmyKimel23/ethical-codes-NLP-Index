# Реестр тематик анализа (`topic_id`)

Этот реестр задаёт поддерживаемые темы для анализа на уровне `document_id × topic_id`.

## Формат

- `topic_id` — машинный идентификатор темы.
- `topic_title_ru` — человеко-читаемое название.
- `scope_ru` — что включается в тему.
- `relevance_categories` — допустимые тематические категории релевантности.
- `principles_path` — путь до канонического реестра принципов темы.

## Темы

### competitor_relations
- `topic_title_ru`: Отношения с конкурентами
- `scope_ru`: Антимонопольные требования, контакты с конкурентами, обмен чувствительной информацией, добросовестная конкуренция, эскалация и сообщения о рисках.
- `relevance_categories`:
  - `competition_law_compliance`
  - `anti_collusion`
  - `information_exchange_controls`
  - `competitor_contacts_protocol`
  - `competitor_information_integrity`
  - `fair_competition_and_non_disparagement`
  - `escalation_and_reporting`
  - `other_competitor_related`
- `principles_path`: `docs/principles/competitor_relations.md`

## Добавление новой темы

1. Добавь новый блок с уникальным `topic_id`.
2. Определи `scope_ru` и список `relevance_categories`.
3. Создай файл `docs/principles/<topic_id>.md`.
4. Используй новый `topic_id` в анализе и синтезе.
