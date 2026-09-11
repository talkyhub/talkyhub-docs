---
title: Channels and mailboxes
sidebar_label: Overview
sidebar_position: 1
---

# Channels

A channel (inbox) is a source of customer requests. Messages from all connected
channels land in the workspace's shared conversation list.

## Email

The email channel uses standard protocols:

- **IMAP** — TalkyHub periodically fetches new messages from a folder of the
  mailbox and turns each thread into a conversation;
- **SMTP** — agent replies are sent to the customer from the mailbox address.

When connecting, provide:

| Field | Description |
| --- | --- |
| Address | The email customers write to and replies are sent from |
| IMAP host and port | Incoming mail server (e.g. `imap.example.com:993`, SSL) |
| SMTP host and port | Outgoing mail server (e.g. `smtp.example.com:465`, SSL) |
| Login and password | Mailbox credentials (or an app password) |

:::tip One mailbox — one channel
Don't connect the same mailbox to more than one channel: two channels would poll
the same IMAP folder at once and duplicate conversations. TalkyHub warns you when
you try to create a second channel on the same mailbox.
:::

### Viewing and changing credentials

Channel connection settings can be viewed and changed from the UI or via the API.
The password is never returned in API responses — set it again if you need to
change it.

### Line breaks are preserved

Incoming email bodies are stored as-is: the customer's line breaks and paragraphs
are kept, and the email subject becomes the conversation subject.

## VK

The VK channel receives community messages. To connect it you'll need a community
access token with messaging permissions and a configured Callback API or Long
Poll — TalkyHub walks you through it in the UI.

## What's next

- [Working with conversations](../guides/conversations.md)
- [Contacts and enrichment](../guides/contacts.md)
