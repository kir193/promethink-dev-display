# Handoff: MSW mock mode для Promethink Dev UI

Этот файл - передаваемый пакет для следующего шага в `Promethink Dev UI`.
Его цель - помочь добавить в UI такой же mock mode для тестирования без backend,
как уже сделано в `promethink-automatica-electron-ui`.

## Зачем это нужно

MSW - это network-level mock layer. Он перехватывает обычные `fetch`-запросы
на уровне браузера или Electron renderer и возвращает ответы из локальных
handlers.

Это лучше, чем мокать данные прямо в React-компонентах, потому что:

- UI ходит по тем же API-адресам, что и в live mode;
- сценарии тестирования не зависят от backend;
- mock logic можно переиспользовать в браузере, Playwright и будущем Node test layer;
- при переходе на live backend не нужно переписывать экраны.

## Что уже служит эталоном

В `promethink-automatica-electron-ui` этот подход уже собран и проверен:

- `C:\Users\kiril\IdeaProjects\promethink-automatica-electron-ui\public\mockServiceWorker.js`
- `C:\Users\kiril\IdeaProjects\promethink-automatica-electron-ui\src\runtime\runtimeMode.ts`
- `C:\Users\kiril\IdeaProjects\promethink-automatica-electron-ui\src\mocks\runtime.ts`
- `C:\Users\kiril\IdeaProjects\promethink-automatica-electron-ui\src\mocks\browser.ts`
- `C:\Users\kiril\IdeaProjects\promethink-automatica-electron-ui\src\mocks\handlers.ts`
- `C:\Users\kiril\IdeaProjects\promethink-automatica-electron-ui\src\main.tsx`
- `C:\Users\kiril\IdeaProjects\promethink-automatica-electron-ui\playwright.config.ts`
- `C:\Users\kiril\IdeaProjects\promethink-automatica-electron-ui\tests\e2e\mock\mock-mode.spec.ts`

Документация-эталон:

- `C:\Users\kiril\IdeaProjects\promethink-automatica-electron-ui\README.md`
- `C:\Users\kiril\IdeaProjects\promethink-automatica-electron-ui\TROUBLESHOOTING.md`
- `C:\Users\kiril\IdeaProjects\promethink-automatica-electron-ui\docs\FRONTEND_MOCKING.md`

## Что нужно повторить в Promethink Dev UI

### 1. Добавить runtime mode contract

Нужны 3 режима:

- `auto` - по умолчанию: если задан backend URL, работаем с backend, иначе включаем mock mode;
- `mock` - принудительный mock mode;
- `api` - принудительный live mode.

### 2. Подключить MSW

Добавить:

- `msw` как devDependency;
- `public/mockServiceWorker.js` через `npx msw init public --save`;
- `src/mocks/browser.ts` с `setupWorker(...)`;
- `src/mocks/handlers.ts` с сетевыми handlers;
- `src/mocks/runtime.ts` для переключения mock transport;
- bootstrap, который ждёт `worker.start()` до первого render в mock mode.

### 3. Не мокать внутри компонентов

Не делать fake data прямо в React-дереве.
Весь mock должен жить через network layer, чтобы:

- тесты видели реальные `fetch`-вызовы;
- мок и live mode использовали один и тот же API shape;
- позже можно было без переписывания перейти на backend.

### 4. Добавить отдельный mock запуск

Нужны отдельные команды:

- `dev:mock`
- `test:mock`

Если в этом репо уже есть свой desktop launcher, mock mode должен включаться через
тот же launcher, но с принудительным `mock` runtime.

### 5. Покрыть основные endpoint'ы

Для UI mock layer обычно нужны:

- список сущностей;
- детали;
- create/save flow;
- status actions;
- groups/categories endpoint;
- executions или run endpoint;
- examples/templates endpoint, если есть экран создания.

Для Dev UI ориентируйся на свой реальный API contract, но не делай mock через
ручные дубли внутри страниц.

## Что обязательно документировать в целевом репо

В Promethink Dev UI должны появиться простые и очень явные документы:

- `README.md`
  - что такое `dev:mock`;
  - как переключать `auto/mock/api`;
  - где лежит `mockServiceWorker.js`;
  - как запускать UI без backend;
  - какой порт использует renderer;
- `TROUBLESHOOTING.md`
  - как понять, что запущен mock mode;
  - как исправлять проблемы service worker;
  - как отличать renderer-port от Electron;
  - что делать, если запущен старый процесс;
- `docs/FRONTEND_MOCKING.md`
  - что такое MSW;
  - какие endpoint'ы мокируются;
  - когда использовать mock mode;
  - когда переключаться на api mode;
- `tests/README.md`
  - где лежат mock tests;
  - как запускать Playwright smoke без backend.

## Минимальный checklist готовности

Считать работу сделанной только если проходят:

- `npm run typecheck`
- `npm run lint`
- `npm run build`
- `npm run dev:mock`
- `npm run test:mock`

И в mock mode реально можно:

- открыть основной экран;
- пройти create flow;
- увидеть, что запросы идут через MSW;
- не запускать backend вообще.

## Что не делать

- Не смешивать mock и api в одном потоке без явного режима.
- Не держать fake data только внутри React-компонентов.
- Не подменять backend contract ради того, чтобы тест прошёл.
- Не считать mock suite доказательством live integration.

## Рекомендуемая формулировка для следующего агента

> Возьми MSW handoff из `prompts/promethink_dev_ui_msw_handoff.md` и добавь такой же mock mode в `Promethink Dev UI`. Сначала сделай runtime contract и MSW wiring, затем docs, затем mock Playwright smoke. Не смешивай mock и api, и не пиши fake data внутри компонентов.

## Стоп-условие

После того как mock mode готов и задокументирован, можно остановиться.
Backend integration делается отдельным этапом, когда backend-команда подтвердит контракт.
