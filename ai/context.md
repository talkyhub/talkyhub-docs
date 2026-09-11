# TalkyHub — context

## Product
TalkyHub is a customer-communication platform (Chatwoot-style, omnichannel
helpdesk). Customer requests from email (IMAP/SMTP), VK and other channels are
collected into one inbox; a support team handles them from a shared workspace
(conversations, contacts, agents, teams, labels, canned responses, CSAT, reports).

- Site: https://talkyhub.ru
- App API: https://api.talkyhub.ru (JWT bearer; workspace-scoped routes)
- Docs: https://docs.talkyhub.ru

## Billing
Plan-based. Two rails: online self-serve (card / SBP / T-Pay / SberPay via T-Bank
acquiring) and a B2B invoice with QR (T-Bank B2B) revealed once billing details
are filled. INN lookup auto-fills company details. Fiscal receipts via ATOL Online
(54-FZ), subject = IT service.

## These repos
- `talkyhub-docs` (this repo) — Markdown content (source of truth).
  Push to `production` → `trigger.yml` fires a `repository_dispatch` (`docs-update`).
- `talkyhub-docs-site` — Docusaurus 3 engine. On dispatch/push it clones this repo,
  swaps in `docs/` and `i18n/`, builds, and deploys to the self-hosted server
  (docs.talkyhub.ru), fronted by host nginx. (No API reference for now — the
  OpenAPI docs are intentionally omitted.)

## Conventions
- `ru` is the default locale (in `docs/`); English translations live in
  `i18n/en/docusaurus-plugin-content-docs/current/` and mirror `docs/` paths.
  Legal docs are intentionally RU-only (fallback to ru), legally binding in ru.
- Cross-doc links use relative `.md` file paths (localizable, build-validated).
- Legal docs are adapted templates — treat as draft until a lawyer reviews them.
