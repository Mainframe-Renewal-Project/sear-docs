---
layout: default
has_toc: false
parent: Python
---


# Groups

## Extracting information

SEAR provides the `extract` and `search` operators to gather information from the RACF database.

### Extracting a specific RACF group

Below you can find a sample of some code that extracts information about the RACF group "DEV".

```python

from sear import sear

result = sear(
        {
        "operation": "extract",
        "admin_type": "group",
        "group": "DEV",
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
      "base:connected_users": [
        {
          "base:connected_user_authority": "USE",
          "base:connected_userid": "ESWIFT"
        }
      ],
      "base:create_date": "10/11/23",
      "base:owner": "ESWIFT",
      "base:superior_group": "SYS1",
      "base:terminal_universal_access": true,
      "base:universal": false
    },
    "omvs": {
      "omvs:gid": 24
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

### Searching for RACF group

The sample below gets all groups that start with "SYS". It will return a list of groups, to get metadata on them you will have to run the extract operation on every single RACF group in the list.

```python

from sear import sear

result = sear(
        {
        "operation": "search",
        "admin_type": "group",
        "group_filter": "SYS",
        },
    )

print(result.result)
```

## Updating RACF groups

SEAR provides 3 main operators for updating the RACF database, `add`, `alter`, and `delete`.

### Creating a new RACF group

The sample below creates a group called "SYSPROG" with the gid a of 6667.

```python

from sear import sear

result = sear(
        {
        "operation": "add",
        "admin_type": "group",
        "group": "SYSPROG",
        "traits": {
            "omvs:gid": 6667,
        },
        }
    )

print(result.result)
```

### Altering a RACF group

The sample below changes the "SYSPROG" RACF group to have a gid of 1234567.

```python

from sear import sear

result = sear(
        {
        "operation": "alter",
        "admin_type": "group",
        "group": "SYSPROG",
        "traits": {
            "omvs:gid": 1234567,
        },
        }
    )

print(result.result)
```

### Deleting a RACF group

The below sample deletes the RACF group "DEVOPS".

```python

from sear import sear

result = sear(
    {
    "operation": "delete",
    "admin_type": "group",
    "group": "DEVOPS",
    },
    )

print(result.result)
```
