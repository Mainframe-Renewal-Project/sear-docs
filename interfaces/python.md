---
layout: default
parent: Interfaces
---

# Python

pySEAR is the Python language interface for SEAR, it calls the same core API as the other language interfaces.

## Installing pySEAR

The Python interface of SEAR may be installed from [PyPi](https://pypi.org/project/pysear/) using `pip`.

```shell
pip install pysear
```

You can also pull down pySEAR from GitHub or PyPi and point pip to a whl file, if your system is air-gapped.

```shell
pip install pysear-0.4.0-py313-none-any.whl
```

A third option is setting up Artifactory access, or an equivalent solution, to your mainframe system and pointing pip to your company's artifactory index. Setting up something like Artifactory would allow you to use the first option to install SEAR, assuming it is set up correctly. This is probably the best option, especially if you plan to use Python more in general.

Before you can use pySEAR you will need some RACF authorizations and possibly even need to define some RACF profiles, see [authorizations](/sear-docs/authorizations).

## Using pySEAR

### Request

You can call sear with `sear.sear()`, it accepts a dictionary and has an optional debug mode argument.

Below is an example of how you would create a new user with pySEAR.

```python
# Import pySEAR 
from sear import sear

# Create a basic user called AMURPHY
result = sear(
    {
        "operation": "add",
        "admin_type": "user",
        "userid": "LMURPHY",
        "traits": {
            "base:name": "Lex Murphy",
            "omvs:uid": 24,
            "omvs:home_directory": "/home/LMURPHY",
        },
    },
)

# Print output to the terminal
print(result.result)
```

Let's go over what the different parts of this Python means.

The first bit tells SEAR you want to add something to RACF.

```python
"operation": "add",
```

This bit tells SEAR that the previously mentioned operation is meant to affect RACF users, in this case add a user.

```python
"admin_type": "user",
```

Now you will have to tell SEAR the username for the new user.

```python
"userid": "LMURPHY",
```

The last section allows you to set "traits", this is how you define the information that is to be added to the segments (in this case user segments).

```python
"traits": {
    "base:name": "Lex Murphy",
    "omvs:uid": 24,
    "omvs:home_directory": "/home/LMURPHY",
},
```

### Result

Below is an example of what the result of the previous request might look like.

<details open>

```python
"profile": {
    "base": {
      "base:audit_logging": false,
      "base:read_only_auditor": false,
      "base:auditor": false,
      "base:automatic_dataset_protection": false,
      "base:create_date": "09/13/24",
      "base:default_group": "INGEN",
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
      "base:name": "Lex Murphy",
      "base:operations": false,
      "base:owner": "SYS1",
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
      "omvs:home_directory": "/u/LMURPHY",
      "omvs:uid": 24
    }
  },
  "return_codes": {
    "racf_reason_code": 0,
    "racf_return_code": 0,
    "sear_return_code": 0,
    "saf_return_code": 0
  }
}
```

</details>
