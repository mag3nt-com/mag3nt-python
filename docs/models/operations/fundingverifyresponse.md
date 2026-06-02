# FundingVerifyResponse

Funding verified or pending


## Fields

| Field                                                                                      | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `success`                                                                                  | *Optional[bool]*                                                                           | :heavy_minus_sign:                                                                         | N/A                                                                                        |
| `status`                                                                                   | [Optional[operations.FundingVerifyStatus]](../../models/operations/fundingverifystatus.md) | :heavy_minus_sign:                                                                         | N/A                                                                                        |
| `funded`                                                                                   | [Optional[operations.Funded]](../../models/operations/funded.md)                           | :heavy_minus_sign:                                                                         | Amount credited from this transaction                                                      |
| `balance`                                                                                  | [Optional[components.Balance]](../../models/components/balance.md)                         | :heavy_minus_sign:                                                                         | N/A                                                                                        |