# Funding

## Overview

Treasury deposits and balances

### Available Operations

* [funding_list_tokens](#funding_list_tokens) - List accepted tokens per network
* [funding_get_balance](#funding_get_balance) - Get treasury balance for authenticated wallet
* [funding_verify](#funding_verify) - Verify an on-chain funding transaction
* [funding_get_wallet_balance](#funding_get_wallet_balance) - Get on-chain token balance for a wallet address

## funding_list_tokens

List accepted tokens per network

### Example Usage

<!-- UsageSnippet language="python" operationID="fundingListTokens" method="get" path="/api/funding/tokens" -->
```python
from mag3nt import Mag3nt


with Mag3nt() as m_client:

    res = m_client.funding.funding_list_tokens()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.FundingListTokensResponse](../../models/operations/fundinglisttokensresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## funding_get_balance

Get treasury balance for authenticated wallet

### Example Usage

<!-- UsageSnippet language="python" operationID="fundingGetBalance" method="get" path="/api/balance" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.funding.funding_get_balance()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.FundingGetBalanceResponse](../../models/operations/fundinggetbalanceresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## funding_verify

Submit an on-chain transaction hash to credit your treasury balance. The platform verifies the transaction on-chain, confirms the Transfer event matches the treasury address, and atomically credits your balance. Idempotent: re-submitting an already-confirmed tx_hash returns the existing balance without double-crediting.


### Example Usage

<!-- UsageSnippet language="python" operationID="fundingVerify" method="post" path="/api/fund/verify" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.funding.funding_verify(tx_hash="<value>", network="eip155:8453", asset="USDC")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `tx_hash`                                                           | *str*                                                               | :heavy_check_mark:                                                  | On-chain transaction hash to verify                                 |
| `network`                                                           | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `asset`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.FundingVerifyResponse](../../models/operations/fundingverifyresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Error              | 400                              | application/json                 |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## funding_get_wallet_balance

Queries the blockchain directly to return the real-time token balance for a given wallet address on a specific network. Supports EVM and Solana.


### Example Usage

<!-- UsageSnippet language="python" operationID="fundingGetWalletBalance" method="get" path="/api/wallet/balance" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.funding.funding_get_wallet_balance(network="eip155:8453", asset="USDC")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `network`                                                           | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | eip155:8453                                                         |
| `asset`                                                             | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | USDC                                                                |
| `address`                                                           | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Wallet address (defaults to authenticated wallet)                   |                                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[operations.FundingGetWalletBalanceResponse](../../models/operations/fundinggetwalletbalanceresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |