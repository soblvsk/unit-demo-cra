# 🏗️ Infrastructure

## 📌 Application functionality

В ветку `master` изменения происходят при PR, основной процесс в ветке `develop`.

### 📖 Lint Commit Messages

- Запускается при PR и коммите
- Происходит проверка коммитов по формату `conventional commits`

### 💢 CI Tests

- Запускается при PR и Release
- Автоматически запускаются на каждый коммит в PR
- Присутствует запрет на merge при PR, если `💢 CI Tests` не прошел проверку
- Запуск проверок:
  - Lint
  - Unit Tests
  - E2E Tests

### 🚀 Release

- Запускается автоматически при появлении нового релизного тэга по маске `v<Число>`
- Запускаются CI Tests
- Получение информации:
  - Текущий тэг
  - Предыдущий тэг
  - Автор
  - Дата создания тэга
- Формируется CHANGELOG по истории коммитов от предыдущего релизного тэга
- Создание Issue с пометкой `RELEASE` и важной информацией
- Добавление комментария к Issue с ссылкой на результаты тестов (`Artifacts`)
- Запуск `build` и `deploy` в ветку `gh-pages` при успешных проверках
- Добавление комментария к Issue с ссылкой на деплой
- Issue закрывается автоматически

## 📜 Information

В этом репозитории находится пример приложения с тестами:

- [e2e тесты](e2e/example.spec.ts)
- [unit тесты](src/example.test.tsx)

Для запуска примеров необходимо установить [NodeJS](https://nodejs.org/en/download/) 16 или выше.

Как запустить:

```sh
# установить зависимости
npm ci

# запустить приложение
npm start
```

Как запустить e2e тесты:

```sh
# скачать браузеры
npx playwright install

# запустить тесты
npm run e2e
```

Как запустить модульные тесты:

```sh
npm test
```
