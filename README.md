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
│  ├─ changelog/             # «Что нового» — СГЕНЕРИРОВАНО CI, руками не править (см. ниже)
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

## «Что нового» (changelog)

Раздел `docs/changelog/` (+ зеркало в `i18n/en/…/changelog/`) **публикует CI** продуктовых репозиториев —
сюда страницы не пишут руками, следующий релиз их перезапишет:

| Страница | Маршрут | Источник | Ключ реестра |
|---|---|---|---|
| `app.md` — веб-приложение | `/docs/changelog/app` | `talkyhub-web-app`: `docs/changelog/{ru,en}.md` → job `publish-changelog` | `changelog.app` |
| `api.md` — API (позже) | `/docs/changelog/api` | `threadhub-api`: тот же механизм | `changelog.api` |

CI коммитит в ветку `production` → `trigger.yml` → сайт пересобирается. Приложение показывает страницу в панели
«Помощь» по ключу реестра; ссылка «Изменения API» появится в приложении сама, как только в
`registry/links.json` добавят `changelog.api`.

Чтобы подключить changelog API: в `threadhub-api` завести `docs/changelog/{ru,en}.md` (формат — как у
приложения, см. `talkyhub-web-app/docs/changelog/README.md`), job, который копирует их в
`docs/changelog/api.md` и `i18n/en/…/changelog/api.md` (секрет с правом записи в этот репозиторий), и добавить
`"api": "/docs/changelog/api"` в `sections.changelog` реестра. `sidebar_position`: приложение — 1, API — 2.

## Настройка

В этом репозитории нужен секрет:
- `REPO_TOKEN` — токен с правом запускать `repository_dispatch` в
  `talkyhub-docs-site`.

Соглашения для людей и AI-агентов — в [AGENTS.md](AGENTS.md).
