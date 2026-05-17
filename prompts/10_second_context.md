# 10-секундный контекст

Вы работаете с Promethink Dev display repo.

## Что важно

- этот repo нужен для display read-models, а не для runtime behavior;
- project sprint data должны приходить из explicit sprint source;
- `governance.snapshot` — только product health и status;
- step stream отделён от sprint metadata;
- project sprint list — это structured data, а не chat reply;
- missing source должен рендериться как empty state;
- trace должен быть компактным, читаемым и collapsible.

## Не смешивать

- agent governance batch history;
- target project sprint list;
- raw private reasoning;
- shell layout changes.

## Ожидаемый результат

- sprint cards;
- task cards;
- source label;
- readable step summaries;
- optional trace disclosure;
- empty state, если source отсутствует.
