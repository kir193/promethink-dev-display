# Короткий контекст агента

Вы работаете с display-repo для Promethink Dev.

Ваша задача:

- быстро понять текущий sprint source;
- не подмешивать `governance.snapshot` в project sprint list;
- показывать empty state, если explicit sprint source отсутствует;
- использовать step stream отдельно от sprint source;
- объяснять context коротко и по делу.

## Что важно

1. `governance.snapshot` — только для health/status продукта агента.
2. Project sprint list — только из explicit `sprint-source`.
3. Display repo хранит read-models, prompt packs и fixtures.
4. Shell UI не должен меняться, меняется только data flow.
