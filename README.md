# Promethink Dev Display — слой отображения

Этот репозиторий хранит display/read-model слой для Promethink Dev.
Здесь лежат prompt packs, sprint read-models, fixtures и trace shapes.
Используйте его, чтобы держать UI-facing data отдельно от runtime backend.

Этот репозиторий хранит display-first память для экосистемы Promethink Dev.
Он нужен не для runtime backend и не для методологии как таковой, а для
визуализации:

- карты репозиториев продуктовой экосистемы;
- roadmap и super-sprints;
- индекс спринтов и их задач;
- read-model для UI;
- prompt packs, которыми можно быстро объяснять контекст `simple-local-agent`;
- JSON fixtures для визуальной проверки.

## Что здесь лежит

- [`REPOSITORIES.md`](./REPOSITORIES.md) — ссылки на связанные репозитории Promethink Dev
- [`ROADMAP.md`](./ROADMAP.md) — дорожная карта display-слоя
- [`SPRINT_INDEX.md`](./SPRINT_INDEX.md) — индекс спринтов этого display repo
- [`SUPER_SPRINT_LOG.md`](./SUPER_SPRINT_LOG.md) — текущий super-sprint display-слоя
- [`DISPLAY_MODEL.md`](./DISPLAY_MODEL.md) — модель данных для отрисовки
- [`prompts/`](./prompts) — короткие prompt packs для агента
- [`fixtures/`](./fixtures) — примерные payload'ы для UI и QA

## Зачем это нужно

В Promethink есть несколько разных уровней данных:

1. product governance агента;
2. sprint data целевого проекта;
3. step / event stream исполнения;
4. prompt/context pack для объяснения работы агенту;
5. визуальные read-models для UI.

Этот репозиторий хранит именно то, что удобно читать и показывать.
Если project sprint source отсутствует, UI должен показывать empty state, а не
подставлять agent-owned governance batch.

## Как использовать

- UI может читать отсюда зафиксированные примеры payload'ов или готовые read-model.
- Агент может быстро взять отсюда короткий contextual prompt, чтобы не объяснять
  всё с нуля.
- Product index может ссылаться на этот репозиторий как на display/source layer.

## Важные правила

- Не смешивать сюда runtime backend code.
- Не использовать этот репозиторий как замену `promethink-dev-api`.
- Не подменять project sprint list данными из `governance.snapshot`.
- Если источника спринтов нет, оставлять пустое состояние.

## Быстрый старт

1. Открой [`DISPLAY_MODEL.md`](./DISPLAY_MODEL.md).
2. Затем посмотри [`SPRINT_INDEX.md`](./SPRINT_INDEX.md).
3. Если нужен контекст для агента, открой [`prompts/README.md`](./prompts/README.md).
4. Для самого короткого brief открой [`prompts/10_second_context.md`](./prompts/10_second_context.md).
5. Для визуального теста используй fixtures из [`fixtures/`](./fixtures).
