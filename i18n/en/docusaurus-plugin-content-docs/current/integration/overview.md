---
title: API overview
sidebar_label: Overview
sidebar_position: 1
---

# API overview

TalkyHub provides an HTTP API to manage workspaces, channels, conversations,
messages and contacts.

## Base URL

```
https://api.talkyhub.ru
```

## Authentication

The API uses JWT: pass the token in the `Authorization` header.

```bash
curl https://api.talkyhub.ru/api/v1/workspaces \
  -H "Authorization: Bearer <your_token>"
```

The token is issued after sign-in (email OTP + device passcode). Most methods run
in the context of a workspace, whose id is passed in the path:
`/api/v1/workspaces/{workspaceId}/...`.

## Format

- Requests and responses use `application/json`.
- Lists use keyset pagination (newest first by creation date).
- Errors are returned as Problem Details (RFC 7807) with a `detail` field.

## What's next

- [Webhooks](./webhooks.md)
