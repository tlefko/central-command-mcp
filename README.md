# Central Command — MCP Server

**Remote [Model Context Protocol](https://modelcontextprotocol.io) server for crypto trading intelligence and paper-first AI‑agent execution.** Pay‑per‑use via [x402](https://www.x402.org/) on Base USDC, a prepaid API key, or free linked Connect keys.

> This repository documents the **public interface** of the Central Command MCP server — tools, connection, pricing, and discovery metadata. The trading terminal and server implementation are proprietary and closed‑source. The server is **remote**; there is nothing to install.

| | |
|---|---|
| 🌐 Product | https://centralcommand.io |
| 🧩 MCP page | https://centralcommand.io/mcp |
| 🆔 MCP Registry | `io.github.tlefko/central-command` |

## Central Command, the product

The MCP server is one part of [Central Command](https://centralcommand.io): a crypto trading terminal and AI agent builder for BloFin accounts, on the web and as a desktop app.

- **A BloFin trading bot without code:** write entries, exits and risk in plain English at [centralcommand.io/agents/new](https://centralcommand.io/agents/new). The agent backtests on closed BloFin candles with fees and funding, runs on paper, and goes live on your own BloFin account when you choose.
- **TradingView alerts to BloFin:** a signal agent takes your TradingView webhook and places the trade on BloFin ([setup guide](https://centralcommand.io/blog/tradingview-alerts-to-blofin)).
- **Prop firm challenge backtests:** test an agent against a funded-account challenge's rules (profit target, daily loss, static or trailing max loss, trading days, time limit) and see pass or fail, the rule and day that ended it, and the pass rate across up to 60 start days ([how it works](https://centralcommand.io/docs/ai-agents)).
- **Your own AI:** connect Claude, Cursor or any MCP client (below) to research, backtest and run paper-first agents from one conversation.

### Start free

Central Command is free with a BloFin account opened through our referral link, for as long as you trade through us. Or take the 10-day free trial: no card, no wallet, nothing renews.

1. Create an account at https://centralcommand.io/signup.
2. Choose **Free with BloFin** and connect BloFin in one click (no BloFin account yet? open one at https://partner.blofin.com/d/centralcommand), or choose the **10-day free trial**.
3. Trade from the terminal at https://centralcommand.io/dataterminal, or describe a strategy in plain English at https://centralcommand.io/agents/new: backtest it, run it on paper, and go live when you choose.

BloFin's normal trading fees still apply. Central Command trades BloFin perpetual futures only. Leveraged trading can lose all of your money.

## What it does

**26 live endpoints** exposing crypto trading intelligence to any MCP client:

- **Market‑intel packs** — funding rates, liquidations, and derivatives data
- **Sanitized fade signals** — crowd‑positioning intelligence
- **Backtests** — historical strategy evaluation
- **Agent strategy console** — paper‑first strategy design and execution
- **Position sizing** — risk‑aware sizing helpers

Every endpoint publishes an explicit price in `cc.list_catalog`.

## Connect (one line)

Add to your MCP client — Claude Desktop, Cursor or any Streamable HTTP client:

```json
{
  "mcpServers": {
    "central-command": {
      "url": "https://rtcelwjnrbmfmrywacky.supabase.co/functions/v1/mcp",
      "headers": { "X-Api-Key": "x402_YOUR_KEY" }
    }
  }
}
```

Omit `X-Api-Key` for **pure x402 pay‑per‑use** — a tool returns a `402` with accepts, and the client retries with an `X-PAYMENT` proof (also accepted as the tool arg `__x_payment`). Linked Connect keys get a **free tier**.

## Pricing

Pay‑per‑use from **~$0.0005 USDC per call** on Base. No account required for x402. Free for linked Connect keys.

## Execution safety model

Execution is **paper‑first**. Live orders require an explicit `confirm_live` step, and deterministic checks — account permissions, position sizing, and exchange constraints — gate every proposed order. The model is not the only thing deciding whether an action can proceed.

## Discovery

- **Official MCP Registry:** `io.github.tlefko/central-command`
- **Agent crawl file:** `llms.txt` (served from the MCP docs endpoint)

## Docs in this repo

- [`docs/quickstart.md`](docs/quickstart.md) — connect from Claude Desktop / Cursor
- [`docs/capabilities.md`](docs/capabilities.md) — endpoint families, pricing model, x402 flow
- [`server.json`](server.json) — official MCP Registry manifest
- [`smithery.yaml`](smithery.yaml) — Smithery server metadata

## License

The interface documentation in this repository may be used freely to integrate with the service. The Central Command server and terminal are **proprietary**. See [SECURITY.md](SECURITY.md) for responsible disclosure.
