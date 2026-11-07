# CarbonMeld MCP server

CarbonMeld's remote MCP server gives AI assistants read-only research on voluntary carbon credit projects:
ratings built from the documents registries publish, the registries' own data, and the method behind each rating.

- **Server URL:** `https://carbonmeld.com/api/v1/mcp` (Streamable HTTP)
- **Sign-in:** OAuth 2.1 with your CarbonMeld account. You approve the connection on a CarbonMeld page, and you can
  disconnect an assistant at any time from your account page («Connected assistants»).
- **Read-only:** the tools cannot change anything, buy, sell or make a payment.
- **Official MCP Registry:** `com.carbonmeld/carbonmeld`, described by [`server.json`](server.json)

This repository holds the server's public description only: its registry entry and client examples. The server runs at
the URL above; its code is not here.

## Tools

| Tool | What it returns |
|---|---|
| `search_projects` | Projects found by words, standard, country, methodology, sector, developer, minimum rating or claim (CORSIA, ICVCM CCP, Article 6, removal) |
| `get_project` | One project's record: rating and analysis, red flags, registry status, vintages issued and retired, claims, developer, buyers and documents |
| `get_projects` | Several project records in one call |
| `check_offer` | An offer you received, checked against public registry facts: registration, vintage issued and still available, CORSIA / CCP / Article 6 claims, seller vs developer |
| `corsia_supply` | CORSIA registry labels by registry and phase, with the highest-rated First Phase projects |
| `get_buyer` | An organisation named as beneficiary of public retirements: tonnes, the projects they came from and those projects' ratings (a beneficiary is not necessarily the buyer) |
| `get_methodology` | One methodology: its identity card with sources, the rules CarbonMeld applies, its version history and its projects |
| `get_ranking` | Leaderboards by sector, country, standard or methodology |
| `get_standard` | One crediting standard: its identity card, the programme rules applied, its methodologies and projects |
| `get_developer` | One project developer: its projects, standards and countries (no company-level score) |
| `ccp_tracker` | The ICVCM Core Carbon Principles assessments of methodologies, with the number of projects CarbonMeld tracks under each |
| `my_portfolio` | The projects saved in your own CarbonMeld portfolio, with their recent changes |
| `what_changed` | The last 30 days of rule-setter notices and registry label changes |
| `get_method` | CarbonMeld's rating method and its rules |
| `search_articles` | CarbonMeld's articles in English, Chinese and Japanese |

## Connect

Full, current steps for every client, including Claude Code, Microsoft 365 Copilot and the API-key alternative:
**https://carbonmeld.com/premium/mcp/**

- **ChatGPT:** chatgpt.com/plugins → **+** → **Add custom MCP server** → the server URL → OAuth → **Create as a
  plugin**. Sign in on the CarbonMeld page that opens, then approve.
- **Claude:** Customize → Connectors → **Add custom connector** → the server URL. You can also add CarbonMeld from
  Claude's connectors directory. Sign in on the CarbonMeld page that opens, then approve.
- **Cursor:** put [`examples/cursor-mcp.json`](examples/cursor-mcp.json) in `~/.cursor/mcp.json` (or `.cursor/mcp.json`
  for one project). Cursor asks you to sign in.
- **VS Code:** run **MCP: Add Server** → **HTTP** → the server URL → server ID `carbonmeld` → **Global**. The resulting entry, in `~/.copilot/mcp-config.json`,
  is [`examples/vscode-mcp.json`](examples/vscode-mcp.json). VS Code asks you to sign in.

## Notes

CarbonMeld sells no carbon credits. Ratings are informational, not investment advice. Registry data is shown as the
registries publish it, with its date.

Questions: hello@carbonmeld.com

## License

[MIT](LICENSE)
