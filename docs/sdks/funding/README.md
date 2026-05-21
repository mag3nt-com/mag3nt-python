# Funding

## Overview

Treasury deposits and balances

### Available Operations

* [funding_list_tokens](#funding_list_tokens) - List accepted tokens per network
* [funding_get_balance](#funding_get_balance) - Get treasury balance for authenticated wallet

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