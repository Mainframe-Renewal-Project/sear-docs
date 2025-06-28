---
layout: default
has_toc: false
parent: Python
---


# Resources

## Extracting information

SEAR provides the `extract` and `search` operators to gather information from the RACF database.

### Extracting a specific resource profile

The sample below extracts information about a specific resource profile.

```python

from sear import sear

result = sear(
        {
        "operation": "extract",
        "admin_type": "resource",
        "resource": "IRR.RADMIN.**",
        "class": "facility",
        },
    )

print(result.result)
```

#### Returned result

<details>

```python
{
  "profile": {
    "base": {
      "base:alter_access_count": 0,
      "base:auditing": "FAILURES(READ)",
      "base:control_access_count": 0,
      "base:create_date": "12/20/23",
      "base:global_auditing": "NONE",
      "base:last_change_date": "12/20/23",
      "base:last_reference_date": "12/20/23",
      "base:level": "0",
      "base:owner": "ESWIFT",
      "base:read_access_count": 0,
      "base:universal_access": "READ",
      "base:update_access_count": 0,
      "base:warn_on_insufficient_access": false
    }
  },
  "return_codes": {
    "racf_reason_code": 0,
    "racf_return_code": 0,
    "saf_return_code": 0,
    "sear_return_code": 0
  }
}
```

</details>

### Searching for resource profiles

The sample below gets all general resource profiles that start with `IRR` in the `facility` class. It will return a list of resource profiles, to get metadata on them you will have to run the extract operation on every single resource profile in the list.

```python

from sear import sear

result = sear(
    {
    "operation": "search",
    "admin_type": "resource",
    "class": "facility",
    "resource_filter": "IRR",
    },
)

print(result.result)
```

## Updating resource profiles

SEAR provides 3 main operators for updating the RACF database, `add`, `alter`, and `delete`.

### Creating a new resource profile

The sample below creates a resource profile called `IRR.RADMIN.**` in the `facility` class with a UACC of NONE and the owner set to the "eswift" RACF userid.

```python

from sear import sear

result = sear(
    {
    "operation": "add",
    "admin_type": "resource",
    "resource": "IRR.RADMIN.**",
    "class": "facility",
    "traits": {
        "base:universal_access": "None",
        "base:owner": "SECADM",
    },
    },
)

print(result.result)
```

### Altering a resource profile

The sample below sets SECADM as the owner of the `IRR.RADMIN.**` resource profile in the `facility` class and sets UACC to "read"

```python

from sear import sear

result = sear(
    {
    "operation": "alter",
    "admin_type": "resource",
    "resource": "IRR.RADMIN.**",
    "class": "facility",
    "traits": {
        "base:universal_access": "Read",
        "base:owner": "SECADM",
    },
    }
)

print(result.result)
```

### Deleting a resource profile

The sample below deletes the `IRR.RADMIN.**` resource profile in the `facility` class.

```python

from sear import sear

result = sear(
    {
    "operation": "delete",
    "admin_type": "resource",
    "resource": "IRR.RADMIN.**",
    "class": "facility",
    },
)

print(result.result)
```
