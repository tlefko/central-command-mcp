# Quickstart

The Central Command MCP server is **remote** (Streamable HTTP). No install, no local runtime.

## Claude Desktop

Add to `claude_desktop_config.json`:

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

Restart Claude Desktop. The Central Command tools appear in the tool picker.

## Cursor

Add the same server block to your MCP settings (`~/.cursor/mcp.json` or the in‑app MCP settings).

## No key? Pay‑per‑use with x402

Leave `X-Api-Key` out entirely. Calls that require payment return an HTTP `402` describing the accepted payment; settle the Base USDC amount and retry with the `X-PAYMENT` proof header (or the `__x_payment` tool argument). Prices per endpoint are listed in `cc.list_catalog`.

## First calls to try

1. `cc.list_catalog` — list every endpoint and its price
2. Funding / liquidation intel packs — current derivatives positioning
3. `cc.agent_strategy` — design a strategy in **paper** mode (live orders require `confirm_live`)
