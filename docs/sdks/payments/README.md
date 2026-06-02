# Payments

## Overview

Universal outbound protocol payments

### Available Operations

* [payments_execute](#payments_execute) - Execute a universal outbound payment

## payments_execute

Enables any mag3nt card to pay any external x402, MPP, or AP2 endpoint in a single HTTP call. The engine automatically probes the target URL, detects the protocol, and settles on-chain.


### Example Usage

<!-- UsageSnippet language="python" operationID="paymentsExecute" method="post" path="/api/pay" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.payments.payments_execute(card_id="sx_a66a6666-...", card_token="tok_3b9fe670-...", url="https://api.weather.com/forecast", method="POST")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `card_id`                                                           | *str*                                                               | :heavy_check_mark:                                                  | Card identifier (sx_...)                                            |
| `card_token`                                                        | *str*                                                               | :heavy_check_mark:                                                  | Card secret token (tok_...)                                         |
| `url`                                                               | *str*                                                               | :heavy_check_mark:                                                  | The external payment-protected URL to pay                           |
| `method`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | HTTP method to use when probing the URL                             |
| `body`                                                              | [Optional[operations.Body]](../../models/operations/body.md)        | :heavy_minus_sign:                                                  | JSON request body to trigger a priced challenge                     |
| `headers`                                                           | [Optional[operations.Headers]](../../models/operations/headers.md)  | :heavy_minus_sign:                                                  | Optional headers for the probe request                              |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.PaymentsExecuteResponse](../../models/operations/paymentsexecuteresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |