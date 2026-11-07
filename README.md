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

## 中文

CarbonMeld 的远程 MCP 服务器为 AI 助手提供自愿碳市场项目的只读研究：根据各登记处公开的文件得出的评分、登记处自己的数据，以及每个评分背后的方法。

- 服务器 URL：`https://carbonmeld.com/api/v1/mcp`（Streamable HTTP）
- 登录：使用您的 CarbonMeld 账户通过 OAuth 2.1 登录。您在 CarbonMeld 页面上批准连接，并可随时在账户页面（“已连接的助手”）断开与助手的连接。
- 仅限读取：这些工具不能更改任何内容，也不能买卖或付款。
- 官方 MCP Registry：`com.carbonmeld/carbonmeld`，其描述见 [`server.json`](server.json)
- 工具列表见上方英文表格。各客户端的完整连接步骤：https://carbonmeld.com/zh/premium/mcp/

本仓库只有服务器的公开描述（MCP Registry 条目和客户端示例），不含服务器代码。

CarbonMeld 不出售碳信用。评分仅供参考，不构成投资建议。登记处数据按登记处公布的内容显示，并注明日期。

## 日本語

CarbonMeldのリモートMCPサーバーは、AIアシスタントに自発的炭素市場のプロジェクトに関する読み取り専用の調査を提供します。レジストリが公開する文書にもとづく評価、レジストリ自身のデータ、そして各評価の背後にある評価方法です。

- サーバーURL：`https://carbonmeld.com/api/v1/mcp`（Streamable HTTP）
- サインイン：CarbonMeldのアカウントでOAuth 2.1によりサインインします。CarbonMeldのページで接続を承認し、アカウントページ（「接続中のアシスタント」）からいつでも接続を解除できます。
- 読み取りのみ：ツールは何も変更できず、売買や支払いもできません。
- 公式MCP Registry：`com.carbonmeld/carbonmeld`（内容は[`server.json`](server.json)に記載）
- ツールの一覧は上の英語の表をご覧ください。各クライアントの詳しい接続手順：https://carbonmeld.com/ja/premium/mcp/

このリポジトリにはサーバーの公開説明（MCP Registryの掲載情報とクライアントの設定例）だけがあり、サーバーのコードは含まれていません。

CarbonMeldはカーボンクレジットを販売しません。評価は参考情報であり、投資助言ではありません。レジストリのデータは、レジストリが公開したとおりに日付とともに示します。

## License

[MIT](LICENSE)
