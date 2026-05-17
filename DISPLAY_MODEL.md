# Модель отображения

Этот файл описывает формы данных, которые удобно показывать в UI.

## 1. Project sprint source

```ts
type ProjectSprintSource = {
  sourceType: 'repo' | 'store';
  sourceRef: string;
  sourceLabel: string;
  sourceState: 'connected' | 'empty' | 'missing' | 'stale';
  lastSyncedAt?: string;
  warnings: string[];
};
```

## 2. Sprint card

```ts
type SprintCard = {
  id: string;
  number: string;
  title: string;
  description: string;
  timestampLabel: string;
  status: 'done' | 'active' | 'pending';
  tasks: SprintTaskCard[];
};
```

## 3. Sprint task card

```ts
type SprintTaskCard = {
  id: string;
  number: string;
  size: 'S' | 'M' | 'L';
  title: string;
  status: 'done' | 'active' | 'pending';
};
```

## 4. Step stream event

```ts
type StepStreamEvent =
  | { type: 'session'; sessionId: string }
  | { type: 'turn_start'; turnId: string; sessionId: string }
  | { type: 'step_start'; stepId: string; title?: string }
  | { type: 'action'; stepId: string; name: string; summary?: string }
  | { type: 'action_result'; stepId: string; name: string; ok: boolean; summary?: string }
  | { type: 'step_end'; stepId: string; status: 'done' | 'blocked' | 'active' }
  | { type: 'persisted'; sessionId: string; executionId?: string }
  | { type: 'done'; sessionId: string; summary?: string }
  | { type: 'error'; message: string; code?: string };
```

## 5. Empty state rules

- Если sprint source отсутствует, показывать empty state.
- Не использовать `governance.snapshot` для заполнения project sprint list.
- Если source stale, показывать warning и оставлять source label видимым.
- Status / health metrics по-прежнему могут приходить из governance snapshot, если это нужно.

## 6. Trace disclosure model

Trace должен быть видим в collapsible виде внутри существующего shell, а не как
отдельная панель.

```ts
type ExecutionTraceDisclosure = {
  open: boolean;
  summary?: string;
  sessionId?: string;
  executionId?: string;
  notes: string[];
  steps: Array<{
    id: string;
    number: string;
    title: string;
    status: 'active' | 'done' | 'blocked';
    notes?: string[];
  }>;
  warnings: string[];
  error?: string;
};
```

## 7. Prompt pack output

Prompt packs в этом repo должны быть короткими и отвечать на 4 вопроса:

1. что это за repo;
2. какой sprint source использовать;
3. что нельзя смешивать;
4. какой ожидается display shape.

## 8. Рекомендуемые UI sections

- mission brief;
- sprint protocol;
- status panel;
- live stream summary;
- source label;
- empty state message;
- collapsible trace disclosure.
