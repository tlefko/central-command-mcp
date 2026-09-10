# Capabilities

Central Command exposes **36+ live endpoints**. Each returns structured output with tool annotations and output schemas for good client UX, and each carries an explicit price surfaced by `cc.list_catalog`.

## Endpoint families

| Family | What it provides |
|---|---|
| Market‑intel packs | Funding rates, liquidations, and derivatives market structure |
| Fade signals | Sanitized crowd‑positioning / contrarian signals |
| Strategy discovery | Public strategies and performance surfaces |
| Backtests | Historical evaluation of a strategy's rules |
| Agent strategy console | Paper‑first strategy design and execution (`cc.agent_strategy`) |
| Position sizing | Risk‑aware sizing given account and market constraints |

## Payment model (x402)

Three ways to pay, chosen per request:

1. **Pure x402 pay‑per‑use** — no account. Call → `402` with accepts → settle Base USDC → retry with `X-PAYMENT`.
2. **Prepaid `X-Api-Key`** — register once, draw down a balance.
3. **Linked Connect keys** — free tier for connected accounts.

## Execution safety

- **Paper‑first:** strategies run against paper execution by default.
- **`confirm_live` gate:** promoting to live orders is an explicit, separate step.
- **Deterministic checks:** account permissions, position sizing, and exchange constraints are enforced in code around every proposed order — independent of the model's judgment.

## Client compatibility

Works with any Streamable HTTP MCP client, including Claude Desktop, Cursor, Smithery, and Glama. Tools, resources, and prompts are all advertised for client‑side UX.
