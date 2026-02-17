!!! note "Content disclaimer"

    Please view the third-party content disclaimer [here](https://github.com/0xPolygon/polygon-docs/blob/main/CONTENT_DISCLAIMER.md).

# Zerion API

Accessing wallet portfolio data, token balances, transaction history, and DeFi positions across multiple chains can be complex when building a dapp. [Zerion API](https://zerion.io/api) provides a single, normalized REST API to query wallet-level data across EVM chains and Solana, returning interpreted, human-readable financial data rather than raw blockchain information.

Zerion API supports all major EVM chains, including:

- Polygon PoS
- Polygon zkEVM

For the full list, see [supported chains](https://developers.zerion.io/reference/supported-blockchains).

## Quick Start

Getting started only takes a few minutes. Follow these three steps:

1. Get an API key
2. Make your first API call
3. Query from your dapp

Here's a step by step walk through:

## 1. Get an API Key

Go to the [Zerion Developer Dashboard](https://dashboard.zerion.io/) and sign up with your work email. Create an organization, and your free API key will be generated instantly. The free Developer plan includes 2,000 requests/day with no credit card required.

## 2. Make Your First API Call

Zerion API uses HTTP Basic authentication. The base URL is `https://api.zerion.io/v1/`.

To get a wallet's token positions on Polygon:

```bash
curl -X GET "https://api.zerion.io/v1/wallets/0xYOUR_ADDRESS/positions?filter[chain_ids]=polygon" \
  -u YOUR_API_KEY:
```

!!! note

    The colon after the API key is required for Basic auth with an empty password.

## 3. Query from Your Dapp

Here's a sample Node.js script to fetch a wallet's Polygon token positions:

```jsx
const axios = require('axios');

const API_KEY = 'YOUR_API_KEY';
const walletAddress = '0xYOUR_ADDRESS';

const config = {
  method: 'get',
  url: `https://api.zerion.io/v1/wallets/${walletAddress}/positions?filter[chain_ids]=polygon`,
  auth: {
    username: API_KEY,
    password: '',
  },
};

axios(config)
  .then((response) => {
    const positions = response.data.data;
    positions.forEach((position) => {
      console.log(
        position.attributes.fungible_info.name,
        position.attributes.quantity.float,
      );
    });
  })
  .catch((error) => {
    console.error(error);
  });
```

### Additional resources:

- To explore all available endpoints including portfolio, transactions, DeFi positions, and NFTs, read the [API reference](https://developers.zerion.io/).
