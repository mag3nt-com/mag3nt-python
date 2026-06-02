# WebhookSecret

Returned ONLY when a webhook is created. The secret is used to verify the X-mag3nt-Signature header on delivered events and cannot be retrieved again.



## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  | Example                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `id`                                                         | *Optional[str]*                                              | :heavy_minus_sign:                                           | N/A                                                          | wh_3b9fe670abcdef...                                         |
| `url`                                                        | *Optional[str]*                                              | :heavy_minus_sign:                                           | N/A                                                          |                                                              |
| `description`                                                | *Optional[str]*                                              | :heavy_minus_sign:                                           | N/A                                                          |                                                              |
| `status`                                                     | *Optional[str]*                                              | :heavy_minus_sign:                                           | N/A                                                          | ACTIVE                                                       |
| `secret`                                                     | *Optional[str]*                                              | :heavy_minus_sign:                                           | HMAC signing secret (whsec_...). Store securely; shown once. | whsec_1a2b3c4d5e6f...                                        |
| `note`                                                       | *Optional[str]*                                              | :heavy_minus_sign:                                           | N/A                                                          |                                                              |