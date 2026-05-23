# X402

## Overview

HTTP 402 payment protocol

### Available Operations

* [x402_pay](#x402_pay) - Pay for a service via x402 protocol
* [x402_discover](#x402_discover) - Discover x402 payment requirements for a URL
* [x402_receive](#x402_receive) - Verify and accept an x402 payment

## x402_pay

Authorizes a payment against a funded card. The card must be ACTIVE with sufficient allocation. Returns payment headers the agent can attach to retry the original 402 request.


### Example Usage

<!-- UsageSnippet language="python" operationID="x402Pay" method="post" path="/api/x402/pay" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.x402.x402_pay(card_id="sx_a66a6666-...", card_token="tok_3b9fe670-...", amount=0.5, merchant="weather-api.com", merchant_address="0xABC...", network="eip155:8453")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        | Example                                                                            |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `card_id`                                                                          | *str*                                                                              | :heavy_check_mark:                                                                 | Card identifier (sx_...)                                                           | sx_a66a6666-1234-5678-9abc-def012345678                                            |
| `card_token`                                                                       | *str*                                                                              | :heavy_check_mark:                                                                 | Card secret token (tok_...)                                                        | tok_3b9fe670-abcd-efgh-ijkl-mnopqrstuvwx                                           |
| `amount`                                                                           | [operations.X402PayAmountRequest](../../models/operations/x402payamountrequest.md) | :heavy_check_mark:                                                                 | Payment amount in USDC                                                             | 0.5                                                                                |
| `merchant`                                                                         | *Optional[str]*                                                                    | :heavy_minus_sign:                                                                 | Merchant identifier                                                                | weather-api.com                                                                    |
| `merchant_address`                                                                 | *Optional[str]*                                                                    | :heavy_minus_sign:                                                                 | Merchant wallet for settlement                                                     | 0xABC...                                                                           |
| `mcc`                                                                              | *Optional[str]*                                                                    | :heavy_minus_sign:                                                                 | Merchant category code                                                             |                                                                                    |
| `resource_url`                                                                     | *Optional[str]*                                                                    | :heavy_minus_sign:                                                                 | URL being paid for                                                                 |                                                                                    |
| `network`                                                                          | *Optional[str]*                                                                    | :heavy_minus_sign:                                                                 | N/A                                                                                |                                                                                    |
| `retries`                                                                          | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                   | :heavy_minus_sign:                                                                 | Configuration to override the default retry behavior of the client.                |                                                                                    |

### Response

**[operations.X402PayResponse](../../models/operations/x402payresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Error              | 400, 401, 403, 404               | application/json                 |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## x402_discover

Discover x402 payment requirements for a URL

### Example Usage

<!-- UsageSnippet language="python" operationID="x402Discover" method="get" path="/api/x402/discover" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.x402.x402_discover(url="https://happy-fireplace.name/")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `url`                                                               | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.X402DiscoverResponse](../../models/operations/x402discoverresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## x402_receive

Verify and accept an x402 payment

### Example Usage

<!-- UsageSnippet language="python" operationID="x402Receive" method="post" path="/api/x402/receive" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.x402.x402_receive()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `payment_header`                                                               | [Optional[operations.PaymentHeader]](../../models/operations/paymentheader.md) | :heavy_minus_sign:                                                             | N/A                                                                            |
| `resource_url`                                                                 | *Optional[str]*                                                                | :heavy_minus_sign:                                                             | N/A                                                                            |
| `retries`                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)               | :heavy_minus_sign:                                                             | Configuration to override the default retry behavior of the client.            |

### Response

**[operations.X402ReceiveResponse](../../models/operations/x402receiveresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |