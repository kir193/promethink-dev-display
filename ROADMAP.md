# Дорожная карта

## Назначение

Показать, как display-слой Promethink Dev будет развиваться независимо от
runtime backend.

## Фазы

### Фаза 1 - Display source model

- собрать единый read-model для спринтов, задач, source и empty state;
- описать, какие поля нужны для UI;
- отделить product governance от project sprint source.

**Methodology:** `Complex_M` + `AI_Task_Governor`  
**Budget:** `S/M`  
**Stop condition:** UI может отрисовать sprint source без fallback на `governance.snapshot`.

### Фаза 2 - Sprint index и super sprint log

- вести индекс спринтов display repo;
- хранить текущий super sprint log;
- фиксировать статусы, boundary review и preview следующего batch.

**Budget:** `S`  
**Stop condition:** спринты и super sprint можно читать как статический source of truth.

### Фаза 3 - Prompt packs для agent context

- хранить короткие prompt'ы для `simple-local-agent`;
- быстро объяснять текущий context, display rules и source selection rules;
- держать prompt packs отдельно от runtime backend.

**Budget:** `S`  
**Stop condition:** агент может быстро получить короткий и понятный context brief.

### Фаза 4 - Fixture data и QA payloads

- хранить sample JSON payload'ы для UI;
- тестировать empty state, connected state и step stream summaries;
- поддерживать display QA без изменения backend.

**Budget:** `S/M`  
**Stop condition:** есть fixtures для визуальной проверки и ручной отладки.

### Фаза 5 - Frontend hydration helpers

- использовать этот repo как optional source для display snapshots;
- подключать его к frontend только через contract/read-model слой;
- не смешивать его с backend runtime logic.

**Budget:** `M`  
**Stop condition:** frontend умеет показывать sprint source и step stream из read-model.

### Фаза 6 - Trace disclosure и collapsible execution summaries

- хранить short trace disclosure model для shell UI;
- держать step-by-step execution summaries collapsible внутри существующего layout;
- добавлять prompt'ы и fixtures, которые описывают trace output без raw reasoning dump.

**Budget:** `S/M`  
**Stop condition:** frontend умеет показывать readable collapsible trace внутри текущего shell.

## Правила работы

1. Не использовать `governance.snapshot` как источник project sprint list.
2. Если sprint source не подключён, показывать empty state.
3. Prompt packs должны быть короткими, reusable и versioned.
4. Fixtures должны быть читаемыми и иметь стабильную структуру.
5. Trace disclosure должен оставаться collapsible и отдельным от sprint metadata.
