---
layout: default
has_toc: false
parent: Examples
---

# RRSF

{: .warning }

> Please note RRSF support is exclusive to SEAR 0.4.0 and later, earlier versions do not support this feature.

{: .warning }

> Be mindful of what you do with the RRSF extracted data, it contains many pieces of sensitive information about system layout and network configuration that can be abused by bad actors.

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

SEAR provides the `extract` operator to gather information about the RRSF configuration.

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

#### Returned result

<details>

```python
{
    "profile": {
        "base": {
            "base:appc_trace_active": False,
            "base:autodirect_application_updates": False,
            "base:autodirect_passwords": False,
            "base:full_autodirect_active": False,
            "base:full_rrsf_communication_active": True,
            "base:image_trace_active": False,
            "base:number_of_defined_nodes": 0,
            "base:privileged_attribute_on": True,
            "base:ssl_trace_active": False,
            "base:subsystem_name": "RACF",
            "base:subsystem_operator_prefix": "%",
            "base:subsystem_userid": "RACFSUB",
            "base:trusted_attribute_on": False,
            "base:nodes": [
                {
                    "base:node_name": "CXX",
                    "base:node_description": "TEST NODE",
                    "base:node_state": 128,
                    "base:node_protocol": "tcpip",
                    "base:tcpip_listener_status_active": False,
                    "base:requests_denied": 0,
                },
                {
                    "base:node_name": "CXY",
                    "base:node_description": "TEST NODE 2",
                    "base:node_state": 128,
                    "base:node_protocol": "tcpip",
                    "base:tcpip_listener_status_active": False,
                    "base:requests_denied": 0,
                },
            ] 
        }
    },
    "return_codes": {
        "racf_reason_code": 0,
        "racf_return_code": 0,
        "saf_return_code": 0,
        "sear_return_code": 0,
    },
}

```

</details>
