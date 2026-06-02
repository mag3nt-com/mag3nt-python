# Mpp

## Overview

Micropayment Protocol with streaming

### Available Operations

* [~~mpp_pay~~](#mpp_pay) - (Removed) Make a micropayment via MPP protocol :warning: **Deprecated**
* [mpp_create_session](#mpp_create_session) - Create an MPP payment session
* [mpp_discover](#mpp_discover) - Discover MPP capabilities for a URL
* [mpp_receive](#mpp_receive) - Verify and accept an MPP payment
* [mpp_streams_open](#mpp_streams_open) - Open a payment stream for continuous micropayments
* [mpp_streams_tick](#mpp_streams_tick) - Advance a payment stream by one tick
* [mpp_streams_close](#mpp_streams_close) - Close a payment stream
* [mpp_streams_get](#mpp_streams_get) - Get payment stream details

## ~~mpp_pay~~

This proprietary push endpoint has been removed. Use POST /api/pay with { card_id, card_token, url } instead. It automatically decodes the MPP challenge and settles on-chain.


> :warning: **DEPRECATED**: This will be removed in a future release, please migrate away from it as soon as possible.

### Example Usage

<!-- UsageSnippet language="python" operationID="mppPay" method="post" path="/api/mpp/pay" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    m_client.mpp.mpp_pay()

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.MppPayGoneError    | 410                              | application/json                 |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## mpp_create_session

Create an MPP payment session

### Example Usage

<!-- UsageSnippet language="python" operationID="mppCreateSession" method="post" path="/api/mpp/session" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.mpp.mpp_create_session(card_id="<id>", card_token="<value>", merchant="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `card_id`                                                           | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `card_token`                                                        | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `merchant`                                                          | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.MppCreateSessionResponse](../../models/operations/mppcreatesessionresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## mpp_discover

Discover MPP capabilities for a URL

### Example Usage

<!-- UsageSnippet language="python" operationID="mppDiscover" method="get" path="/api/mpp/discover" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.mpp.mpp_discover(url="https://dutiful-gallery.name/")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `url`                                                               | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.MppDiscoverResponse](../../models/operations/mppdiscoverresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## mpp_receive

Verify and accept an MPP payment

### Example Usage

<!-- UsageSnippet language="python" operationID="mppReceive" method="post" path="/api/mpp/receive" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.mpp.mpp_receive()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `payment_data`                                                             | [Optional[operations.PaymentData]](../../models/operations/paymentdata.md) | :heavy_minus_sign:                                                         | N/A                                                                        |
| `retries`                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)           | :heavy_minus_sign:                                                         | Configuration to override the default retry behavior of the client.        |

### Response

**[operations.MppReceiveResponse](../../models/operations/mppreceiveresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## mpp_streams_open

Open a payment stream for continuous micropayments

### Example Usage

<!-- UsageSnippet language="python" operationID="mppStreamsOpen" method="post" path="/api/mpp/stream/open" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.mpp.mpp_streams_open(card_id="<id>", card_token="<value>", budget="<value>", tick_amount=1246.22)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                    | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `card_id`                                                                    | *str*                                                                        | :heavy_check_mark:                                                           | N/A                                                                          |
| `card_token`                                                                 | *str*                                                                        | :heavy_check_mark:                                                           | N/A                                                                          |
| `budget`                                                                     | [operations.BudgetRequest](../../models/operations/budgetrequest.md)         | :heavy_check_mark:                                                           | Total budget for the stream in USDC                                          |
| `tick_amount`                                                                | [operations.TickAmountRequest](../../models/operations/tickamountrequest.md) | :heavy_check_mark:                                                           | Amount per tick                                                              |
| `receiver_card_id`                                                           | *Optional[str]*                                                              | :heavy_minus_sign:                                                           | N/A                                                                          |
| `retries`                                                                    | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)             | :heavy_minus_sign:                                                           | Configuration to override the default retry behavior of the client.          |

### Response

**[operations.MppStreamsOpenResponse](../../models/operations/mppstreamsopenresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## mpp_streams_tick

Advance a payment stream by one tick

### Example Usage

<!-- UsageSnippet language="python" operationID="mppStreamsTick" method="post" path="/api/mpp/stream/tick" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.mpp.mpp_streams_tick(stream_id="<id>", card_id="<id>", card_token="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `stream_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `card_id`                                                           | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `card_token`                                                        | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.MppStreamsTickResponse](../../models/operations/mppstreamstickresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## mpp_streams_close

Close a payment stream

### Example Usage

<!-- UsageSnippet language="python" operationID="mppStreamsClose" method="post" path="/api/mpp/stream/close" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.mpp.mpp_streams_close(stream_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `stream_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.MppStreamsCloseResponse](../../models/operations/mppstreamscloseresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## mpp_streams_get

Get payment stream details

### Example Usage

<!-- UsageSnippet language="python" operationID="mppStreamsGet" method="get" path="/api/mpp/stream/{id}" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.mpp.mpp_streams_get(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.MppStreamsGetResponse](../../models/operations/mppstreamsgetresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |