---
title: How to add a channel
sidebar_label: Adding a channel
sidebar_position: 2
---

# How to add a channel

Connecting a channel takes a couple of minutes in the interface: you pick a
channel type, fill in a short form, and requests from it start landing in your
shared conversation list. This page explains how the add-channel wizard works,
what each type needs, and how to configure a channel after it's connected.

:::note Who can connect channels
Only workspace **administrators** can add and configure channels. Agents can see
the channel list, but the connect form is disabled for them.
:::

## Open the wizard

1. Go to **Settings → Channels**.
2. Click **Add inbox**.

The wizard has three steps: **Choose a channel → Set it up → Done**. You fill in
the fields on the left; a short, channel-specific guide sits on the right.

## Step 1. Choose a channel

Each channel tile shows a status:

- **Available** — connect it right here in the wizard.
- **Via provider** — onboarded through an external partner (WhatsApp).

## Step 2. Fill in the settings

What each channel needs:

| Channel | What you need | Where to get it |
| --- | --- | --- |
| **Telegram** | Bot token | Create a bot with [@BotFather](https://t.me/BotFather) via `/newbot` and copy the token |
| **MAX** | Bot token | [MAX for Business](https://business.max.ru/self/chat-bots) account: Chatbots → your bot → settings |
| **VK** | Community ID, access token, confirmation string | Manage community → Settings → API usage (Callback API) |
| **Email** | IMAP and SMTP details | From your mail provider (see [Channels and mailboxes](./index.md)) |
| **Website (live chat)** | Nothing upfront | The token and embed snippet are generated for you after creation |
| **WhatsApp** | An account with a provider (360dialog / Twilio) | Through the provider's embedded signup |
| **API** | — (optionally a webhook URL) | A custom channel for any network TalkyHub doesn't support natively |

:::tip The inbox name is optional
The **Inbox name** field is optional — leave it empty and TalkyHub fills in a
sensible name (e.g. the bot's @username). The name is only shown to your team and
can be changed anytime.
:::

### Channel specifics

- **VK** needs a handshake: TalkyHub returns a URL and a secret that you paste
  into the community's Callback API screen and confirm. The wizard shows these on
  the "Done" step.
- **Website (live chat)** shows an **embed snippet** after creation — a one-line
  `<script>`. Add it to every page of your site, just before `</body>`.
- **WhatsApp** connects only via the official Cloud API through a provider — there
  are no unofficial / QR-session routes.

## Step 3. Done

The channel is created and already receiving messages (for VK — after you confirm
in the community's interface; for a website — after you add the snippet). From
here you can jump to conversations or add another channel.

## Configure a channel after connecting

Open the channel from **Settings → Channels** to set:

- **General** — name, auto-assignment of new conversations, privacy (visible to
  members only), greeting and resolution messages, and channel members.
- **Credentials** (email) — the IMAP/SMTP settings; leave a password blank to keep
  the stored one.
- **Widget** (website) — the embed snippet and token rotation, accent color,
  launcher position and style, header name, reply-time label, pre-chat fields, and
  the list of allowed domains.

## Best practices

- **Clear names.** Name channels by purpose — "Support", "Sales", "Website" — so
  agents recognize the source at a glance.
- **One mailbox, one channel.** Otherwise two channels read the same folder and
  duplicate conversations.
- **Test it right away.** Message the bot / mailbox / widget and confirm the
  conversation appears and your reply arrives.
- **Private channels for sensitive queues.** Turn on privacy so only channel
  members see the conversations.
- **Spread the load.** Enable auto-assignment and add members (or a team) so new
  conversations are distributed among agents.
- **Greeting and resolution messages** set the tone and save time — configure them
  under "General".
- **For the website widget, restrict domains.** List the allowed domains so the
  snippet only runs on your site. The token is a public identifier; if it leaks,
  **rotate the token** and replace the snippet on your site.

## What's next

- [Channels and mailboxes](./index.md)
- [Working with conversations](../guides/conversations.md)
- [Contacts and data enrichment](../guides/contacts.md)
