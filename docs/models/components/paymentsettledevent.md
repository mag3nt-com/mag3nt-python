# PaymentSettledEvent

Body POSTed to a registered webhook when a pay link settles. Signed via the X-mag3nt-Signature header (t=<unix>,v1=<hex hmac-sha256 of `${t}.${rawBody}`>). Verify with your webhook secret before acting.



## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  | Example                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `id`                                                         | *Optional[str]*                                              | :heavy_minus_sign:                                           | N/A                                                          | evt_9f8e7d...                                                |
| `type`                                                       | [Optional[components.Type]](../../models/components/type.md) | :heavy_minus_sign:                                           | N/A                                                          | payment.settled                                              |
| `created`                                                    | *Optional[int]*                                              | :heavy_minus_sign:                                           | Unix timestamp (seconds)                                     | 1780319099                                                   |
| `data`                                                       | [Optional[components.Data]](../../models/components/data.md) | :heavy_minus_sign:                                           | N/A                                                          |                                                              |