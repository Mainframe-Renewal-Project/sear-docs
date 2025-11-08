---
layout: default
has_toc: false
parent: Examples
---


# Permits

Valid operators for this type of request

<div class="valid-operation-table" markdown="block">

| Operator | Valid |
|----------|-------|
| add      | ❌    |
| alter    | ✅    |
| delete   | ✅    |
| extract  | ❌    |
| search   | ❌    |

</div>

## Creating permits

Unlike with most of the other `admin_types` you can only use `alter` and `delete` to modify permits in the RACF database, `alter` is not just used to alter permits but also create them.

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
    },
)

print(result.result)
```

You can see the full list of traits in [the traits/permission section](https://mainframe-renewal-project.github.io/sear-docs/traits/permission/)

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
    },
)

print(result.result)
```

You can see the full list of traits in [the traits/permission section](https://mainframe-renewal-project.github.io/sear-docs/traits/permission/)

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
    },
)

print(result.result)
```
