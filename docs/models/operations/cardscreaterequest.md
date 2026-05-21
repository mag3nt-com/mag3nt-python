# CardsCreateRequest


## Fields

| Field                                        | Type                                         | Required                                     | Description                                  | Example                                      |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| `purpose`                                    | *str*                                        | :heavy_check_mark:                           | Human-readable label for the card            | Research Agent                               |
| `limit_amount`                               | *float*                                      | :heavy_check_mark:                           | Maximum spend in USDC                        | 50                                           |
| `network`                                    | *Optional[str]*                              | :heavy_minus_sign:                           | N/A                                          |                                              |
| `asset`                                      | *Optional[str]*                              | :heavy_minus_sign:                           | N/A                                          |                                              |
| `tx_hash`                                    | *Optional[str]*                              | :heavy_minus_sign:                           | On-chain funding transaction hash (optional) |                                              |
| `mcc_locks`                                  | *Optional[str]*                              | :heavy_minus_sign:                           | Comma-separated merchant category codes      |                                              |
| `single_use`                                 | *Optional[bool]*                             | :heavy_minus_sign:                           | N/A                                          |                                              |
| `expires_in`                                 | *Optional[float]*                            | :heavy_minus_sign:                           | Hours until expiry (0 = never)               |                                              |