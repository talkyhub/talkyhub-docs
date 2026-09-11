---
title: Contacts and enrichment
sidebar_label: Contacts
sidebar_position: 2
---

# Contacts

A contact is a customer's card. On the first request from any channel TalkyHub
creates the contact automatically and links all of that customer's conversations
to it.

## The contact card

The card stores the name, email, phone, contact type, labels and custom
attributes. Right from the card you can see the customer's **previous
conversations** — the whole history in one place.

## Email enrichment

When a contact's email is known, TalkyHub adds useful hints without calling any
external service:

- **avatar_url** — a Gravatar avatar URL (falls back to initials when there's no
  avatar);
- **company_domain** — the company domain (business addresses only; free email
  providers are ignored).

These land in the contact's additional attributes and are shown in the UI.

## Attributes

- **Additional attributes** — service data filled automatically (e.g. the
  enrichment above).
- **Custom attributes** — fields you define yourself: text, number, link, date,
  checkbox or list. Definitions are created at the workspace level and apply to
  contacts or conversations.

## Labels

Labels are a tagging mechanism shared with conversations. A contact's label set
can be replaced in one request; every id must belong to the workspace.

## What's next

- [Working with conversations](./conversations.md)
- [API integration](../integration/overview.md)
