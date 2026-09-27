# Eulerpool MCP Server

Financial data for AI agents. A hosted [Model Context Protocol](https://modelcontextprotocol.io) server exposing the [Eulerpool Financial Data API](https://eulerpool.com/developers) as 250+ tools: stocks, ETFs, funds, fundamentals, estimates, insider trades, 13F filings, congress trading, options flow, macro series (FRED, ECB, IMF, World Bank, Eurostat, OECD, BIS), crypto, FX and commodities.

Eulerpool is The Financial Data Company.

## Endpoints

| Endpoint | Auth | Use with |
|---|---|---|
| `https://eulerpool.com/mcp` | OAuth (log in, no key handling) | Claude.ai connectors, ChatGPT connectors |
| `https://api.eulerpool.com/mcp` | `Authorization: Bearer YOUR_API_KEY` | Cursor, Claude Code, VS Code, Windsurf, any MCP client |

Transport: Streamable HTTP (SSE fallback). Same tools on both endpoints.

Get a free API key at [eulerpool.com/developers/register](https://eulerpool.com/developers/register). No credit card required.

## Setup

### Claude Code

```bash
claude mcp add --transport http eulerpool https://api.eulerpool.com/mcp \
  --header "Authorization: Bearer YOUR_API_KEY"
```

### Cursor

`.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "eulerpool": {
      "url": "https://api.eulerpool.com/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

### VS Code

`.vscode/mcp.json`:

```json
{
  "servers": {
    "eulerpool": {
      "type": "http",
      "url": "https://api.eulerpool.com/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

### Claude.ai / ChatGPT

Add a custom connector and paste `https://eulerpool.com/mcp`. Complete the OAuth login; no key to copy.

## Example prompts

- "Compare the free cash flow margins of Apple, Microsoft and Google over the last 5 years"
- "Which stocks did US senators buy last month?"
- "Plot ECB deposit rate against euro area core inflation since 2015"
- "Show the largest 13F position changes at Berkshire Hathaway last quarter"

The agent selects the right tools automatically.

## Tool coverage

Equities (profiles, quotes, candles, financial statements, estimates, dividends, splits, peers, segments, KPIs, ownership, insider trades US + EU, short interest, analyst grades, fair value, quality scores) · ETFs and mutual funds (holdings, sectors, countries, flows) · Macro (FRED, ECB, IMF, World Bank, Eurostat, OECD, BIS, country risk, economic calendar) · Alternative data (13F, superinvestors, congress trading, COT, options flow, dark pool, social sentiment) · Crypto, DeFi and DEX · Forex · Commodities and futures curves · Bonds and yield curves · Earnings call transcripts · Screener · Backtesting · Portfolio analytics.

Full REST reference and OpenAPI spec: [eulerpool.com/developers](https://eulerpool.com/developers) · [OpenAPI JSON](https://api.eulerpool.com/api/1/documentation/json)

## Discovery

Manifest: [`https://eulerpool.com/.well-known/mcp.json`](https://eulerpool.com/.well-known/mcp.json)

## SDKs

Prefer a typed client instead of MCP? Official SDKs: [Python](https://github.com/eulerpool/eulerpool-python) · [TypeScript](https://github.com/eulerpool/eulerpool-js) · [Go](https://github.com/eulerpool/eulerpool-go) · [Java](https://github.com/eulerpool/eulerpool-java) · [R](https://github.com/eulerpool/eulerpool-r) · [PHP](https://github.com/eulerpool/eulerpool-php) · [Rust](https://github.com/eulerpool/eulerpool-rust) · [C++](https://github.com/eulerpool/eulerpool-cpp)

## Pricing

Free tier for non-commercial use; paid plans for commercial use. Details at [eulerpool.com/financial-data-api/pricing](https://eulerpool.com/financial-data-api/pricing).

## License

[MIT](LICENSE). Copyright (c) 2026 Eulerpool Research Systems.

## Support

api@eulerpool.com · [Documentation](https://eulerpool.com/developers/mcp-server)
