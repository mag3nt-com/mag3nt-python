# Settlement

## Overview

On-chain settlement status

### Available Operations

* [settlement_get_status](#settlement_get_status) - Check settlement status for a transaction

## settlement_get_status

Check settlement status for a transaction

### Example Usage

<!-- UsageSnippet language="python" operationID="settlementGetStatus" method="get" path="/api/settlement/status/{txn_id}" -->
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.settlement.settlement_get_status(txn_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `txn_id`                                                            | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.SettlementGetStatusResponse](../../models/operations/settlementgetstatusresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |