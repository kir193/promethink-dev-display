# Project Sprint Source Brief

Используй этот brief, когда нужно показать спринты проекта, а не спринты самого агента.

## Правила источника

1. Если у проекта есть sprint metadata в репо - используй `source_type=repo`.
2. Если sprint metadata нет - используй `source_type=store`.
3. Если источника нет - верни empty state и warning.
4. Никогда не подставляй `governance.snapshot` как sprint list source.

## Что возвращать

- `sourceType`
- `sourceRef`
- `sourceMetadata`
- `lastSyncedAt`
- `activeSprint`
- `sprints`
- `warnings`

## Что не делать

- не использовать агентские batch/sprint history как project sprint list;
- не менять визуальную композицию экрана;
- не прятать отсутствие источника за чужими спринтами.
