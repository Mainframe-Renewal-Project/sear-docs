---
layout: default
has_toc: false
parent: Python
---


# RACF system options

## Extracting information

SEAR provides the "extract" and "search" operators to gather information from the RACF database.

### Extracting RACF system options

The sample below returns all of the RACF system options.

```python

from sear import sear

result = sear(
    {
    "operation": "extract",
    "admin_type": "racf-options"
    }
)

print(result.result)
```

## Updating the RACF system options

You can update the RACF system options through SEAR, the only valid operator is "alter" in this case.

### Altering the RACF system options

The sample below updates the amount of incorrect password attempts allowed on the system to 5.

```python

from sear import sear

result = sear(
    {
    "operation": "alter",
    "admin_type": "racf-options",
    "traits": {
        "base:max_incorrect_password_attempts": 5,
    },
    }
)

print(result.result)
```
