<!-- Start SDK Example Usage [usage] -->
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