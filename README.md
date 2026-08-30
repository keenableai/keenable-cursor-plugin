# Keenable plugins for Cursor

Keyless web search and clean page extraction for the Cursor agent, from
[Keenable](https://keenable.ai). No signup, no API key.

This repository is a Cursor plugin marketplace. It currently holds one plugin:

| Plugin | What it does |
|---|---|
| [`keenable`](./plugins/keenable) | `search_web_pages` and `fetch_page_content` over Keenable's hosted MCP server, plus two research skills. |

## Layout

```text
.cursor-plugin/marketplace.json   # marketplace manifest
plugins/keenable/
├── .cursor-plugin/plugin.json    # plugin manifest
├── assets/logo.svg               # marketplace logo
├── mcp.json                      # MCP server definition
├── skills/keenable-web/SKILL.md
└── skills/keenable-deep-research/SKILL.md
```

## Try it before it lands in the marketplace

Clone the repo and load the plugin from `~/.cursor/plugins/local`, or point a
team marketplace at this repository from Dashboard → Plugins → Add Marketplace →
Import from Repo.

## Validate

This repo follows the layout of
[`cursor/plugin-template`](https://github.com/cursor/plugin-template). To check
it, run that template's validator from the root of this repository:

```bash
curl -sSL https://raw.githubusercontent.com/cursor/plugin-template/main/scripts/validate-template.mjs -o /tmp/validate-template.mjs
node /tmp/validate-template.mjs
```

## License

MIT
