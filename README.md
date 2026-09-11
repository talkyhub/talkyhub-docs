# TalkyHub Docs

Источник истины для документации TalkyHub (контент в Markdown).

Работает в паре с репозиторием движка [`talkyhub-docs-site`](https://github.com/talkyhub/talkyhub-docs-site):
тот при сборке клонирует этот репозиторий, подставляет `docs/` и `i18n/`,
собирает Docusaurus-сайт и деплоит его на собственный сервер (тот же хост, что и
API) по адресу https://docs.talkyhub.ru.

## Структура

```text
talkyhub-docs/
├─ docs/                     # контент (локаль ru)
│  ├─ index.md
│  ├─ start/                 # быстрый старт
│  ├─ channels/              # каналы (почта, ВК)
│  ├─ guides/                # диалоги, контакты, оплата
│  ├─ integration/           # обзор API, вебхуки
│  ├─ faq.md
│  └─ legal/                 # оферта, политика, условия, согласие
├─ i18n/en/                  # английские переводы (кроме legal)
├─ registry/links.json       # карта ссылок для внешних потребителей
└─ .github/workflows/trigger.yml   # дёргает пересборку сайта
```

## Поток работы

1. Правите Markdown в `docs/` (и перевод в `i18n/en/`, если он есть).
2. Синхронизируете `registry/links.json` при изменении структуры/маршрутов.
3. Пуш в ветку `production` → `trigger.yml` отправляет `repository_dispatch`
   (`docs-update`) в `talkyhub-docs-site`, и сайт пересобирается.

## Настройка

В этом репозитории нужен секрет:
- `REPO_TOKEN` — токен с правом запускать `repository_dispatch` в
  `talkyhub-docs-site`.

Соглашения для людей и AI-агентов — в [AGENTS.md](AGENTS.md).
