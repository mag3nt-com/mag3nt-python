# CardStatus

## Example Usage

```python
from mag3nt.models.components import CardStatus

# Open enum: unrecognized values are captured as UnrecognizedStr
value: CardStatus = "ACTIVE"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"ACTIVE"`
- `"FROZEN"`
- `"EXPIRED"`
- `"USED"`
- `"PENDING_FUNDING"`
- `"FUNDING_FAILED"`
