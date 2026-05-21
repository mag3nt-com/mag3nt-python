# BalanceError


## Fields

| Field                | Type                 | Required             | Description          | Example              |
| -------------------- | -------------------- | -------------------- | -------------------- | -------------------- |
| `error`              | *str*                | :heavy_check_mark:   | N/A                  | Insufficient balance |
| `available`          | *float*              | :heavy_check_mark:   | N/A                  | 40                   |
| `requested`          | *float*              | :heavy_check_mark:   | N/A                  | 50                   |
| `network`            | *Optional[str]*      | :heavy_minus_sign:   | N/A                  | eip155:8453          |
| `asset`              | *Optional[str]*      | :heavy_minus_sign:   | N/A                  | USDC                 |