# Индекс спринтов

## Уровень super-sprint

- super-sprint: `D.01` — display source foundation;
- цель: собрать display memory для спринтов, roadmap и prompt packs;
- review границы: после `D-S05`.

## Спринты в текущем батче

- `D-S01` — определить display read-model и правила выбора source;
- `D-S02` — добавить sprint index и super sprint log;
- `D-S03` — добавить prompt packs для контекста `simple-local-agent`;
- `D-S04` — добавить fixtures и ручные QA payloads;
- `D-S05` — добавить trace disclosure model и collapsible execution summaries.

## Текущий статус

- `D-S01` — planned;
- `D-S02` — planned;
- `D-S03` — planned;
- `D-S04` — planned;
- `D-S05` — planned.

## Правила display

1. Project sprint data должны приходить только из explicit sprint source или fixture source.
2. Agent governance data — не источник sprint list для project work.
3. Step stream отделён от sprint source.
4. Empty state валиден и не должен заменяться чужими batch data.

## Карта файлов

- `ROADMAP.md`
- `SUPER_SPRINT_LOG.md`
- `DISPLAY_MODEL.md`
- `prompts/`
- `fixtures/`
