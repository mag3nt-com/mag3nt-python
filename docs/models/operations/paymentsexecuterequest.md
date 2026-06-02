# PaymentsExecuteRequest


## Fields

| Field                                                              | Type                                                               | Required                                                           | Description                                                        |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `card_id`                                                          | *str*                                                              | :heavy_check_mark:                                                 | Card identifier (sx_...)                                           |
| `card_token`                                                       | *str*                                                              | :heavy_check_mark:                                                 | Card secret token (tok_...)                                        |
| `url`                                                              | *str*                                                              | :heavy_check_mark:                                                 | The external payment-protected URL to pay                          |
| `method`                                                           | *Optional[str]*                                                    | :heavy_minus_sign:                                                 | HTTP method to use when probing the URL                            |
| `body`                                                             | [Optional[operations.Body]](../../models/operations/body.md)       | :heavy_minus_sign:                                                 | JSON request body to trigger a priced challenge                    |
| `headers`                                                          | [Optional[operations.Headers]](../../models/operations/headers.md) | :heavy_minus_sign:                                                 | Optional headers for the probe request                             |