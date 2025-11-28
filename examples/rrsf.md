---
layout: default
has_toc: false
parent: Examples
---

{: .warning }

> Please note RRSF support is exclusive to SEAR 0.4.0 and later, earlier versions do not support it.

# RRSF

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
