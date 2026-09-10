# Central Command — MCP Server

**Remote [Model Context Protocol](https://modelcontextprotocol.io) server for crypto trading intelligence and paper-first AI‑agent execution.** Pay‑per‑use via [x402](https://www.x402.org/) on Base USDC, a prepaid API key, or free linked Connect keys.

> This repository documents the **public interface** of the Central Command MCP server — tools, connection, pricing, and discovery metadata. The trading terminal and server implementation are proprietary and closed‑source. The server is **remote**; there is nothing to install.

| | |
|---|---|
| 🌐 Product | https://centralcommand.io |
| 🧩 MCP page | https://centralcommand.io/mcp |
| 🛰️ Smithery | https://smithery.ai/servers/@lefkotyler/central-command |
| 🆔 MCP Registry | `io.github.tlefko/central-command` |

## What it does

**36+ live endpoints** exposing crypto trading intelligence to any MCP client:

- **Market‑intel packs** — funding rates, liquidations, and derivatives data
- **Sanitized fade signals** — crowd‑positioning intelligence
- **Backtests** — historical strategy evaluation
- **Agent strategy console** — paper‑first strategy design and execution
- **Position sizing** — risk‑aware sizing helpers

Every endpoint publishes an explicit price in `cc.list_catalog`.

## Connect (one line)

Add to your MCP client — Claude Desktop, Cursor, Smithery, Glama, or any Streamable HTTP client:

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
- **Smithery:** https://smithery.ai/servers/@lefkotyler/central-command
- **Agent crawl file:** `llms.txt` (served from the MCP docs endpoint)

## Docs in this repo

- [`docs/quickstart.md`](docs/quickstart.md) — connect from Claude Desktop / Cursor
- [`docs/capabilities.md`](docs/capabilities.md) — endpoint families, pricing model, x402 flow
- [`server.json`](server.json) — official MCP Registry manifest
- [`smithery.yaml`](smithery.yaml) — Smithery server metadata

## License

The interface documentation in this repository may be used freely to integrate with the service. The Central Command server and terminal are **proprietary**. See [SECURITY.md](SECURITY.md) for responsible disclosure.
