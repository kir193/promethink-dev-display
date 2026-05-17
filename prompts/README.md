# Prompt Packs

Эти prompt packs нужны, чтобы быстро объяснять `simple-local-agent`:

- что это за display repo;
- откуда брать sprint data;
- как отделять project sprint source от agent governance;
- как показывать step stream и empty state.

## Файлы

- [`brief_agent_context.md`](./brief_agent_context.md) - короткий общий brief
- [`project_sprint_source.md`](./project_sprint_source.md) - как читать sprint source
- [`step_stream_summary.md`](./step_stream_summary.md) - как отдавать шаги и события
- [`visual_display_brief.md`](./visual_display_brief.md) - как готовить данные для UI

## Правило

Prompt должен быть коротким, reusable и versioned.
Если нужно менять смысл, лучше сделать новый файл, чем переписывать старый без следа.
