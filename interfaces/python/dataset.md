---
layout: default
has_toc: false
parent: Python
---


# Dataset requests

## Extracting information

SEAR provides the "extract" and "search" operators to gather information from the RACF database.

### Extracting a specific dataset profile

The sample below extracts information about a specific dataset profile.

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

### Searching for dataset profiles

The sample below gets all dataset profiles the start with "LEONARD". It will return a list of dataset profiles, to get metadata on them you will have to run the extract operation on every single dataset profile in the list.

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

SEAR provides 3 main operators for updating the RACF database, "add", "alter", and "delete".

### Creating a new dataset profile

The sample below creates a dataset profile called "ESWIFT.TEST.**" with a UACC of NONE and the owner set to the "eswift" RACF userid.

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
        }
    )

print(result.result)
```

### Altering a dataset profile

The sample below sets SECADM as the owner of the LEONARD.LIB.HLASM dataset profile and sets UACC to "read"

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
        }
    )

print(result.result)
```

### Deleting a dataset profile

The sample below deletes the "LEONARD.LIB.HLASM" dataset profile

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
