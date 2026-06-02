# Ap2

## Overview

Agent-to-Agent Payment Protocol

### Available Operations

* [ap2_get_agent_card](#ap2_get_agent_card) - Get the default agent card for AP2 payments
* [ap2_list_payment_methods](#ap2_list_payment_methods) - List available payment methods for AP2
* [ap2_create_mandate](#ap2_create_mandate) - Create a spending mandate for recurring AP2 payments
* [ap2_execute](#ap2_execute) - Execute a payment against an AP2 mandate
* [ap2_list_mandates](#ap2_list_mandates) - List mandates for a card
* [ap2_settle](#ap2_settle) - Settle a pay link with a closed AP2 Payment Mandate

## ap2_get_agent_card

Get the default agent card for AP2 payments

### Example Usage

<!-- UsageSnippet language="python" operationID="ap2GetAgentCard" method="get" path="/api/ap2/agent-card" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.ap2.ap2_get_agent_card()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.Ap2GetAgentCardResponse](../../models/operations/ap2getagentcardresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## ap2_list_payment_methods

List available payment methods for AP2

### Example Usage

<!-- UsageSnippet language="python" operationID="ap2ListPaymentMethods" method="post" path="/api/ap2/payment-methods" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.ap2.ap2_list_payment_methods()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.Ap2ListPaymentMethodsResponse](../../models/operations/ap2listpaymentmethodsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## ap2_create_mandate

Create a spending mandate for recurring AP2 payments

### Example Usage

<!-- UsageSnippet language="python" operationID="ap2CreateMandate" method="post" path="/api/ap2/mandate" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.ap2.ap2_create_mandate(card_id="<id>", card_token="<value>", amount=1529.88, merchant="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                              | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `card_id`                                                                              | *str*                                                                                  | :heavy_check_mark:                                                                     | N/A                                                                                    |
| `card_token`                                                                           | *str*                                                                                  | :heavy_check_mark:                                                                     | N/A                                                                                    |
| `amount`                                                                               | [operations.Ap2CreateMandateAmount](../../models/operations/ap2createmandateamount.md) | :heavy_check_mark:                                                                     | N/A                                                                                    |
| `merchant`                                                                             | *str*                                                                                  | :heavy_check_mark:                                                                     | N/A                                                                                    |
| `max_amount`                                                                           | [Optional[operations.MaxAmount]](../../models/operations/maxamount.md)                 | :heavy_minus_sign:                                                                     | N/A                                                                                    |
| `expires_at`                                                                           | [date](https://docs.python.org/3/library/datetime.html#date-objects)                   | :heavy_minus_sign:                                                                     | N/A                                                                                    |
| `retries`                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                       | :heavy_minus_sign:                                                                     | Configuration to override the default retry behavior of the client.                    |

### Response

**[operations.Ap2CreateMandateResponse](../../models/operations/ap2createmandateresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## ap2_execute

Execute a payment against an AP2 mandate

### Example Usage

<!-- UsageSnippet language="python" operationID="ap2Execute" method="post" path="/api/ap2/execute" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.ap2.ap2_execute(card_id="<id>", card_token="<value>", amount="802.33")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `card_id`                                                                  | *str*                                                                      | :heavy_check_mark:                                                         | N/A                                                                        |
| `card_token`                                                               | *str*                                                                      | :heavy_check_mark:                                                         | N/A                                                                        |
| `amount`                                                                   | [operations.Ap2ExecuteAmount](../../models/operations/ap2executeamount.md) | :heavy_check_mark:                                                         | N/A                                                                        |
| `mandate_id`                                                               | *Optional[str]*                                                            | :heavy_minus_sign:                                                         | N/A                                                                        |
| `retries`                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)           | :heavy_minus_sign:                                                         | Configuration to override the default retry behavior of the client.        |

### Response

**[operations.Ap2ExecuteResponse](../../models/operations/ap2executeresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## ap2_list_mandates

List mandates for a card

### Example Usage

<!-- UsageSnippet language="python" operationID="ap2ListMandates" method="get" path="/api/ap2/mandates/{card_id}" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.ap2.ap2_list_mandates(card_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `card_id`                                                           | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.Ap2ListMandatesResponse](../../models/operations/ap2listmandatesresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## ap2_settle

Settles a mag3nt pay link by consuming a closed AP2 Payment Mandate (`mandate.payment.1`). The mandate is verified for signature, expiry, and payee scoping against the link; if an open mandate is supplied, the open→closed chain is re-verified. The payer card named by the mandate is authenticated via its card token, then the payer card is debited and the link credited atomically. Idempotent on the mandate `jti` (replay-safe).


### Example Usage

<!-- UsageSnippet language="python" operationID="ap2Settle" method="post" path="/api/ap2/settle" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.ap2.ap2_settle(pay_link_code="pl_a1b2c3d4", closed_mandate="<value>", card_token="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   | Example                                                                       |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `pay_link_code`                                                               | *str*                                                                         | :heavy_check_mark:                                                            | Code of the pay link being settled.                                           | pl_a1b2c3d4                                                                   |
| `closed_mandate`                                                              | *str*                                                                         | :heavy_check_mark:                                                            | Closed AP2 Payment Mandate (mandate.payment.1) as an SD-JWT.                  |                                                                               |
| `card_token`                                                                  | *str*                                                                         | :heavy_check_mark:                                                            | Token of the payer card named by the mandate (authorizes the debit).          |                                                                               |
| `open_mandate`                                                                | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | Optional open AP2 mandate; when present the open→closed chain is re-verified. |                                                                               |
| `retries`                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)              | :heavy_minus_sign:                                                            | Configuration to override the default retry behavior of the client.           |                                                                               |

### Response

**[operations.Ap2SettleResponse](../../models/operations/ap2settleresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Error              | 400, 401, 404, 422               | application/json                 |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |