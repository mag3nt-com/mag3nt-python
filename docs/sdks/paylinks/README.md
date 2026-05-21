# PayLinks

## Overview

Shareable payment URLs

### Available Operations

* [pay_links_create](#pay_links_create) - Create a shareable payment link
* [pay_links_list](#pay_links_list) - List pay links for authenticated wallet
* [pay_links_get](#pay_links_get) - Get public pay link details
* [pay_links_cancel](#pay_links_cancel) - Cancel a pay link
* [pay_links_get_status](#pay_links_get_status) - Check pay link payment status
* [pay_links_resolve](#pay_links_resolve) - Resolve a pay link for payment processing
* [pay_links_prepare](#pay_links_prepare) - Prepare payment intent for a pay link
* [pay_links_settle](#pay_links_settle) - Settle a pay link payment

## pay_links_create

Create a shareable payment link

### Example Usage

<!-- UsageSnippet language="python" operationID="payLinksCreate" method="post" path="/api/paylinks" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.pay_links.pay_links_create(card_id="<id>", type_="SINGLE", max_uses=1)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                | Type                                                                                     | Required                                                                                 | Description                                                                              |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `card_id`                                                                                | *str*                                                                                    | :heavy_check_mark:                                                                       | N/A                                                                                      |
| `amount`                                                                                 | *OptionalNullable[float]*                                                                | :heavy_minus_sign:                                                                       | Fixed amount (null for open-amount)                                                      |
| `memo`                                                                                   | *Optional[str]*                                                                          | :heavy_minus_sign:                                                                       | N/A                                                                                      |
| `type`                                                                                   | [Optional[operations.PayLinksCreateType]](../../models/operations/paylinkscreatetype.md) | :heavy_minus_sign:                                                                       | SINGLE for one-time, RECURRING for multi-use                                             |
| `max_uses`                                                                               | *Optional[int]*                                                                          | :heavy_minus_sign:                                                                       | N/A                                                                                      |
| `expires_in`                                                                             | *Optional[float]*                                                                        | :heavy_minus_sign:                                                                       | Hours until expiry                                                                       |
| `retries`                                                                                | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                         | :heavy_minus_sign:                                                                       | Configuration to override the default retry behavior of the client.                      |

### Response

**[operations.PayLinksCreateResponse](../../models/operations/paylinkscreateresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## pay_links_list

List pay links for authenticated wallet

### Example Usage

<!-- UsageSnippet language="python" operationID="payLinksList" method="get" path="/api/paylinks" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.pay_links.pay_links_list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.PayLinksListResponse](../../models/operations/paylinkslistresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## pay_links_get

Get public pay link details

### Example Usage

<!-- UsageSnippet language="python" operationID="payLinksGet" method="get" path="/api/paylinks/{code}" -->
```python
from mag3nt import Mag3nt


with Mag3nt() as m_client:

    res = m_client.pay_links.pay_links_get(code="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `code`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[components.PayLink](../../models/components/paylink.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## pay_links_cancel

Cancel a pay link

### Example Usage

<!-- UsageSnippet language="python" operationID="payLinksCancel" method="delete" path="/api/paylinks/{code}" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.pay_links.pay_links_cancel(code="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `code`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.PayLinksCancelResponse](../../models/operations/paylinkscancelresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## pay_links_get_status

Check pay link payment status

### Example Usage

<!-- UsageSnippet language="python" operationID="payLinksGetStatus" method="get" path="/api/paylinks/{code}/status" -->
```python
from mag3nt import Mag3nt


with Mag3nt() as m_client:

    res = m_client.pay_links.pay_links_get_status(code="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `code`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.PayLinksGetStatusResponse](../../models/operations/paylinksgetstatusresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## pay_links_resolve

Resolve a pay link for payment processing

### Example Usage

<!-- UsageSnippet language="python" operationID="payLinksResolve" method="get" path="/api/pay/{code}/resolve" -->
```python
from mag3nt import Mag3nt


with Mag3nt() as m_client:

    res = m_client.pay_links.pay_links_resolve(code="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `code`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.PayLinksResolveResponse](../../models/operations/paylinksresolveresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## pay_links_prepare

Prepare payment intent for a pay link

### Example Usage

<!-- UsageSnippet language="python" operationID="payLinksPrepare" method="get" path="/api/pay/{code}/prepare" -->
```python
from mag3nt import Mag3nt


with Mag3nt() as m_client:

    res = m_client.pay_links.pay_links_prepare(code="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `code`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.PayLinksPrepareResponse](../../models/operations/paylinksprepareresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## pay_links_settle

Settle a pay link payment

### Example Usage

<!-- UsageSnippet language="python" operationID="payLinksSettle" method="post" path="/api/pay/{code}/settle" -->
```python
from mag3nt import Mag3nt


with Mag3nt() as m_client:

    res = m_client.pay_links.pay_links_settle(code="<value>", body={})

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                    | Type                                                                                         | Required                                                                                     | Description                                                                                  |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `code`                                                                                       | *str*                                                                                        | :heavy_check_mark:                                                                           | N/A                                                                                          |
| `body`                                                                                       | [operations.PayLinksSettleRequestBody](../../models/operations/paylinkssettlerequestbody.md) | :heavy_check_mark:                                                                           | N/A                                                                                          |
| `retries`                                                                                    | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                             | :heavy_minus_sign:                                                                           | Configuration to override the default retry behavior of the client.                          |

### Response

**[operations.PayLinksSettleResponse](../../models/operations/paylinkssettleresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |