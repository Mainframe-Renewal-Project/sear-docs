---
layout: default
has_toc: false
parent: Python
---


# Datasets

Valid operators for this type of request

| Operator | Valid |
|----------|-------|
| add      | ✅    |
| alter    | ✅    |
| delete   | ✅    |
| extract  | ✅    |
| search   | ✅    |

## Extracting information

SEAR provides the `extract` and `search` operators to gather information about dataset profiles.

### Extracting a specific dataset profile

The sample below extracts information about a dataset profile called `FDEGILIO.TEST.*`.

```python

from sear import sear

result = sear(
    {
        "operation": "extract",
        "admin_type": "dataset",
        "dataset": "FDEGILIO.TEST.*",
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
      "base:create_date": "03/19/24",
      "base:creation_group_name": "SYS1",
      "base:dataset_type": "NON-VSAM",
      "base:erase_datasets_on_delete": false,
      "base:global_auditing": "NONE",
      "base:high_level_qualifier_is_group": false,
      "base:last_change_date": "03/19/24",
      "base:last_reference_date": "03/19/24",
      "base:level": 0,
      "base:owner": "LEONARD",
      "base:read_access_count": 0,
      "base:universal_access": "NONE",
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

### Searching for dataset profiles

The sample below gets all dataset profiles that start with `LEONARD`. It will return a list of dataset profiles, to get metadata on them you will have to run the extract operation on every single dataset profile in the list.

```python

from sear import sear

result = sear(
    {
        "operation": "search",
        "admin_type": "dataset",
        "dataset_filter": "LEONARD",
    },
 )

print(result.result)
```

## Updating dataset profiles

SEAR provides 3 main operators for updating the RACF database, `add`, `alter`, and `delete`.

### Creating a new dataset profile

The sample below creates a dataset profile called `ESWIFT.TEST.**` with a UACC of NONE and the owner set to the `eswift` RACF userid.

```python

from sear import sear

result = sear(
    {
        "operation": "add",
        "admin_type": "dataset",
        "dataset": "ESWIFT.TEST.**",
        "generic": True,
        "traits": {
            "base:universal_access": "None",
            "base:owner": "eswift",
        },
    },
)

print(result.result)
```

You can see the full list of traits in [the traits/dataset section](https://mainframe-renewal-project.github.io/sear-docs/traits/dataset/)

### Altering a dataset profile

The sample below sets the RACF user `SECADM` as the owner of the `LEONARD.LIB.HLASM` dataset profile and sets UACC to `READ`.

```python

from sear import sear

result = sear(
    {
        "operation": "alter",
        "admin_type": "dataset",
        "dataset": "LEONARD.LIB.HLASM",
        "traits": {
            "base:universal_access": "Read",
            "base:owner": "SECADM",
        },
    },
)

print(result.result)
```

You can see the full list of traits in [the traits/dataset section](https://mainframe-renewal-project.github.io/sear-docs/traits/dataset/)

### Deleting a dataset profile

The sample below deletes the `LEONARD.LIB.HLASM` dataset profile.

```python

from sear import sear

result = sear(
    {
        "operation": "delete",
        "admin_type": "dataset",
        "dataset": "LEONARD.LIB.HLASM",
    },
)

print(result.result)
```
