# Brief по источнику спринтов проекта

Используйте этот brief, когда нужно показать спринты проекта, а не спринты
самого агента.

## Правила source

1. Если у проекта есть sprint metadata в repo — используйте `source_type=repo`.
2. Если sprint metadata нет — используйте `source_type=store`.
3. Если источника нет — верните empty state и warning.
4. Никогда не подставляйте `governance.snapshot` как sprint list source.

## Что возвращать

- `sourceType`
- `sourceRef`
- `sourceMetadata`
- `lastSyncedAt`
- `activeSprint`
- `sprints`
- `warnings`

## Что не делать

- не использовать agent batch/sprint history как project sprint list;
- не менять визуальную композицию экрана;
- не скрывать отсутствие source за чужими спринтами.
