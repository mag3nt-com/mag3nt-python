# WithdrawalStatus

## Example Usage

```python
from mag3nt.models.components import WithdrawalStatus

# Open enum: unrecognized values are captured as UnrecognizedStr
value: WithdrawalStatus = "PROCESSING"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"PROCESSING"`
- `"COMPLETED"`
- `"FAILED"`
