---
layout: default
parent: Traits
---

# Group Traits

The following tables describes the group segments and traits that are supported for add and alter operations, and returned by extract operations.
{: .fs-6 .fw-300 }

&nbsp;

{: .note }
> _More information about **RACF Keys** can be found [here](https://www.ibm.com/docs/en/zos/3.1.0?topic=tables-user-administration)._

&nbsp;

{: .note }
> _See [Data Types](../data_types) for more information about **Data Types**._

&nbsp;

{: .note }
> _See [Operators](../operators) for more information about **Operator** usage._

## Base Segment

| **Trait** | **RACF Key** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"base:connected_users"` | `connects` | `repeat` | N/A | `"extract"` |
| `"base:connected_user_authority"` | `gauth` | `string` | N/A | `"extract"` |
| `"base:connected_userid"` | `guserid` | `string` | N/A | `"extract"` |
| `"base:create_date"` | `creatdat` | `string` | N/A | `"extract"` |
| `"base:installation_data"` | `data` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:data_set_model"` | `model` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:owner"` | `owner` | `string` | `"set"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:subgroups"` | `subgrpct` | `repeat` | N/A | `"extract"` |
| `"base:subgroup"` | `subgroup` | `string` | `"set"`<br>`"delete"` | `"extract"` |
| `"base:superior_group"` | `supgroup` | `string` | `"set"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:terminal_universal_access"` | `termuacc` | `boolean` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:universal"` | `universl` | `boolean` | `"set"` | `"add"`<br>`"extract"` |

## DFP Segment

| **Trait** | **RACF Key** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"dfp:data_application"` | `dataappl` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"dfp:data_class"` | `dataclas` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"dfp:management_class"` | `mgmtclas` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"dfp:storage_class"` | `storclas` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |

## OMVS Segment

| **Trait** | **RACF Key** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"omvs:auto_gid"` | `autogid` | `string` | `"set"` | `"add"`<br>`"alter"` |
| `"omvs:gid"` | `gid` | `uint` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"omvs:shared"` | `shared` | `string` | `"set"` | `"add"`<br>`"alter"` |

## OVM Segment

| **Trait** | **RACF Key** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"ovm:gid"` | `gid` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |

## TME Segment

| **Trait** | **RACF Key** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"tme:roles"` | `roles` | `string` | `"set"` | `"add"`<br>`"alter"`<br>`"extract"` |
