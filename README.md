# Antevo MCP

**Markets, world risk, trademarks and your own portfolio — inside the AI you already use.**

Three remote MCP servers. Two of them need no account.

| | | |
|---|---|---|
| **Executive** | `https://api.antevo.ch/mcp/executive/mcp` | Public — no account |
| **Trademark** | `https://trademark.antevo.ch/mcp` | Public — no account |
| **Wealth** | `https://api.antevo.ch/mcp/wealth/mcp` | Sign in with Antevo Wealth |

Every tool is read-only. Every answer carries its source and its date.

## Install

See **[INSTALL.md](INSTALL.md)** for one-click links, or paste a URL into any MCP client —
Claude, ChatGPT, Cursor, VS Code, Gemini CLI, Windsurf, Zed, Goose.

**Cursor** — search the marketplace for Antevo, or install a plugin from this repo
directly. The three connectors are three separate plugins under `plugins/`, so you
can take only the one you want.

**Gemini CLI**

```
gemini extensions install https://github.com/ANTEVO-CH/antevo-mcp
```

**Anything else** — the servers speak Streamable HTTP at the URLs above. There is nothing to
download and nothing to run locally.

## What you can ask

**Executive** — public
- What happened in markets today, and what does the desk think it means?
- What is on the risk radar right now, and what would prove it wrong?
- Which catalysts land in the next two weeks?
- Show me Swiss inflation since 1990.

**Trademark** — public
- Is "Meridian" taken as a brand name?
- Which Nice classes does a business like mine file in?
- How long do I have to oppose a filing at the EUIPO, and from when?
- Who holds this mark, and how do they behave?

**Wealth** — after sign-in, scoped to your own household
- What is my brief today?
- What is my total AUM?
- Where am I concentrated?
- What real assets do I hold?

## What this repository is

Connection metadata, and nothing else: the registry manifests, the Gemini extension
descriptor and the Cursor plugin descriptor that tell a client where the Antevo servers
live. There is no application code here, no data, and no business logic — the servers
themselves are hosted by Antevo and are not open source.

It is MIT licensed because a URL and a description are not worth protecting, and because
several marketplaces require the listed repository to be open. The Antevo plugins and
Agent Skills live in [ANTEVO-CH/plugins](https://github.com/ANTEVO-CH/plugins) and remain
all rights reserved.

```
registry/*/server.json        Official MCP Registry manifests (mirrors of what is live)
gemini-extension.json         Makes this repo a Gemini CLI extension
.cursor-plugin/plugin.json    Cursor plugin descriptor
INSTALL.md                    Generated one-click install links
```

## Registry

All three servers are listed in the official MCP Registry and active:

- `ch.antevo/executive`
- `ch.antevo/trademark`
- `ch.antevo/wealth`

The files under `registry/` mirror those entries. If you change one, change it there too —
they are the published record, not a draft.

## Links

[antevo.ch/mcp](https://antevo.ch/mcp) · [Security](SECURITY.md) · contact@antevo.ch

## Layout

```
.cursor-plugin/marketplace.json     the three plugins, for the Cursor marketplace
plugins/antevo-executive/           .cursor-plugin/plugin.json + mcp.json
plugins/antevo-trademark/
plugins/antevo-wealth/
registry/*/server.json              mirrors of the live MCP registry entries
gemini-extension.json               Gemini CLI
```

This layout is Cursor's, not ours — see
[cursor/plugin-template](https://github.com/cursor/plugin-template). CI runs their
validator against this repo on every push, so a change that would be rejected at
submission fails here first.
