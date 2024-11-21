---
layout: default
parent: Traits
---

# User Traits

The following tables describes the segments and traits that are supported for add and alter operations and returned by extract operations.
{: .fs-6 .fw-300 }

&nbsp;

{: .note }
> _See [Operators](../operators) for more information about **Operator** usage._

&nbsp;

## Base Segment

| **Trait** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"base:automatic_data_set_protection"` | boolean | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:auditor"` | boolean | `"set"`<br>`"delete"` | `add`<br>`"alter"`<br>`"extract"` |
| `"base:default_group_authority"` | string | `"set"` | `"add"`<br>`"alter"` |
| `"base:security_category"` | string<br>array | `"add"`<br>`"remove"` | `add`<br>`alter`<br>`extract` |
| `"base:security_caterogies"`| object | N/A | `"extract"` |
| `"base:class_authorization"` | string<br>array | `"add"`<br>`"remove"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:class_authorizations"`| object | N/A | `"extract"` |
| `"base:group_connections"` | object | N/A | `"extract"` |
| `"base:group_connection_automatic_data_set_protection"` | boolean | N/A | `"extract"` |
| `"base:group_connection_auditor"` | boolean | N/A | `"extract"` |
| `"base:group_connection_connect_date"` | string | N/A | `"extract"` |
| `"base:group_connection_group` | string | N/A | `"extract"` |
| `"base:group_connection_data_set_access"` | string | N/A | `"extract"` |
| `"base:group_connection_connects"` | number | N/A | `"extract"` |
| `"base:group_connection_last_connect_date"` | string | N/A | `"extract"` |
| `"base:group_connection_operations` | boolean | N/A | `"extract"` |
| `"base:group_connection_owner"` | string | N/A | `"extract"` |
| `"base:group_connection_resume_date"` | string | N/A | `"extract"` |
| `"base:group_connection_revoke_date"` | string | N/A | `"extract"` |
| `"base:group_connection_revoked"` | boolean | N/A | `"extract"` |
| `"base:group_connection_special"` | boolean | N/A | `"extract"` |
| `"base:group_connection_universal_access"` | string | N/A | `"extract"` |
| `"base:create_date"` | string | N/A | `"extract"` |
| `"base:installation_data"` | string | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:default_group"` | string | `"set"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:password_expired"` | boolean | `"set"`<br>`"delete"` | `"add"`<br>`"alter"` |
| `"base:mfa"` | object | N/A | `"extract"` |
| `"base:mfa_factor"` | string | `"set"`<br>`"remove"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:mfa_factor_tag_*"` | string | N/A | `"extract"` |
| `"base:mfa_factor_value_*"` | string | N/A | `"extract"` |
| `"base:group"` | string | `"set"` | `"add"`<br>`"alter"` |
| `"base:group_data_set_access"` | boolean | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:has_passphrase"` | boolean | N/A | `"extract"` |
| `"base:has_password"` | boolean | N/A | `"extract"` |
| `"base:last_access_date"` | string | N/A | `"extract"` |
| `"base:last_access_time"` | string | N/A | `"extract"` |
