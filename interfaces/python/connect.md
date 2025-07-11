---
layout: default
has_toc: false
parent: Python
---


# Connects

Valid operators for this type of request

<div class="valid-operation-table" markdown="block">

| Operator | Valid |
|----------|-------|
| add      | ❌    |
| alter    | ✅    |
| delete   | ✅    |
| extract  | ✅    |
| search   | ❌    |

</div>

## Updating connects

Unlike with most of the other `admin_types` you can only use `alter` and `delete` to modify connections in the RACF database, `alter` is not just used to alter connects but also create them.

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

You can see the full list of traits in [the traits/group_connection section](https://mainframe-renewal-project.github.io/sear-docs/traits/group_connection/)

### Deleting a connect

The sample below removes `LEONARD`'s connect from the RACF `DEVOPS` group.

```python

from sear import sear

result = sear(
    {
        "operation": "delete",
        "admin_type": "group-connection",
        "userid": "LEONARD",
        "group": "DEVOPS",
    },
)

print(result.result)
```
