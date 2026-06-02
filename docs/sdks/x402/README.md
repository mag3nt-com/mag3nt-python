# X402

## Overview

HTTP 402 payment protocol

### Available Operations

* [~~x402_pay~~](#x402_pay) - (Removed) Pay for a service via x402 protocol :warning: **Deprecated**
* [x402_discover](#x402_discover) - Discover x402 payment requirements for a URL
* [x402_receive](#x402_receive) - Verify and accept an x402 payment

## ~~x402_pay~~

This proprietary push endpoint has been removed. Use POST /api/pay with { card_id, card_token, url } instead. It automatically detects x402 and settles on-chain.


> :warning: **DEPRECATED**: This will be removed in a future release, please migrate away from it as soon as possible.

### Example Usage

<!-- UsageSnippet language="python" operationID="x402Pay" method="post" path="/api/x402/pay" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    m_client.x402.x402_pay()

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.X402PayGoneError   | 410                              | application/json                 |
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