# Strategy Radar

**What changed today for your company's strategy.**

Every morning Antevo writes a business board: the risks and opportunities for companies
from trade and tariffs, regulation, supply and inputs, shipping, energy, demand,
currencies, funding and rates, labour, technology, cyber, geopolitics and climate. Each
entry gives its theme and the exposures it touches, its impact, likelihood and trend in
words, what to watch, and two or three possible responses with their reasons.

The matching happens in your own assistant. Five short setup questions become a profile
that stays with your assistant; no tool here takes company details, so nothing about your
company reaches Antevo.

**Public. No account, no key.** Remote MCP server over Streamable HTTP:

`https://api.antevo.ch/mcp/strategy/mcp`

## Install in Cursor

One click from the Cursor marketplace, or add this to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "antevo-strategy-radar": {
      "url": "https://api.antevo.ch/mcp/strategy/mcp"
    }
  }
}
```

## What you can ask

- Set up Antevo Strategy Radar for my company.
- What changed today for my company's strategy?
- Which entries on today's business board touch a company that imports from Asia and sells in Europe?
- Show me last Monday's business board.

## What it will not do

Both tools are read-only. Nothing here can place a trade, move money or change a record.
The board names no news outlets; official bodies are named when a figure or decision is
theirs. Its options are possible responses with reasons, never advice.

## Privacy and support

- Privacy policy: <https://antevo.ch/policies/privacy-policy>
- Support: [contact@antevo.ch](mailto:contact@antevo.ch)
- Security reports: [SECURITY.md](../../SECURITY.md)

The page: <https://antevo.ch/executive/strategy/> · set-up guide: <https://antevo.ch/mcp/strategy/>
