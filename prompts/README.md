# Пакеты промптов

Эта папка хранит короткие reusable prompts для display/read-model слоя
Promethink Dev.

Используйте их, чтобы быстро объяснить:

- что это за repo;
- откуда приходят project sprint data;
- что нельзя смешивать с `governance.snapshot`;
- как показывать step stream и empty states;
- как держать trace output компактным и читаемым.

## Файлы

- [`brief_agent_context.md`](./brief_agent_context.md) — короткий общий brief
- [`project_sprint_source.md`](./project_sprint_source.md) — как читать sprint source
- [`step_stream_summary.md`](./step_stream_summary.md) — как суммировать step events
- [`visual_display_brief.md`](./visual_display_brief.md) — как готовить UI-shaped data
- [`10_second_context.md`](./10_second_context.md) — ultra-short agent context pack

## Правило

Промпты должны быть короткими, reusable и versioned.
Если смысл меняется, создавайте новый файл вместо того, чтобы переписывать историю.
