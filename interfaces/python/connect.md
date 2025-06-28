---
layout: default
has_toc: false
parent: Python
---


# Connects

## Updating connects

### Creating a new connect

The sample below connects the RACF user `LEONARD` to the `DEVOPS` group with the group special attribute.

```python

from sear import sear

result = sear(
    {
        "operation": "alter",
        "admin_type": "group-connection",
        "userid": "LEONARD",
        "group": "DEVOPS",
        "traits": {
            "base:special": True,
        },
    },
)

print(result.result)
```

### Deleting a connect

The sample below removes `LEONARD`'s connect to the RACF `DEVOPS` group.

```python

from sear import sear

result = sear(
    {
        "operation": "delete",
        "admin_type": "group-connection",
        "userid": "eswift",
        "group": "TESTGRP0"
    }
)

print(result.result)
```
