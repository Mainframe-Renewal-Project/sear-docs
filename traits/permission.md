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
| `"base:access"` | `access` | `string` | `"set"` | `"extract"` |
| `"base:model_profile_class"` | `fclass` | `string` | `"set"` | `"extract"` |
| `"base:model_profile"` | `fprofile` | `string` | `"set"` | `"extract"` |
| `"base:model_profile_generic"` | `fgeneric` | `boolean` | `"set"` | `"extract"` |
| `"base:model_profile_volume"` | `fvolume` | `string` | `"set"` | `"extract"` |
| `"base:reset"` | `reset` | `string` | `"set"` | `"extract"` |
| `"base:when_partner_lu_name"` | `whenappc` | `string` | `"set"` | `"extract"` |
| `"base:when_console"` | `whencons` | `string` | `"set"` | `"extract"` |
| `"base:when_jes"` | `whenjes` | `string` | `"set"` | `"extract"` |
| `"base:when_program"` | `whenprog` | `string` | `"set"` | `"extract"` |
| `"base:when_servauth"` | `whenserv` | `string` | `"set"` | `"extract"` |
| `"base:when_sms"` | `whensms` | `string` | `"set"` | `"extract"` |
| `"base:when_service"` | `whensrv` | `string` | `"set"` | `"extract"` |
| `"base:when_system"` | `whensys` | `string` | `"set"` | `"extract"` |
| `"base:when_terminal"` | `whenterm` | `string` | `"set"` | `"extract"` |
