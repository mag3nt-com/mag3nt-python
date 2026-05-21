# Cards

## Overview

Virtual payment card lifecycle

### Available Operations

* [cards_list](#cards_list) - List all cards for the authenticated wallet
* [cards_create](#cards_create) - Issue a new virtual payment card
* [cards_bulk_create](#cards_bulk_create) - Issue multiple cards in a single atomic request
* [cards_freeze](#cards_freeze) - Freeze a card to block all transactions
* [cards_unfreeze](#cards_unfreeze) - Unfreeze a previously frozen card
* [cards_claim](#cards_claim) - Claim a card using its token
* [cards_update_controls](#cards_update_controls) - Update card spending controls
* [cards_list_transactions](#cards_list_transactions) - List transactions for a card

## cards_list

List all cards for the authenticated wallet

### Example Usage

<!-- UsageSnippet language="python" operationID="cardsList" method="get" path="/api/cards" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.CardsListResponse](../../models/operations/cardslistresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Error              | 401                              | application/json                 |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## cards_create

Creates a card backed by your treasury balance. Provide `tx_hash` for UI pay-and-issue flow (card starts as PENDING_FUNDING). Omit `tx_hash` to allocate from pre-funded balance.


### Example Usage

<!-- UsageSnippet language="python" operationID="cardsCreate" method="post" path="/api/issue" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_create(purpose="Research Agent", limit_amount=50, network="eip155:8453", asset="USDC", single_use=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `purpose`                                                           | *str*                                                               | :heavy_check_mark:                                                  | Human-readable label for the card                                   | Research Agent                                                      |
| `limit_amount`                                                      | *float*                                                             | :heavy_check_mark:                                                  | Maximum spend in USDC                                               | 50                                                                  |
| `network`                                                           | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `asset`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `tx_hash`                                                           | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | On-chain funding transaction hash (optional)                        |                                                                     |
| `mcc_locks`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Comma-separated merchant category codes                             |                                                                     |
| `single_use`                                                        | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |                                                                     |
| `expires_in`                                                        | *Optional[float]*                                                   | :heavy_minus_sign:                                                  | Hours until expiry (0 = never)                                      |                                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[operations.CardsCreateResponse](../../models/operations/cardscreateresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Error              | 401                              | application/json                 |
| models.errors.BalanceError       | 403                              | application/json                 |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## cards_bulk_create

Creates up to 1000 cards atomically. All cards are allocated from treasury balance in a single atomic operation. Supports idempotency via header.


### Example Usage

<!-- UsageSnippet language="python" operationID="cardsBulkCreate" method="post" path="/api/issue/bulk" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_bulk_create(cards=[], network="eip155:8453", asset="USDC")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `cards`                                                             | List[[operations.Card](../../models/operations/card.md)]            | :heavy_check_mark:                                                  | N/A                                                                 |
| `idempotency_key`                                                   | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Unique key to prevent duplicate bulk operations                     |
| `network`                                                           | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `asset`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.CardsBulkCreateResponse](../../models/operations/cardsbulkcreateresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.BalanceError       | 403                              | application/json                 |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## cards_freeze

Freeze a card to block all transactions

### Example Usage

<!-- UsageSnippet language="python" operationID="cardsFreeze" method="post" path="/api/cards/{id}/freeze" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_freeze(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.CardsFreezeResponse](../../models/operations/cardsfreezeresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## cards_unfreeze

Unfreeze a previously frozen card

### Example Usage

<!-- UsageSnippet language="python" operationID="cardsUnfreeze" method="post" path="/api/cards/{id}/unfreeze" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_unfreeze(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.CardsUnfreezeResponse](../../models/operations/cardsunfreezeresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## cards_claim

Claim a card using its token

### Example Usage

<!-- UsageSnippet language="python" operationID="cardsClaim" method="post" path="/api/cards/{id}/claim" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_claim(id="<id>", token="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `token`                                                             | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[components.Card](../../models/components/card.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## cards_update_controls

Update card spending controls

### Example Usage

<!-- UsageSnippet language="python" operationID="cardsUpdateControls" method="patch" path="/api/cards/{id}/controls" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_update_controls(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `mcc_locks`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `daily_limit`                                                       | *Optional[float]*                                                   | :heavy_minus_sign:                                                  | N/A                                                                 |
| `max_transaction`                                                   | *Optional[float]*                                                   | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.CardsUpdateControlsResponse](../../models/operations/cardsupdatecontrolsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## cards_list_transactions

List transactions for a card

### Example Usage

<!-- UsageSnippet language="python" operationID="cardsListTransactions" method="get" path="/api/cards/{id}/transactions" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_list_transactions(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.CardsListTransactionsResponse](../../models/operations/cardslisttransactionsresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |