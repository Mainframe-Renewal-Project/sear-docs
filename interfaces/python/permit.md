---
layout: default
has_toc: false
parent: Python
---


# Permits

## Creating permits

### Dataset permits

The sample below gives a permit of READ to the `MATRIX.SECRETS.**` dataset profile for the user `LEONARD`.

```python

from sear import sear

result = sear(
    {
    "operation": "alter",
    "admin_type": "permission",
    "dataset": "MATRIX.SECRETS.**",
    "volume": "MYVOL",
    "generic": True,
    "userid": "LEONARD",
    "traits": {
        "base:access": "READ",
    },
    }
)

print(result.result)
```

### Resource permits

The sample below gives a permit of READ to the `IRR.IRRSMO00.PRECHECK` in the `XFACILIT` class to the user `FDEGILIO`.

```python

from sear import sear

result = sear(
    {
    "operation": "alter",
    "admin_type": "permission",
    "resource": "IRR.IRRSMO00.PRECHECK",
    "class": "XFACILIT",
    "userid": "FDEGILIO",
    "traits": {
        "base:access": "READ",
    },
    }
)

print(result.result)
```

## Deleting permits

The sample below removes `FDEGILIO`'s permit from the access list of `IRR.IRRSMO00.PRECHECK` in the `XFACILIT` class.

```python

from sear import sear

result = sear(
    {
    "operation": "delete",
    "admin_type": "permission",
    "resource": "IRR.IRRSMO00.PRECHECK",
    "class": "XFACILIT",
    "userid": "FDEGILIO",
    }
)

print(result.result)
```
