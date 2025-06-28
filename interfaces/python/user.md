---
layout: default
has_toc: false
parent: Python
---


# Users

## Extracting information

SEAR provides the "extract" and "search" operators to gather information from the RACF database.

### Extracting a specific RACF user

Below you can find a sample of some code that extracts information about a specific RACF user.

```python

from sear import sear

result = sear(
    {
    "operation": "extract",
    "admin_type": "user",
    "userid": "FDEGILIO",
    },
)

print(result.result)
```

### Searching for RACF users

The sample below gets all users that start with "ZWE". It will return a list of users, to get metadata on them you will have to run the extract operation on every single RACF user in the list.

```python

from sear import sear

result = sear(
    {
    "operation": "search",
    "admin_type": "user",
    "userid_filter": "ZWE",
    },
)

print(result.result)
```

## Updating RACF users

SEAR provides 3 main operators for updating the RACF database, "add", "alter", and "delete".

### Creating a new RACF user

The sample below creates a user called "ESWIFT" with the base name of "ELIJAH SWIFT", a UID of 24, and the home directory set to "/home/ESWIFT".

```python

from sear import sear

result = sear(
    {
    "operation": "add",
    "admin_type": "user",
    "userid": "ESWIFT",
    "traits": {
        "base:name": "ELIJAH SWIFT",
        "omvs:uid": 24,
        "omvs:home_directory": "/home/ESWIFT",
    },
    }
)

print(result.result)
```

### Altering a RACF user

The sample below gives special and read only auditor to the RACF user "LEONARD".

```python

from sear import sear

result = sear(
    {
    "operation": "alter",
    "admin_type": "user",
    "userid": "LEONARD",
    "traits": {
        "base:name": "LEONARD CARCARAMO",
        "base:special": True,
        "base:read_only_auditor": True,
    },
    }
)

print(result.result)
```

### Deleting a RACF user

The below sample deletes the RACF user "LEONARD".

```python

from sear import sear

result = sear(
    {
    "operation": "delete",
    "admin_type": "user",
    "userid": "LEONARD",
    },
)

print(result.result)
```
