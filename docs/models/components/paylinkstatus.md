# PayLinkStatus

## Example Usage

```python
from mag3nt.models.components import PayLinkStatus

# Open enum: unrecognized values are captured as UnrecognizedStr
value: PayLinkStatus = "ACTIVE"
```


## Values

This is an open enum. Unrecognized values will not fail type checks.

- `"ACTIVE"`
- `"EXPIRED"`
- `"CANCELLED"`
