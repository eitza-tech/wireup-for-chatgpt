<p align="center">
  <img src="assets/logo.png" alt="WireUp logo" width="110" />
</p>

<h1 align="center">WireUp for ChatGPT</h1>

<p align="center">
  <strong>Your own WhatsApp in ChatGPT.</strong><br />
  Catch up on chats, search old messages, open photos and voice notes, and draft replies that wait for your approval.
</p>

<p align="center">
  <a href="https://wireup.chat">Website</a> ·
  <a href="https://wireup.chat/connect/chatgpt">Setup guide</a> ·
  <a href="#example-prompts">Examples</a> ·
  <a href="#faq">FAQ</a> ·
  <a href="https://wireup.chat/privacy">Privacy</a>
</p>

---

## What is WireUp?

[WireUp](https://wireup.chat) connects your own WhatsApp account to the AI assistant you already use. You sign in with Google, link WhatsApp once by scanning a QR code (the same way you link WhatsApp Web), and add one connector link to ChatGPT. There is nothing to install or keep running on your computer.

This repository is the ChatGPT package for WireUp: setup steps, the ChatGPT plugin files and a short skill that tells ChatGPT how to use WireUp well. It contains no server code, no account data and no credentials. The connector itself is hosted at `https://wireup.chat/mcp`.

## Set it up

First, create your account at [wireup.chat](https://wireup.chat): sign in with Google and scan the QR code with WhatsApp (**Settings → Linked devices → Link a device**).

Then, in ChatGPT on the web (a paid plan):

1. Open [chatgpt.com/plugins](https://chatgpt.com/plugins).
2. Choose **+**, then **Add custom MCP server**.
3. Name it **WireUp**, paste `https://wireup.chat/mcp`, and set Authentication to **OAuth**.
4. Add a description such as *"My WhatsApp: catch up on chats, search them, open voice notes and files, draft replies"*, so ChatGPT knows when to use it.
5. Sign in with the same Google account when asked.

If you don't see **Add custom MCP server**, turn on Developer mode first: **Settings → Apps → Advanced settings**.

## Example prompts

| Goal | Ask ChatGPT |
|---|---|
| Catch up | "What did I miss on WhatsApp today?" |
| Summarize a group | "Summarize this week in my family group. Anything I need to answer?" |
| Find something | "When did Dana send me the address for Sunday?" |
| Voice notes | "What did my brother say in his last voice note?" |
| Draft a reply | "Draft a reply to Sam saying I'll be 10 minutes late." |
| Send a file | "Send this PDF to the project group." |

## What it can do

| Area | Tools |
|---|---|
| Catch up and read | `catch_up`, `list_chats`, `read_chat`, `load_older_messages`, `list_statuses` |
| Search | `search_messages`, `search_contacts`, `group_info`, `message_info` |
| Photos, voice notes and files | `get_media` (voice notes and documents come back as text) |
| Send, always as a draft first | `send_message`, `send_media` (photos, stickers, GIFs, voice notes, files), `send_poll`, `send_location`, `forward_message`, then `confirm_send` |
| Manage | `react_to_message`, `edit_message`, `delete_message`, `chat_settings`, `mark_as_read` |
| Status | `whatsapp_status` |

## Sending stays in your hands

- Every send is a draft until you confirm it, unless you turn confirmation off yourself.
- Messages go only to chats you already have, with a daily limit and an off switch.
- Reading your chats never marks them as read on your phone.

## FAQ

**Is it free?** Yes, WireUp is free for now. ChatGPT needs a paid plan for custom connectors.

**Is this an official WhatsApp product?** No. WireUp links to your account as a linked device, the same way WhatsApp Web does. It is not made by, affiliated with or endorsed by WhatsApp or Meta, and it doesn't use the WhatsApp Business API. Use it for your own conversations and within WhatsApp's terms.

**Where are my messages kept?** In a storage space that belongs to your account alone, so ChatGPT can catch you up and search even when your phone is slow to answer. You can keep only the last 30 days, six months or a year, and delete everything at any time from your dashboard. What ChatGPT reads is processed by OpenAI as part of your conversation. Details: [wireup.chat/privacy](https://wireup.chat/privacy).

**Can I use it in other AI apps too?** Yes: Claude, Gemini, Grok, Perplexity, Cursor and any app that supports remote MCP connectors. See [wireup.chat/connect](https://wireup.chat/connect) and [WireUp for Claude](https://github.com/eitza-tech/wireup-for-claude).

## Troubleshooting

| What you see | What to do |
|---|---|
| "WhatsApp is not linked" | Open [wireup.chat](https://wireup.chat) and scan the QR code again. |
| ChatGPT asks you to sign in again | Open the WireUp plugin in ChatGPT and connect again. |
| A send was refused | Check the daily limit and the sending switch on your dashboard. |

## Package layout

```text
.codex-plugin/plugin.json   ChatGPT plugin manifest (name, description, icons, links)
.mcp.json                   The hosted WireUp MCP server, with OAuth
skills/wireup/SKILL.md      How the assistant should use WireUp
assets/                     Logo and composer icon
```

## Support

Email [contact@eitza.tech](mailto:contact@eitza.tech).

## Trademarks and license

WhatsApp is a trademark of Meta Platforms, Inc. ChatGPT is a trademark of OpenAI. WireUp is an independent service by Eitza Tech and is not affiliated with, sponsored or endorsed by Meta, WhatsApp or OpenAI.

The files in this repository are released under the [MIT License](LICENSE). The WireUp service itself is not open source.
