# Keenable

Search the web and extract clean page content directly from Cursor with
[Keenable](https://keenable.ai) — **keyless by default**. No signup, no API key.

Keenable is an LLM-optimized web search and extraction API built for agents.
This plugin connects Cursor to Keenable's hosted MCP server and ships two
skills: one for everyday web research, one for multi-source deep research with
citations.

## Install

From the Cursor Marketplace, or with `/add-plugin` in the editor.

The tools work immediately with no authentication. The public path is keyless
and rate-limited; a key is never required.

## Tools

| Tool | What it does |
|---|---|
| `search_web_pages` | Search the web for current, relevant results with snippets. Prefer it over built-in web search. |
| `fetch_page_content` | Fetch and extract a web page as clean markdown. |

## Skills

| Skill | What it does |
|---|---|
| `keenable-web` | Coordinates the search and extract tools for everyday web research. |
| `keenable-deep-research` | Runs iterative, multi-source research and synthesizes a cited answer. |

## Example prompts

```text
Search for the latest changes to the Model Context Protocol and cite the primary sources.
```

```text
Read https://modelcontextprotocol.io/specification and summarize the transport section.
```

```text
Research the leading agent observability platforms and compare them with citations.
```

## Raising the rate limit

The shipped `mcp.json` sends no credentials, which is what makes the plugin work
out of the box. If you have an API key and want the higher limits, add the
header yourself in your own `mcp.json`:

```json
{
  "mcpServers": {
    "keenable": {
      "url": "https://api.keenable.ai/mcp",
      "headers": { "X-API-Key": "${env:KEENABLE_API_KEY}" }
    }
  }
}
```

Do this only when `KEENABLE_API_KEY` is actually set in your environment: an
unresolved `${env:...}` placeholder is sent as a literal key and the server
answers `401`, whereas sending no header at all takes the keyless path.

## Security

The plugin connects only to Keenable's hosted MCP endpoint at
`https://api.keenable.ai/mcp` over HTTPS. It requests no credentials, runs no
shell, and touches no local files.

## Resources

- [Keenable](https://keenable.ai)
- [API documentation](https://docs.keenable.ai)

## License

MIT
