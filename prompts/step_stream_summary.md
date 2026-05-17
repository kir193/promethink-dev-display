# Step Stream Summary Brief

Используй этот prompt, когда нужно превращать поток событий в короткий readable summary для UI.

## Event types

- `session`
- `turn_start`
- `step_start`
- `action`
- `action_result`
- `step_end`
- `persisted`
- `done`
- `error`

## Output rules

- показывай только короткие summaries;
- не выводи сырой reasoning dump;
- не добавляй лишнюю техническую воду;
- если событие неполное, сообщай это честно;
- если есть ошибка, покажи её коротко и понятно.
