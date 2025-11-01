---
layout: default
has_toc: false
parent: Python
---

# Racf Remote Sharing Facility (RRSF)

Valid operators for this type of request

<div class="valid-operation-table" markdown="block">

| Operator | Valid |
|----------|-------|
| add      | ❌    |
| alter    | ❌    |
| delete   | ❌    |
| extract  | ✅    |
| search   | ❌    |

</div>

## Extracting information

SEAR provides the `extract` operator to gather information about the RACF database.

### Extracting RACF RRSF options

The sample below returns all of the RRSF options.

```python

from sear import sear

result = sear(
    {
        "operation": "extract",
        "admin_type": "racf-rrsf"
    },
)

print(result.result)
```
