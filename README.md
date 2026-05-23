# mag3nt

Developer-friendly & type-safe Python SDK specifically catered to leverage *mag3nt* API.

[![Built by Speakeasy](https://img.shields.io/badge/Built_by-SPEAKEASY-374151?style=for-the-badge&labelColor=f3f4f6)](https://www.speakeasy.com/?utm_source=mag3nt&utm_campaign=python)
[![License: MIT](https://img.shields.io/badge/LICENSE_//_MIT-3b5bdb?style=for-the-badge&labelColor=eff6ff)](https://opensource.org/licenses/MIT)


<br /><br />
> [!IMPORTANT]
> This SDK is not yet ready for production use. To complete setup please follow the steps outlined in your [workspace](https://app.speakeasy.com/org/mag3nt/mag3nt-com). Delete this section before > publishing to a package manager.

<!-- Start Summary [summary] -->
## Summary

mag3nt API: Payment infrastructure for AI agents. Issue virtual cards, pay for API access via x402/AP2/MPP protocols, and settle in USDC on Base.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [mag3nt](#mag3nt)
  * [SDK Installation](#sdk-installation)
  * [IDE Support](#ide-support)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
  * [Resource Management](#resource-management)
  * [Debugging](#debugging)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

> [!NOTE]
> **Python version upgrade policy**
>
> Once a Python version reaches its [official end of life date](https://devguide.python.org/versions/), a 3-month grace period is provided for users to upgrade. Following this grace period, the minimum python version supported in the SDK will be updated.

The SDK can be installed with *uv*, *pip*, or *poetry* package managers.

### uv

*uv* is a fast Python package installer and resolver, designed as a drop-in replacement for pip and pip-tools. It's recommended for its speed and modern Python tooling capabilities.

```bash
uv add mag3nt
```

### PIP

*PIP* is the default package installer for Python, enabling easy installation and management of packages from PyPI via the command line.

```bash
pip install mag3nt
```

### Poetry

*Poetry* is a modern tool that simplifies dependency management and package publishing by using a single `pyproject.toml` file to handle project metadata and dependencies.

```bash
poetry add mag3nt
```

### Shell and script usage with `uv`

You can use this SDK in a Python shell with [uv](https://docs.astral.sh/uv/) and the `uvx` command that comes with it like so:

```shell
uvx --from mag3nt python
```

It's also possible to write a standalone Python script without needing to set up a whole project like so:

```python
#!/usr/bin/env -S uv run --script
# /// script
# requires-python = ">=3.10"
# dependencies = [
#     "mag3nt",
# ]
# ///

from mag3nt import Mag3nt

sdk = Mag3nt(
  # SDK arguments
)

# Rest of script here...
```

Once that is saved to a file, you can run it with `uv run script.py` where
`script.py` can be replaced with the actual file name.
<!-- End SDK Installation [installation] -->

<!-- Start IDE Support [idesupport] -->
## IDE Support

### PyCharm

Generally, the SDK will work well with most IDEs out of the box. However, when using PyCharm, you can enjoy much better integration with Pydantic by installing an additional plugin.

- [PyCharm Pydantic Plugin](https://docs.pydantic.dev/latest/integrations/pycharm/)
<!-- End IDE Support [idesupport] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```python
# Synchronous Example
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_list()

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.

```python
# Asynchronous Example
import asyncio
from mag3nt import Mag3nt

async def main():

    async with Mag3nt(
        api_key_auth="<YOUR_API_KEY_HERE>",
    ) as m_client:

        res = await m_client.cards.cards_list_async()

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name           | Type   | Scheme  |
| -------------- | ------ | ------- |
| `api_key_auth` | apiKey | API key |

To authenticate with the API the `api_key_auth` parameter must be set when initializing the SDK client instance. For example:
```python
from mag3nt import Mag3nt


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_list()

    # Handle response
    print(res)

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [Ap2](docs/sdks/ap2/README.md)

* [ap2_get_agent_card](docs/sdks/ap2/README.md#ap2_get_agent_card) - Get the default agent card for AP2 payments
* [ap2_list_payment_methods](docs/sdks/ap2/README.md#ap2_list_payment_methods) - List available payment methods for AP2
* [ap2_create_mandate](docs/sdks/ap2/README.md#ap2_create_mandate) - Create a spending mandate for recurring AP2 payments
* [ap2_execute](docs/sdks/ap2/README.md#ap2_execute) - Execute a payment against an AP2 mandate
* [ap2_list_mandates](docs/sdks/ap2/README.md#ap2_list_mandates) - List mandates for a card

### [Cards](docs/sdks/cards/README.md)

* [cards_list](docs/sdks/cards/README.md#cards_list) - List all cards for the authenticated wallet
* [cards_create](docs/sdks/cards/README.md#cards_create) - Issue a new virtual payment card
* [cards_bulk_create](docs/sdks/cards/README.md#cards_bulk_create) - Issue multiple cards in a single atomic request
* [cards_freeze](docs/sdks/cards/README.md#cards_freeze) - Freeze a card to block all transactions
* [cards_unfreeze](docs/sdks/cards/README.md#cards_unfreeze) - Unfreeze a previously frozen card
* [cards_claim](docs/sdks/cards/README.md#cards_claim) - Claim a card using its token
* [cards_update_controls](docs/sdks/cards/README.md#cards_update_controls) - Update card spending controls
* [cards_list_transactions](docs/sdks/cards/README.md#cards_list_transactions) - List transactions for a card

### [Funding](docs/sdks/funding/README.md)

* [funding_list_tokens](docs/sdks/funding/README.md#funding_list_tokens) - List accepted tokens per network
* [funding_get_balance](docs/sdks/funding/README.md#funding_get_balance) - Get treasury balance for authenticated wallet

### [Keys](docs/sdks/keys/README.md)

* [keys_create](docs/sdks/keys/README.md#keys_create) - Generate a new API key
* [keys_list](docs/sdks/keys/README.md#keys_list) - List all API keys for the authenticated wallet
* [keys_revoke](docs/sdks/keys/README.md#keys_revoke) - Revoke an API key
* [keys_validate](docs/sdks/keys/README.md#keys_validate) - Validate an API key

### [Mpp](docs/sdks/mpp/README.md)

* [mpp_pay](docs/sdks/mpp/README.md#mpp_pay) - Make a micropayment via MPP protocol
* [mpp_create_session](docs/sdks/mpp/README.md#mpp_create_session) - Create an MPP payment session
* [mpp_discover](docs/sdks/mpp/README.md#mpp_discover) - Discover MPP capabilities for a URL
* [mpp_receive](docs/sdks/mpp/README.md#mpp_receive) - Verify and accept an MPP payment
* [mpp_streams_open](docs/sdks/mpp/README.md#mpp_streams_open) - Open a payment stream for continuous micropayments
* [mpp_streams_tick](docs/sdks/mpp/README.md#mpp_streams_tick) - Advance a payment stream by one tick
* [mpp_streams_close](docs/sdks/mpp/README.md#mpp_streams_close) - Close a payment stream
* [mpp_streams_get](docs/sdks/mpp/README.md#mpp_streams_get) - Get payment stream details

### [PayLinks](docs/sdks/paylinks/README.md)

* [pay_links_create](docs/sdks/paylinks/README.md#pay_links_create) - Create a shareable payment link
* [pay_links_list](docs/sdks/paylinks/README.md#pay_links_list) - List pay links for authenticated wallet
* [pay_links_get](docs/sdks/paylinks/README.md#pay_links_get) - Get public pay link details
* [pay_links_cancel](docs/sdks/paylinks/README.md#pay_links_cancel) - Cancel a pay link
* [pay_links_get_status](docs/sdks/paylinks/README.md#pay_links_get_status) - Check pay link payment status
* [pay_links_resolve](docs/sdks/paylinks/README.md#pay_links_resolve) - Resolve a pay link for payment processing
* [pay_links_prepare](docs/sdks/paylinks/README.md#pay_links_prepare) - Prepare payment intent for a pay link
* [pay_links_settle](docs/sdks/paylinks/README.md#pay_links_settle) - Settle a pay link payment

### [Settlement](docs/sdks/settlement/README.md)

* [settlement_get_status](docs/sdks/settlement/README.md#settlement_get_status) - Check settlement status for a transaction

### [Status](docs/sdks/status/README.md)

* [status_get](docs/sdks/status/README.md#status_get) - Get platform status, supported protocols, and capabilities
* [status_get_config](docs/sdks/status/README.md#status_get_config) - Get treasury addresses and token registry

### [X402](docs/sdks/x402/README.md)

* [x402_pay](docs/sdks/x402/README.md#x402_pay) - Pay for a service via x402 protocol
* [x402_discover](docs/sdks/x402/README.md#x402_discover) - Discover x402 payment requirements for a URL
* [x402_receive](docs/sdks/x402/README.md#x402_receive) - Verify and accept an x402 payment

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `RetryConfig` object to the call:
```python
from mag3nt import Mag3nt
from mag3nt.utils import BackoffStrategy, RetryConfig


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_list(,
        RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False))

    # Handle response
    print(res)

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `retry_config` optional parameter when initializing the SDK:
```python
from mag3nt import Mag3nt
from mag3nt.utils import BackoffStrategy, RetryConfig


with Mag3nt(
    retry_config=RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False),
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_list()

    # Handle response
    print(res)

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`Mag3ntError`](./src/mag3nt/models/errors/mag3nterror.py) is the base class for all HTTP error responses. It has the following properties:

| Property           | Type             | Description                                                                             |
| ------------------ | ---------------- | --------------------------------------------------------------------------------------- |
| `err.message`      | `str`            | Error message                                                                           |
| `err.status_code`  | `int`            | HTTP response status code eg `404`                                                      |
| `err.headers`      | `httpx.Headers`  | HTTP response headers                                                                   |
| `err.body`         | `str`            | HTTP body. Can be empty string if no body is returned.                                  |
| `err.raw_response` | `httpx.Response` | Raw HTTP response                                                                       |
| `err.data`         |                  | Optional. Some errors may contain structured data. [See Error Classes](#error-classes). |

### Example
```python
from mag3nt import Mag3nt, models


with Mag3nt(
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:
    res = None
    try:

        res = m_client.cards.cards_list()

        # Handle response
        print(res)


    except models.errors.Mag3ntError as e:
        # The base class for HTTP error responses
        print(e.message)
        print(e.status_code)
        print(e.body)
        print(e.headers)
        print(e.raw_response)

        # Depending on the method different errors may be thrown
        if isinstance(e, models.errors.Error):
            print(e.data.error)  # str
```

### Error Classes
**Primary error:**
* [`Mag3ntError`](./src/mag3nt/models/errors/mag3nterror.py): The base class for HTTP error responses.

<details><summary>Less common errors (8)</summary>

<br />

**Network errors:**
* [`httpx.RequestError`](https://www.python-httpx.org/exceptions/#httpx.RequestError): Base class for request errors.
    * [`httpx.ConnectError`](https://www.python-httpx.org/exceptions/#httpx.ConnectError): HTTP client was unable to make a request to a server.
    * [`httpx.TimeoutException`](https://www.python-httpx.org/exceptions/#httpx.TimeoutException): HTTP request timed out.


**Inherit from [`Mag3ntError`](./src/mag3nt/models/errors/mag3nterror.py)**:
* [`Error`](./src/mag3nt/models/errors/error.py): Applicable to 4 of 41 methods.*
* [`BalanceError`](./src/mag3nt/models/errors/balanceerror.py): Insufficient balance. Status code `403`. Applicable to 2 of 41 methods.*
* [`GoneError`](./src/mag3nt/models/errors/goneerror.py): Pay link has been used. Status code `410`. Applicable to 1 of 41 methods.*
* [`ResponseValidationError`](./src/mag3nt/models/errors/responsevalidationerror.py): Type mismatch between the response data and the expected Pydantic model. Provides access to the Pydantic validation error via the `cause` attribute.

</details>

\* Check [the method documentation](#available-resources-and-operations) to see if the error is applicable.
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Override Server URL Per-Client

The default server can be overridden globally by passing a URL to the `server_url: str` optional parameter when initializing the SDK client instance. For example:
```python
from mag3nt import Mag3nt


with Mag3nt(
    server_url="https://mag3nt.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as m_client:

    res = m_client.cards.cards_list()

    # Handle response
    print(res)

```
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Python SDK makes API calls using the [httpx](https://www.python-httpx.org/) HTTP library.  In order to provide a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration, you can initialize the SDK client with your own HTTP client instance.
Depending on whether you are using the sync or async version of the SDK, you can pass an instance of `HttpClient` or `AsyncHttpClient` respectively, which are Protocol's ensuring that the client has the necessary methods to make API calls.
This allows you to wrap the client with your own custom logic, such as adding custom headers, logging, or error handling, or you can just pass an instance of `httpx.Client` or `httpx.AsyncClient` directly.

For example, you could specify a header for every request that this sdk makes as follows:
```python
from mag3nt import Mag3nt
import httpx

http_client = httpx.Client(headers={"x-custom-header": "someValue"})
s = Mag3nt(client=http_client)
```

or you could wrap the client with your own custom logic:
```python
from mag3nt import Mag3nt
from mag3nt.httpclient import AsyncHttpClient
import httpx

class CustomClient(AsyncHttpClient):
    client: AsyncHttpClient

    def __init__(self, client: AsyncHttpClient):
        self.client = client

    async def send(
        self,
        request: httpx.Request,
        *,
        stream: bool = False,
        auth: Union[
            httpx._types.AuthTypes, httpx._client.UseClientDefault, None
        ] = httpx.USE_CLIENT_DEFAULT,
        follow_redirects: Union[
            bool, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
    ) -> httpx.Response:
        request.headers["Client-Level-Header"] = "added by client"

        return await self.client.send(
            request, stream=stream, auth=auth, follow_redirects=follow_redirects
        )

    def build_request(
        self,
        method: str,
        url: httpx._types.URLTypes,
        *,
        content: Optional[httpx._types.RequestContent] = None,
        data: Optional[httpx._types.RequestData] = None,
        files: Optional[httpx._types.RequestFiles] = None,
        json: Optional[Any] = None,
        params: Optional[httpx._types.QueryParamTypes] = None,
        headers: Optional[httpx._types.HeaderTypes] = None,
        cookies: Optional[httpx._types.CookieTypes] = None,
        timeout: Union[
            httpx._types.TimeoutTypes, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
        extensions: Optional[httpx._types.RequestExtensions] = None,
    ) -> httpx.Request:
        return self.client.build_request(
            method,
            url,
            content=content,
            data=data,
            files=files,
            json=json,
            params=params,
            headers=headers,
            cookies=cookies,
            timeout=timeout,
            extensions=extensions,
        )

s = Mag3nt(async_client=CustomClient(httpx.AsyncClient()))
```
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Resource Management [resource-management] -->
## Resource Management

The `Mag3nt` class implements the context manager protocol and registers a finalizer function to close the underlying sync and async HTTPX clients it uses under the hood. This will close HTTP connections, release memory and free up other resources held by the SDK. In short-lived Python programs and notebooks that make a few SDK method calls, resource management may not be a concern. However, in longer-lived programs, it is beneficial to create a single SDK instance via a [context manager][context-manager] and reuse it across the application.

[context-manager]: https://docs.python.org/3/reference/datamodel.html#context-managers

```python
from mag3nt import Mag3nt
def main():

    with Mag3nt(
        api_key_auth="<YOUR_API_KEY_HERE>",
    ) as m_client:
        # Rest of application here...


# Or when using async:
async def amain():

    async with Mag3nt(
        api_key_auth="<YOUR_API_KEY_HERE>",
    ) as m_client:
        # Rest of application here...
```
<!-- End Resource Management [resource-management] -->

<!-- Start Debugging [debug] -->
## Debugging

You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass your own logger class directly into your SDK.
```python
from mag3nt import Mag3nt
import logging

logging.basicConfig(level=logging.DEBUG)
s = Mag3nt(debug_logger=logging.getLogger("mag3nt"))
```
<!-- End Debugging [debug] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=mag3nt&utm_campaign=python)
