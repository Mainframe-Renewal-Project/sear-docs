---
layout: default
parent: Traits
---

# Permission Traits

The following tables describes the permission segments and traits that are supported for alter operations and returned by extract operations.
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
| `"base:access"` | `access` | `string` | `"set"` |  |
| `"base:authid"` | `authid` | `string` | `"set"` |  |
| `"base:model_profile_class"` | `fclass` | `string` | `"set"` |  |
| `"base:model_profile"` | `fprofile` | `string` | `"set"` |  |
| `"base:model_profile_generic"` | `fgeneric` | `boolean` | `"set"` |  |
| `"base:model_profile_volume"` | `fvolume` | `string` | `"set"` |  |
| `"base:reset"` | `reset` | `string` | `"set"` |  |
| `"base:when_partner_lu_name"` | `whenappc` | `string` | `"set"` |  |
| `"base:when_console"` | `whencons` | `string` | `"set"` |  |
| `"base:when_jes"` | `whenjes` | `string` | `"set"` |  |
| `"base:when_program"` | `whenprog` | `string` | `"set"` |  |
| `"base:when_servauth"` | `whenserv` | `string` | `"set"` |  |
| `"base:when_sms"` | `whensms` | `string` | `"set"` |  |
| `"base:when_service"` | `whensrv` | `string` | `"set"` |  |
| `"base:when_system"` | `whensys` | `string` | `"set"` |  |
| `"base:when_terminal"` | `whenterm` | `string` | `"set"` |  |
