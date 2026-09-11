# AGENTS — talkyhub-docs

This repository holds documentation **content** for TalkyHub. The Docusaurus
engine lives in `talkyhub-docs-site` and pulls this content at build time.

## Purpose
- Keep edits focused on Markdown in `docs/` and the `registry/links.json` map.
- Russian (`ru`) is the default locale and lives in `docs/`. English (`en`)
  translations live in `i18n/en/docusaurus-plugin-content-docs/current/` and
  mirror `docs/` paths/filenames; legal docs are intentionally RU-only (see
  `i18n/README.md`). When you change a `docs/` page, update its `i18n/en/`
  counterpart (if one exists), or note it's now out of sync.
- Keep changes small, reviewable, and safe for production deploys.

## Working rules
- Prefer direct Markdown edits over structural churn.
- Keep routes and slugs stable unless the task explicitly requires changes.
- **Keep `registry/links.json` in sync** with any docs structure change (new,
  removed, renamed, or re-routed pages) — especially legal docs.
- Each section has a `_category_.json` controlling its sidebar label/position.
- Legal docs are adapted templates — treat substantive legal text as draft
  until reviewed by a lawyer; don't invent binding terms.

## Brand
- Tone: plain Russian, concrete.
- Product: TalkyHub — платформа для общения с клиентами (омниканальная
  поддержка): почта (IMAP/SMTP), ВКонтакте и др. каналы в едином инбоксе.
- Billing: тарифные планы; онлайн-оплата (карта/СБП/T-Pay/SberPay) и счёт для
  юрлиц (T-Bank B2B), чеки по 54-ФЗ.
- API base `https://api.talkyhub.ru`; site `https://talkyhub.ru`;
  docs `https://docs.talkyhub.ru`.

## Standard flow
1. Apply the smallest valid change for the task.
2. Verify links/paths when touching navigation pages (`index.md`, categories).
3. Update `registry/links.json` if routes changed.
4. Commit with a clear, scoped message; push to `production` to deploy.

## AI context
Shareable context lives in `ai/` (tracked). Ephemeral cache goes in `.ai/`
(git-ignored).
