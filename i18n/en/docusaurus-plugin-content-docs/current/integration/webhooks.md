---
title: Webhooks
sidebar_label: Webhooks
sidebar_position: 2
---

# Webhooks

TalkyHub receives inbound webhooks from connected platforms and payment services.
These endpoints are called by the platforms themselves, not by your code.

## Channels

- **VK** — the community Callback API delivers new messages to the corresponding
  webhook endpoint; TalkyHub acknowledges receipt and creates a conversation.

## Payments

- **Acquiring** — payment status notifications arrive at a service endpoint and
  are validated by signature (token); on a successful payment the plan is
  activated.
- **Fiscalization** — the receipt status arrives from the fiscal data operator
  and is matched to the payment.

:::warning Authenticity checks
Webhook service endpoints are available without authorization, but every
notification is verified: payment ones by token/signature, channel ones by the
platform's identifiers. Invalid requests are rejected.
:::

## What's next

- [API overview](./overview.md)
