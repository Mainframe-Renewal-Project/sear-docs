---
layout: default
has_toc: false
parent: Python
---


# Users

Valid operators for this type of request

<div class="valid-operation-table" markdown="block">

| Operator | Valid |
|----------|-------|
| add      | ✅    |
| alter    | ✅    |
| delete   | ✅    |
| extract  | ✅    |
| search   | ✅    |

</div>

## Extracting information

SEAR provides the `extract` and `search` operators to gather information about users.

### Extracting a specific RACF user

Below you can find a sample of some code that extracts information about the RACF user `FDEGILIO`.

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

#### Returned result

<details>

```python
{
  "profile": {
    "base": {
      "base:audit_logging": false,
      "base:read_only_auditor": false,
      "base:auditor": false,
      "base:automatic_dataset_protection": false,
      "base:create_date": "09/13/24",
      "base:default_group": "SYS1",
      "base:group_connections": [
        {
          "base:group_connection_auditor": false,
          "base:group_connection_automatic_dataset_protection": false,
          "base:group_connection_create_date": "09/13/24",
          "base:group_connection_dataset_access": false,
          "base:group_connection_group": "SYS1",
          "base:group_connection_last_connect_date": null,
          "base:group_connection_last_connect_time": null,
          "base:group_connection_operations": false,
          "base:group_connection_owner": "LEONARD",
          "base:group_connection_resume_date": null,
          "base:group_connection_revoke_date": null,
          "base:group_connection_revoked": false,
          "base:group_connection_special": false,
          "base:group_connection_universal_access": "NONE",
          "base:group_connection_used_count": 0
        }
      ],
      "base:group_dataset_access": false,
      "base:has_passphrase": false,
      "base:has_password": false,
      "base:logon_allowed_days": [
        {
          "base:logon_allowed_day": "SUNDAY"
        },
        {
          "base:logon_allowed_day": "MONDAY"
        },
        {
          "base:logon_allowed_day": "TUESDAY"
        },
        {
          "base:logon_allowed_day": "WEDNESDAY"
        },
        {
          "base:logon_allowed_day": "THURSDAY"
        },
        {
          "base:logon_allowed_day": "FRIDAY"
        },
        {
          "base:logon_allowed_day": "SATURDAY"
        }
      ],
      "base:logon_allowed_time": "ANYTIME",
      "base:mfa_password_fallback": false,
      "base:name": "Frank DeGilio",
      "base:operations": false,
      "base:owner": "FDEGILIO",
      "base:passphrase_change_interval": 0,
      "base:passphrase_enveloped": false,
      "base:password_change_interval": 186,
      "base:password_enveloped": false,
      "base:protected": true,
      "base:restrict_global_access_checking": false,
      "base:revoked": false,
      "base:special": false
    },
    "omvs": {
      "omvs:home_directory": "/u/fdegilio",
      "omvs:uid": 24
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

### Searching for RACF users

The sample below gets all users that start with `ZWE`. It will return a list of users, to get metadata on them you will have to run the extract operation on every single RACF user in the list.

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

SEAR provides 3 main operators for updating the RACF database, `add`, `alter`, and `delete`.

### Creating a new RACF user

The sample below creates a user called `ESWIFT` with the base name of `ELIJAH SWIFT`, a UID of 24, and the home directory set to `/home/ESWIFT`.

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
    },
)

print(result.result)
```

You can see the full list of traits in [the traits/user section](https://mainframe-renewal-project.github.io/sear-docs/traits/user/)

### Altering a RACF user

The sample below gives special and read only auditor attributes to the RACF user `LEONARD`.

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
    },
)

print(result.result)
```

You can see the full list of traits in [the traits/user section](https://mainframe-renewal-project.github.io/sear-docs/traits/user/)

### Deleting a RACF user

The below sample deletes the RACF user `LEONARD`.

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
