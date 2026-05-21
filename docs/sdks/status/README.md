# Status

## Overview

System health and configuration

### Available Operations

* [status_get](#status_get) - Get platform status, supported protocols, and capabilities
* [status_get_config](#status_get_config) - Get treasury addresses and token registry

## status_get

Get platform status, supported protocols, and capabilities

### Example Usage

<!-- UsageSnippet language="python" operationID="statusGet" method="get" path="/api/status" -->
```python
from mag3nt import Mag3nt


with Mag3nt() as m_client:

    res = m_client.status.status_get()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.StatusGetResponse](../../models/operations/statusgetresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |

## status_get_config

Get treasury addresses and token registry

### Example Usage

<!-- UsageSnippet language="python" operationID="statusGetConfig" method="get" path="/api/config" -->
```python
from mag3nt import Mag3nt


with Mag3nt() as m_client:

    res = m_client.status.status_get_config()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[operations.StatusGetConfigResponse](../../models/operations/statusgetconfigresponse.md)**

### Errors

| Error Type                       | Status Code                      | Content Type                     |
| -------------------------------- | -------------------------------- | -------------------------------- |
| models.errors.Mag3ntDefaultError | 4XX, 5XX                         | \*/\*                            |