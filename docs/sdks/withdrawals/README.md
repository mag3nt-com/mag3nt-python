# Withdrawals

## Overview

Withdraw unspent funds back to wallet

### Available Operations

* [withdrawals_create](#withdrawals_create) - Withdraw unspent funds back to your wallet
* [withdrawals_list](#withdrawals_list) - List withdrawal history

## withdrawals_create

Initiates a withdrawal of USDC from your treasury balance to an on-chain wallet address. A flat network fee is deducted from the requested amount. The net amount is sent on-chain via CDP; the fee is retained as platform revenue. Withdrawals are processed asynchronously: check status via GET /api/withdrawals.


### Example Usage

<!-- UsageSnippet language="python" operationID="withdrawalsCreate" method="post" path="/api/withdraw" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.withdrawals.withdrawals_create(amount=50, network="eip155:8453", asset="USDC")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                              | Type                                                                                                   | Required                                                                                               | Description                                                                                            | Example                                                                                                |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| `amount`                                                                                               | [operations.WithdrawalsCreateAmountRequest](../../models/operations/withdrawalscreateamountrequest.md) | :heavy_check_mark:                                                                                     | Gross amount to withdraw (fee is deducted from this)                                                   | 50                                                                                                     |
| `network`                                                                                              | *str*                                                                                                  | :heavy_check_mark:                                                                                     | CAIP-2 network to withdraw on                                                                          | eip155:8453                                                                                            |
| `asset`                                                                                                | *str*                                                                                                  | :heavy_check_mark:                                                                                     | N/A                                                                                                    | USDC                                                                                                   |
| `to_address`                                                                                           | *Optional[str]*                                                                                        | :heavy_minus_sign:                                                                                     | Destination wallet address (defaults to authenticated wallet)                                          |                                                                                                        |
| `retries`                                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                       | :heavy_minus_sign:                                                                                     | Configuration to override the default retry behavior of the client.                                    |                                                                                                        |

### Response

**[operations.WithdrawalsCreateResponse](../../models/operations/withdrawalscreateresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.BadRequestError    | 400                              | application/json                 |
| models.errors.ForbiddenError     | 403                              | application/json                 |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## withdrawals_list

Returns up to 50 most recent withdrawals for the authenticated wallet.

### Example Usage

<!-- UsageSnippet language="python" operationID="withdrawalsList" method="get" path="/api/withdrawals" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.withdrawals.withdrawals_list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `id`                                                                                           | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Look up a single withdrawal by ID                                                              |
| `status`                                                                                       | [Optional[operations.WithdrawalsListStatus]](../../models/operations/withdrawalsliststatus.md) | :heavy_minus_sign:                                                                             | Filter by status                                                                               |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |

### Response

**[operations.WithdrawalsListResponse](../../models/operations/withdrawalslistresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |