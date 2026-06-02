# Webhooks

## Overview

Signed payment.settled notifications for sellers

### Available Operations

* [webhooks_create](#webhooks_create) - Register a webhook endpoint
* [webhooks_list](#webhooks_list) - List registered webhooks
* [webhooks_delete](#webhooks_delete) - Delete a webhook endpoint

## webhooks_create

Register an HTTPS endpoint to receive signed `payment.settled` events when your pay links settle. The signing secret is returned ONCE in this response and cannot be retrieved again. Use it to verify the X-mag3nt-Signature header on each delivery. Max 5 active webhooks per wallet. URLs must be https and may not target private/loopback hosts.


### Example Usage

<!-- UsageSnippet language="python" operationID="webhooksCreate" method="post" path="/api/webhooks" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.webhooks.webhooks_create(url="https://api.acme.com/hooks/mag3nt")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `url`                                                               | *str*                                                               | :heavy_check_mark:                                                  | HTTPS endpoint that will receive events                             | https://api.acme.com/hooks/mag3nt                                   |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Optional label for this webhook                                     |                                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[components.WebhookSecret](../../models/components/webhooksecret.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Error              | 400, 401                         | application/json                 |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## webhooks_list

Returns all webhooks for the authenticated wallet. Secrets are never returned.

### Example Usage

<!-- UsageSnippet language="python" operationID="webhooksList" method="get" path="/api/webhooks" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.webhooks.webhooks_list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.WebhooksListResponse](../../models/operations/webhookslistresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Error              | 401                              | application/json                 |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## webhooks_delete

Delete a webhook endpoint

### Example Usage

<!-- UsageSnippet language="python" operationID="webhooksDelete" method="delete" path="/api/webhooks/{id}" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.webhooks.webhooks_delete(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.WebhooksDeleteResponse](../../models/operations/webhooksdeleteresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Error              | 403, 404                         | application/json                 |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |