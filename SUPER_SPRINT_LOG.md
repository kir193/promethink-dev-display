# Лог супер-спринта

Status: active  
Type: display planning container

## Макроцикл

- Macrocycle: `D`;
- Theme: display memory и visual source packaging.

## Current super-sprint

- Super-sprint: `D.01`;
- Cadence: 5 display sprints;
- Goal: подготовить sprint source read-model, prompt packs и fixtures для UI display;
- Boundary review: after `D-S05`.

## Спринты внутри batch

- `D-S01` — display read-model и source selection rules;
- `D-S02` — sprint index и super sprint log;
- `D-S03` — prompt packs for `simple-local-agent` context;
- `D-S04` — fixtures и QA payloads;
- `D-S05` — trace disclosure и collapsible step summaries.

## Правило исполнения

Внутри batch:

- каждый sprint должен оставаться atomic;
- каждый sprint должен заканчиваться check/test или proof step;
- если sprint выходит за рамки плана, остаток переносится в следующий sprint;
- display packaging не смешивается с backend runtime changes.

## Бизнес-цель D.01

- сделать sprint и roadmap информацию легко рендеримой;
- дать UI стабильный read-model;
- держать prompt/context guidance рядом с display source;
- дать агенту короткий reusable способ объяснять текущий context;
- дать UI короткий collapsible способ показывать execution trace.
