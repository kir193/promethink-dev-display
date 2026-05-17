# Display Model

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

- If sprint source is missing, show empty state.
- Do not use `governance.snapshot` to fill project sprint list.
- If source is stale, show warning and keep the source label visible.
- Status / health metrics may still come from governance snapshot if needed.

## 6. Trace disclosure model

Trace should be visible in a collapsible form inside the existing shell, not as a separate panel.

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

Prompt packs in this repo should be short and should answer:

1. what this repo is;
2. which sprint source should be used;
3. which data must not be mixed;
4. what the expected display shape is.

## 8. Recommended UI sections

- mission brief
- sprint protocol
- status panel
- live stream summary
- source label
- empty state message
- collapsible trace disclosure
