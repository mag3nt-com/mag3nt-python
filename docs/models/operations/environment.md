# Environment

'sandbox' for testnet networks (e.g. eip155:84532), 'production' for mainnet. Sandbox transactions deduct balance but are never settled on-chain.

## Example Usage

```python
from mag3nt.models.operations import Environment

# Open enum: unrecognized values are captured as UnrecognizedStr
value: Environment = "sandbox"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"sandbox"`
- `"production"`
