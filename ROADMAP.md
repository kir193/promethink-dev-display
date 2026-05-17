# Roadmap

## Purpose

Показать, как display-слой Promethink Dev будет развиваться независимо от runtime backend.

## Phases

### Phase 1 - Display source model

- собрать единый read-model для спринтов, задач, источника и empty state;
- описать, какие поля нужны для UI;
- отделить product governance от project sprint source.

**Methodology:** `Complex_M` + `AI_Task_Governor`  
**Budget:** `S/M`  
**Stop condition:** UI может отрисовать sprint source без fallback на `governance.snapshot`.

### Phase 2 - Sprint index and super sprint log

- вести индекс спринтов display-репо;
- хранить текущий super sprint log;
- фиксировать статусы, boundary review и next batch preview.

**Budget:** `S`  
**Stop condition:** спринты и super sprint можно читать как статический source of truth.

### Phase 3 - Prompt packs for agent context

- хранить короткие prompt'ы для `simple-local-agent`;
- быстро объяснять текущий контекст, display rules и source selection rules;
- держать prompt packs отдельно от runtime backend.

**Budget:** `S`  
**Stop condition:** агент может быстро получить короткий и понятный context brief.

### Phase 4 - Fixture data and QA payloads

- хранить sample JSON payloads для UI;
- тестировать empty state, source connected state и step stream summaries;
- поддерживать display QA без изменения backend.

**Budget:** `S/M`  
**Stop condition:** есть fixtures для визуальной проверки и ручной отладки.

### Phase 5 - Frontend hydration helpers

- использовать этот repo как optional source for display snapshots;
- подключать его к frontend только через contract/read-model слой;
- не смешивать с backend runtime logic.

**Budget:** `M`  
**Stop condition:** frontend умеет показывать sprint source и step stream из read-model.

### Phase 6 - Trace disclosure and collapsible execution summaries

- store a short trace disclosure model for the shell UI;
- keep step-by-step execution summaries collapsible inside the existing layout;
- add prompts and fixtures that describe trace output without raw reasoning dumps.

**Budget:** `S/M`  
**Stop condition:** frontend can render a readable collapsible trace inside the current shell.

## Working rules

1. Не использовать `governance.snapshot` как источник project sprint list.
2. Если sprint source не подключён, показывать empty state.
3. Prompt packs должны быть короткими, reusable и versioned.
4. Fixtures должны быть читаемыми и иметь стабильную структуру.
5. Trace disclosure should stay collapsible and separate from sprint metadata.
