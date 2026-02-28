
!!! note "Content disclaimer"

    Please view the third-party content disclaimer [here](https://github.com/0xPolygon/polygon-docs/blob/main/CONTENT_DISCLAIMER.md).

# Codex

[Codex](https://www.codex.io/) is a blockchain data API that provides real-time and historical DeFi data across 100+ networks via GraphQL, including Polygon PoS. With access to over 70 million tokens and 700 million wallets, Codex delivers sub-second data for building token explorers, trading bots, portfolio trackers, and DeFi dashboards.

## GraphQL API

Codex exposes a single GraphQL endpoint with 73 query operations for fetching current and historical data. All requests are sent as HTTPS POST to `https://graph.codex.io/graphql`.

Key query capabilities include:

| **Category** | **Data Available** |
| --- | --- |
| **Token Data** | Real-time and historical prices, OHLCV candlestick charts, metadata, and scam filtering |
| **DEX Trades** | Swap events across decentralized exchanges with pair-level detail |
| **Liquidity Pools** | Pool reserves, volume, fees, and newly created pairs |
| **Wallet Activity** | Token balances, transaction history, and holdings across 100+ networks |
| **Analytics** | Aggregated volume, liquidity, unique wallet metrics, and holder tracking |
| **Launchpad Monitoring** | Alerts for new token launches and early token discovery |

## Real-Time Subscriptions

Codex supports 25 real-time data streams via WebSocket (`wss://graph.codex.io/graphql`), enabling live updates for:

- Token price changes and trade events
- New and updated DEX pairs
- Wallet activity and balance changes
- Launchpad and new token events

## Webhooks

Webhooks provide push-based notifications for on-chain events, delivering data to your server as events occur without requiring persistent WebSocket connections.

## SDK

Codex provides a TypeScript/JavaScript SDK that acts as a thin wrapper around the GraphQL API with predefined queries, mutations, and built-in subscription connection handling. Alternatively, you can write custom GraphQL queries directly against the API for more flexibility.

## Getting Started

### 1. Create an account

Sign up at [dashboard.codex.io](https://dashboard.codex.io/signup) to create your Codex account.

### 2. Get your API key

Copy your API key from the API Keys page in the dashboard.

### 3. Make your first request

All requests require an `Authorization` header with your API key.

```bash
curl -X POST https://graph.codex.io/graphql \
  -H "Content-Type: application/json" \
  -H "Authorization: YOUR_API_KEY" \
  -d '{"query": "{ getNetworks { name id } }"}'
```

### 4. Explore the API

Use the [GraphQL Explorer](https://docs.codex.io/explore) to interactively build and test queries. Note that Codex does not support introspection queries directly against the API — use the provided schema files or the explorer instead.

## Recipes & Guides

- [Token Discovery](https://docs.codex.io/recipes/discover-tokens) — Build token discovery pages with trending data, advanced filtering, and search
- [Price Charts](https://docs.codex.io/recipes/charts) — Render token charts with OHLCV data and real-time updates
- [Wallet Analytics](https://docs.codex.io/recipes/wallets) — Analyze wallet performance and discover high-performing traders
- [Token Swap Events](https://docs.codex.io/recipes/events) — Fetch and display token swaps with filtering, sorting, and real-time updates
- [Launchpad Monitoring](https://docs.codex.io/recipes/launchpads) — Build a launchpad dashboard with filtering, sorting, and real-time updates
- [Real-Time Price Tracking](https://docs.codex.io/recipes/realtime) — Build a Node.js app that listens for token price changes in real time

## Additional Resources

- [Codex API Documentation](https://docs.codex.io/)
- [GraphQL API Reference](https://docs.codex.io/api-reference)
- [GraphQL Explorer](https://docs.codex.io/explore)
- [GitHub](https://github.com/Codex-Data)
- [Dashboard](https://dashboard.codex.io/)
- [Discord Community](https://discord.com/invite/mFpUhT3vAq)
