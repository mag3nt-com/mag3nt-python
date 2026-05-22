# XMag3ntEnvironment

'sandbox' for testnet networks, 'production' for mainnet

## Example Usage

```python
from mag3nt.models.components import XMag3ntEnvironment

# Open enum: unrecognized values are captured as UnrecognizedStr
value: XMag3ntEnvironment = "sandbox"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"sandbox"`
- `"production"`
