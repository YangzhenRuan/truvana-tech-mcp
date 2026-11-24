# Truvana Tech MCP server

[![Truvana Tech MCP connector](https://glama.ai/mcp/connectors/com.truvanatech/site/badges/score.svg)](https://glama.ai/mcp/connectors/com.truvanatech/site)

**Card processing, payment fees and POS answers for small restaurants and stores, inside ChatGPT, Claude and other AI assistants.**

A free, public [MCP](https://modelcontextprotocol.io) server from [Truvana Tech](https://truvanatech.com?utm_source=github&utm_medium=readme&utm_campaign=mcp). Connect it to your AI assistant, then ask about card fees, surcharge and cash discount rules in your state, delivery-app commissions or leaving a processor contract. The assistant answers from Truvana Tech's published guides and runs the same calculators as [truvanatech.com/tools](https://truvanatech.com/tools?utm_source=github&utm_medium=readme&utm_campaign=mcp), so the numbers match the website.

```
https://truvanatech.com/mcp
```

No sign-in, no API key, nothing to install. Listed in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers?search=com.truvanatech) as `com.truvanatech/site`.

## What you can ask

- "My statement shows $412.50 in fees on $12,500 in card sales across 900 transactions. What's my real rate?"
- "Can I add a credit card surcharge in Maryland? What's the most I can charge?"
- "We sell $40 orders on a delivery app at 30% commission, 300 a month. What does the app keep in a year?"
- "I have 14 months left on my processing contract and a $495 exit fee. Switching saves $90 a month. Leave now or wait?"
- "What should a cash discount sign say in Virginia?"
- "Which POS works for a convenience store that takes EBT?"

## Tools

| Tool | What it does |
|---|---|
| `about_site` | What the library covers and the free calculators. Call first. |
| `search_site` | Search Truvana Tech's guides, articles and FAQs (titles, summaries, source URLs). |
| `read_page` | Full text of one page from a search result. |
| `card_fee_calculator` | Your real card processing rate from one statement: effective rate, cost per $100 and per year, compared with common example flat rates. |
| `card_surcharge_rules` | Surcharge and cash rules for any US state (all 50 and DC), the highest surcharge allowed, and what a surcharge or cash discount would recover. |
| `card_price_sign_check` | The percent a cash discount, two-price or surcharge sign may show in a state. |
| `contract_exit_cost` | Early termination fee vs the savings you give up by waiting, payback months, and what a machine lease still bills. |
| `delivery_commission_calculator` | What delivery apps keep per order, month and year; the markup that keeps your take; what your own ordering page saves. |
| `ask_expert` | A question still open? With your OK, your name and email, the assistant sends it to Truvana Tech's specialists, and a person replies by email (English or Spanish). |

Every tool only reads Truvana Tech's published pages, except `ask_expert`, which sends only what you approve.

## Connect it

**Claude** (claude.ai and desktop, every plan; Free allows one custom connector): Customize > Connectors > **+ Add** > **Add custom connector**. Name it, paste `https://truvanatech.com/mcp`, choose **No sign in**, then **Add**. In a chat: **+** > Connectors, switch it on. ([Claude help](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp))

**ChatGPT** (Pro, Business, Enterprise, Edu; web): **Plugins** > **+** > **Add custom MCP server**. Name it, paste the URL under Connection, accept the notice, **Create as a plugin**. In a new chat type **@** and pick it. ([OpenAI help](https://help.openai.com/en/articles/12584461))

**Claude Code**:
```bash
claude mcp add --transport http truvana-tech https://truvanatech.com/mcp
```
Or clone this repo: its `.mcp.json` connects it for the project.

**Cursor** (`~/.cursor/mcp.json`):
```json
{ "mcpServers": { "truvana-tech": { "url": "https://truvanatech.com/mcp" } } }
```

**VS Code (GitHub Copilot)**: Command Palette > **MCP: Add Server** > HTTP > paste the URL.

**Gemini CLI**:
```bash
gemini mcp add --transport http truvana-tech https://truvanatech.com/mcp
```

## Try it without an AI

```bash
curl -s https://truvanatech.com/mcp -H 'content-type: application/json' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"card_surcharge_rules","arguments":{"state":"Maryland"}}}'
```

## Also from Truvana Tech

- [Restaurant Health Report](https://github.com/YangzhenRuan/restaurant-health-report): a free, open-source AI skill that builds a 7-page check-up of any restaurant from public sources. It uses this server when it's connected.
- [Free tools](https://truvanatech.com/tools?utm_source=github&utm_medium=readme&utm_campaign=mcp) on the website.

Rules and numbers are general information, not legal or financial advice. Truvana Tech is a local team in DC, Maryland and Northern Virginia that installs POS systems and card machines for restaurants and small businesses, in English or Spanish.

## License

This repository (README and config) is MIT licensed. The server is operated by Truvana Tech.
