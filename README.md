![Antevo: a question field cycling through questions your assistant can now answer, beside a lens where signals from the world travel inward to you](assets/cover.svg)

# Antevo MCP: five remote MCP servers for markets, trademarks, wealth and mandates

**Antevo's connections, for any assistant that speaks MCP.** The 07:00 Brief, the Executive Brief and its dated archive, the trademark registers, your own household and your firm's client book — five remote servers over Streamable HTTP. Three need no account. There is nothing to download and nothing to run.

[![validate](https://github.com/ANTEVO-CH/antevo-mcp/actions/workflows/validate.yml/badge.svg)](https://github.com/ANTEVO-CH/antevo-mcp/actions/workflows/validate.yml)
[![MCP Registry](https://img.shields.io/badge/MCP%20Registry-ch.antevo-252c28?labelColor=9b7936)](https://registry.modelcontextprotocol.io/v0/servers?search=ch.antevo)
[![Transport](https://img.shields.io/badge/transport-Streamable%20HTTP-252c28?labelColor=9b7936)](#the-servers)
[![npm](https://img.shields.io/npm/v/@antevo/cli?label=%40antevo%2Fcli&color=252c28&labelColor=9b7936)](https://www.npmjs.com/package/@antevo/cli)
[![License: MIT](https://img.shields.io/badge/license-MIT-252c28?labelColor=9b7936)](LICENSE)

### Why Antevo

- **A named desk, not a web search.** Answers come from Antevo's published Executive Brief, the trademark registers themselves, and — when you sign in — your own record, with the date on every read.
- **Public where it can be, permissioned where it matters.** Executive and trademark screening reach no personal data. Wealth and Mandates sign in over OAuth 2.1 with PKCE.
- **Intelligence, not advice.** Nothing here places a trade or moves money.

![How a question travels: your assistant speaks MCP to four Antevo connections, which draw on the Antevo desk and return an answer with the record behind it](assets/connections.svg)

## Table of Contents

- [The servers](#the-servers)
- [The 07:00 Brief: make it automatic](#the-0700-brief-make-it-automatic)
- [Install in your client](#install-in-your-client)
- [Quick Start](#quick-start)
- [Authentication](#authentication)
- [What this repository is](#what-this-repository-is)
- [Registry](#registry)
- [FAQ](#faq)
- [Privacy and support](#privacy-and-support)
- [Security](#security)
- [License](#license)

## The servers

| | Server | Address | Access | Tools |
|:--|:--|:--|:--|--:|
| **0.** | **The 07:00 Brief** — your agent knows the markets by 07:00, every day: the daily brief, Market Map, Big Picture, Three Minute Brief, Risk Radar and sector notes | `https://api.antevo.ch/mcp/0700/mcp` | Public | 4 |
| **I.** | **Executive** — the daily editorial read, risk radar, forward calendar, dated archive, desk reads, world-events map, macro-economic history | `https://api.antevo.ch/mcp/executive/mcp` | Public | 15 |
| **II.** | **Trademark** — screen a name, read a holder's filing pattern, check an opposition window | `https://trademark.antevo.ch/mcp` | Public screening | 4 |
| **III.** | **Wealth** — your household: holdings, allocation, risk, real assets, liabilities, goals, documents | `https://api.antevo.ch/mcp/wealth/mcp` | Your account | 36 |
| **IV.** | **Mandates** — your firm's client book: clients, reviews, meeting briefs, goals, documents, succession | `https://api.antevo.ch/mcp/mandates/mcp` | By arrangement | 24 |

Tool counts are read live from each server's `tools/list`. Every Wealth tool is read-only; Mandates can also change records in your own firm's book and asks for confirmation before anything irreversible.

## The 07:00 Brief: make it automatic

**Your agent knows the markets by 07:00, every day. We read them so you don't have to.**

In Claude, add a Scheduled task; in ChatGPT, a Task. Set it for 07:05 every morning and paste a prompt. Your agent has read the markets before you have.

| When | Prompt |
|:--|:--|
| Every day, 07:05 | "Read today's 07:00 Brief and tell me the three things that matter today, and what to watch." |
| Every day, 07:05, with Antevo Wealth | "Read today's 07:00 Brief and tell me the three things that matter today, and what they mean for my holdings." |
| Every Monday, 07:05 | "From The 07:00 Brief's Risk Radar, tell me which risks are rising this week and what to watch." |

The brief is out around 07:00 Zurich time; in Asia, pick a time after 14:00 Singapore time. **Prefer email?** Get the brief in your inbox each morning: [antevo.ch/executive](https://antevo.ch/executive)

## Install in your client

| Client | How |
|:--|:--|
| **Claude** — Code, Desktop, claude.ai | `/plugin marketplace add ANTEVO-CH/plugins`, then `/plugin install antevo-executive@antevo` — each connection with its skills. See [ANTEVO-CH/plugins](https://github.com/ANTEVO-CH/plugins). |
| **Claude** — directory | One click: [The 07:00 Brief](https://claude.ai/directory/the-0700-brief), [Executive](https://claude.ai/directory/antevo-executive-brief), [Wealth](https://claude.ai/directory/antevo-wealth). |
| **Cursor** | One click on [antevo.ch/mcp](https://antevo.ch/mcp/#connections), the `mcp.json` in [INSTALL.md](INSTALL.md#cursor), or a plugin from [`plugins/`](plugins) — five plugins, take only what you need. |
| **VS Code** | One click from [INSTALL.md](INSTALL.md). |
| **Gemini CLI** | `gemini extensions install https://github.com/ANTEVO-CH/antevo-mcp` |
| **Kiro** | Powers → Add Custom Power → import from GitHub: [`powers/`](powers) has The 07:00 Brief, Executive and Trademark. |
| **Windsurf, Zed, Goose, any MCP client** | Paste an address from [the servers](#the-servers) as a remote Streamable HTTP server. |
| **A terminal** | `npx @antevo/cli brief` — see [ANTEVO-CH/cli](https://github.com/ANTEVO-CH/cli). |

## Quick Start

```text
What do I need to know about markets today?                              → The 07:00 Brief
What happened in markets today, and what does the desk make of it?     → Executive
What could go wrong from here — and what would settle it?               → Executive
Has anyone filed anything close to "Novara"?                             → Trademark
Where am I concentrated?                                                 → Wealth, after sign-in
Which clients are due a review this month?                               → Mandates, after sign-in
```

## Authentication

- **The 07:00 Brief, Executive and Trademark screening** need no token. They are rate-limited per client and hold no personal data.
- **Wealth and Mandates** use OAuth 2.1 with PKCE and Dynamic Client Registration. Discovery is open — `initialize`, `tools/list` and `ping` answer without a token, so a client can inspect the surface before anyone signs in. Any `tools/call` without a token answers `401` with an RFC 9728 `WWW-Authenticate` challenge, and a compliant client completes sign-in on its own.
- Your assistant receives a scoped, short-lived token — never your password — and your account's own permissions apply.

## What this repository is

Connection metadata, and nothing else. There is no application code, no data and no business logic here — the servers are hosted by Antevo and are not open source.

| Path | What it is |
|:--|:--|
| [`registry/*/server.json`](registry) | Mirrors of the five published [MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=ch.antevo) entries |
| [`.cursor-plugin/marketplace.json`](.cursor-plugin/marketplace.json) | The five plugins, for the Cursor marketplace |
| [`plugins/*/`](plugins) | Each plugin's `.cursor-plugin/plugin.json`, `mcp.json`, README and logo |
| [`powers/*/`](powers) | Kiro powers in the [Agent Plugins](https://agent-plugins.org) format: `plugin.json`, `mcp.json` and a README each, for the three public servers |
| [`gemini-extension.json`](gemini-extension.json) | Makes this repository a Gemini CLI extension |
| [`INSTALL.md`](INSTALL.md) | One-click install links for Cursor and VS Code |

CI runs on every push: every JSON file parses, Cursor's own [plugin-template validator](https://github.com/cursor/plugin-template) passes, each `powers/*/` manifest validates against the published Agent Plugins schemas, and each `registry/*/server.json` still matches what is published.

## Registry

All five servers are listed and active in the official MCP Registry under the `ch.antevo` namespace, verified on the `antevo.ch` domain:

`ch.antevo/0700-brief` · `ch.antevo/executive` · `ch.antevo/trademark` · `ch.antevo/wealth` · `ch.antevo/mandates`

## FAQ

### Do I need an account?

Not for The 07:00 Brief, Executive or trademark screening. Wealth needs an [Antevo Wealth](https://antevo.ch/wealth) account; Mandates needs a firm account, [by arrangement](https://antevo.ch/mandate).

### Why is Trademark on a different host?

It runs as a separate service at `trademark.antevo.ch`. It speaks Streamable HTTP only.

### What does my assistant receive?

The information a server returns to your question. Your chosen AI service handles it under its own terms.

### Does Antevo give investment advice?

No. It is editorial market intelligence, public-register data and a reading of your own record. Technical signals say how indicators lean, never buy or sell.

### Who runs Antevo?

Antevo ([antevo.ch](https://antevo.ch)) is operated by VestAI LTD, registered in Limassol, Cyprus, with an operating office in Zürich. It serves clients in Switzerland, and Antevo Wealth is Swiss-hosted: records and documents are held in Switzerland.

### Is there a website as well as the servers?

Yes. The free trademark clearance check also runs on the web, with no account, at [antevo.ch/trademark](https://antevo.ch/trademark/). The 07:00 Brief is described at [0700.io](https://0700.io) and the Executive Brief at [antevo.ch/executive](https://antevo.ch/executive/).

## Privacy and support

- Privacy policy: <https://antevo.ch/policies/privacy-policy>
- Support: [contact@antevo.ch](mailto:contact@antevo.ch)

## Security

Report a vulnerability privately to **contact@antevo.ch** — see [SECURITY.md](SECURITY.md).

## License

The contents of this repository are MIT licensed — see [LICENSE](LICENSE) and [NOTICE](NOTICE). The Antevo services these files point at, and the Claude plugins and skills in [ANTEVO-CH/plugins](https://github.com/ANTEVO-CH/plugins), are not covered.

---

<p align="center">
  <b>Antevo</b> · serves Switzerland, Swiss-hosted · operated by VestAI LTD, Cyprus · <a href="https://antevo.ch">antevo.ch</a> · <a href="https://antevo.ch/mcp">Connect</a> · <a href="mailto:contact@antevo.ch">contact@antevo.ch</a><br>
  <sub>Intelligence, not advice.</sub>
</p>
