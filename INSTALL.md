# Install links

Same five servers everywhere; only the wrapper changes. Every one is a remote Streamable HTTP server, so there is nothing to run locally.

GitHub doesn't open app links (`cursor://`, `vscode:`), so the VS Code links below go through Microsoft's https redirect, and Cursor's one-click buttons are on [antevo.ch/mcp](https://antevo.ch/mcp/#connections). In Cursor you can also paste the [`mcp.json`](#cursor) below.

## The 07:00 Brief

`https://api.antevo.ch/mcp/0700/mcp`

Public, no account.

- **Claude**: [open in Claude's directory](https://claude.ai/directory/the-0700-brief), then Connect
- **VS Code**: [add to VS Code](https://vscode.dev/redirect/mcp/install?name=the-0700-brief&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.antevo.ch%2Fmcp%2F0700%2Fmcp%22%7D)
- **Cursor**: one click on [antevo.ch/mcp](https://antevo.ch/mcp/#connections), or the [`mcp.json`](#cursor) below
- **Claude Code**: `claude mcp add --transport http the-0700-brief https://api.antevo.ch/mcp/0700/mcp`

## Antevo Executive Brief

`https://api.antevo.ch/mcp/executive/mcp`

Public, no account.

- **Claude**: [open in Claude's directory](https://claude.ai/directory/antevo-executive-brief), then Connect
- **VS Code**: [add to VS Code](https://vscode.dev/redirect/mcp/install?name=antevo-executive&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.antevo.ch%2Fmcp%2Fexecutive%2Fmcp%22%7D)
- **Cursor**: one click on [antevo.ch/mcp](https://antevo.ch/mcp/#connections), or the [`mcp.json`](#cursor) below
- **Claude Code**: `claude mcp add --transport http antevo-executive https://api.antevo.ch/mcp/executive/mcp`

## Antevo Trademark

`https://trademark.antevo.ch/mcp`

Screening (five tools) needs no account; the other eleven, such as the watchlist, filer follows and investigations, ask you to sign in.

- **Claude**: Customize → Connectors → Add → Add custom connector, and paste the address
- **VS Code**: [add to VS Code](https://vscode.dev/redirect/mcp/install?name=antevo-trademark&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Ftrademark.antevo.ch%2Fmcp%22%7D)
- **Cursor**: one click on [antevo.ch/mcp](https://antevo.ch/mcp/#connections), or the [`mcp.json`](#cursor) below
- **Claude Code**: `claude mcp add --transport http antevo-trademark https://trademark.antevo.ch/mcp`

## Antevo Wealth

`https://api.antevo.ch/mcp/wealth/mcp`

Your own household, after sign-in.

- **Claude**: [open in Claude's directory](https://claude.ai/directory/antevo-wealth), then Connect
- **VS Code**: [add to VS Code](https://vscode.dev/redirect/mcp/install?name=antevo-wealth&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.antevo.ch%2Fmcp%2Fwealth%2Fmcp%22%7D)
- **Cursor**: one click on [antevo.ch/mcp](https://antevo.ch/mcp/#connections), or the [`mcp.json`](#cursor) below
- **Claude Code**: `claude mcp add --transport http antevo-wealth https://api.antevo.ch/mcp/wealth/mcp`

## Antevo Mandates

`https://api.antevo.ch/mcp/mandates/mcp`

For firms, by arrangement.

- **Claude**: Customize → Connectors → Add → Add custom connector, and paste the address
- **VS Code**: [add to VS Code](https://vscode.dev/redirect/mcp/install?name=antevo-mandates&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.antevo.ch%2Fmcp%2Fmandates%2Fmcp%22%7D)
- **Cursor**: one click on [antevo.ch/mcp](https://antevo.ch/mcp/#connections), or the [`mcp.json`](#cursor) below
- **Claude Code**: `claude mcp add --transport http antevo-mandates https://api.antevo.ch/mcp/mandates/mcp`

## Cursor

Add the ones you want to `~/.cursor/mcp.json` (all projects) or `.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "the-0700-brief": {
      "url": "https://api.antevo.ch/mcp/0700/mcp"
    },
    "antevo-executive": {
      "url": "https://api.antevo.ch/mcp/executive/mcp"
    },
    "antevo-trademark": {
      "url": "https://trademark.antevo.ch/mcp"
    },
    "antevo-wealth": {
      "url": "https://api.antevo.ch/mcp/wealth/mcp"
    },
    "antevo-mandates": {
      "url": "https://api.antevo.ch/mcp/mandates/mcp"
    }
  }
}
```

## Gemini CLI

All five at once, as an extension:

```sh
gemini extensions install https://github.com/ANTEVO-CH/antevo-mcp
```

## Everything else

Any MCP client takes the URL directly. Windsurf, Zed, Goose and the rest accept a remote Streamable HTTP server: paste the address and you are connected.
