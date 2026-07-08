# n8n-nodes-telegram-proxy-by-memoz

This is an n8n community node. It provides a **Telegram** node and **Telegram Trigger** node that behave exactly like the built-in n8n Telegram integration, with one addition: an **HTTP/HTTPS proxy** option, the same kind of `Proxy` field found on the built-in **HTTP Request** node.

Useful when your n8n instance can only reach `api.telegram.org` through an outbound proxy.

n8n is a [fair-code licensed](https://docs.n8n.io/reference/license/) workflow automation platform.

[Installation](#installation)
[Credentials](#credentials)
[Nodes](#nodes)
[Compatibility](#compatibility)
[Known differences from the built-in node](#known-differences-from-the-built-in-node)
[Resources](#resources)

## Installation

Follow the [n8n community nodes installation guide](https://docs.n8n.io/integrations/community-nodes/installation/).

Via the n8n editor UI: **Settings → Community Nodes → Install**, then enter `n8n-nodes-telegram-proxy-by-memoz`.

Via npm, in your n8n custom-extensions folder:

```bash
npm install n8n-nodes-telegram-proxy-by-memoz
```

## Credentials

These nodes reuse n8n's built-in **Telegram API** credential type — the same one the stock Telegram/Telegram Trigger nodes use. If you already have a Telegram credential set up, just pick it; no need to create a new one.

- **Access Token** — get one from [@BotFather](https://telegram.me/botfather)
- **Base URL** — defaults to `https://api.telegram.org`

## Nodes

- **Telegram (Proxy)** — same resources/operations as the built-in Telegram node (Chat, Callback, File, Message: send text/photo/video/document/sticker/media group/rich message, edit, delete, pin, forward, etc.), plus an **Options → Proxy** field (e.g. `http://myproxy:3128`) that routes every Telegram Bot API call through the given HTTP proxy.
- **Telegram Trigger (Proxy)** — same update types as the built-in Telegram Trigger node, plus a **Proxy** field under Additional Fields, used both for registering/checking the webhook and for downloading attached files.

## Compatibility

Built against `n8n-workflow` types current as of n8n 1.x. Tested with node.js 20.

## Known differences from the built-in node

The **Send and Wait for Response** operation (Message resource) is not included. It depends on internal n8n-nodes-base utilities (Form node internals, HITL email templates) that aren't part of the public API surface available to community nodes. Every other operation is unchanged.

## Resources

- [n8n community nodes documentation](https://docs.n8n.io/integrations/community-nodes/)
- [Telegram Bot API documentation](https://core.telegram.org/bots/api)
