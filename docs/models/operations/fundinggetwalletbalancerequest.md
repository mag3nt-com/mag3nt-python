# FundingGetWalletBalanceRequest


## Fields

| Field                                             | Type                                              | Required                                          | Description                                       | Example                                           |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `network`                                         | *str*                                             | :heavy_check_mark:                                | N/A                                               | eip155:8453                                       |
| `asset`                                           | *str*                                             | :heavy_check_mark:                                | N/A                                               | USDC                                              |
| `address`                                         | *Optional[str]*                                   | :heavy_minus_sign:                                | Wallet address (defaults to authenticated wallet) |                                                   |