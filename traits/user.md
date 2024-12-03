---
layout: default
parent: Traits
---

# User Traits

The following tables describes the user segments and traits that are supported for add and alter operations, and returned by extract operations.
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
| `"base:automatic_data_set_protection"` | `ADSP` | `boolean` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:auditor"` | `AUDITOR` | `boolean` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:default_group_authority"` | `AUTH` | `string` | `"set"` | `"add"`<br>`"alter"` |
| `"base:security_category"` | `CATEGORY` | `string`<br>`array` | `"add"`<br>`"remove"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:security_caterogies"`| `NUMCTGY` | `array` | N/A | `"extract"` |
| `"base:class_authorization"` | `CLAUTH` | `string`<br>`array` | `"add"`<br>`"remove"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:class_authorizations"`| `CLCNT` | `array` | N/A | `"extract"` |
| `"base:group_connections"` | `CONNECTS` | `array` | N/A | `"extract"` |
| `"base:group_connection_automatic_data_set_protection"` | `CADSP` | `boolean` | N/A | `"extract"` |
| `"base:group_connection_auditor"` | `CAUDITOR` | `boolean` | N/A | `"extract"` |
| `"base:group_connection_connect_date"` | `CAUTHDA` | `string` | N/A | `"extract"` |
| `"base:group_connection_group` | `CGROUP` | `string` | N/A | `"extract"` |
| `"base:group_connection_data_set_access"` | `CGRPACC` | `string` | N/A | `"extract"` |
| `"base:group_connection_connects"` | `CINITCT` | `number` | N/A | `"extract"` |
| `"base:group_connection_last_connect_date"` | `CLJDATE` | `string` | N/A | `"extract"` |
| `"base:group_conneciton_last_connect_time"` | `CLJTIME` | `string` | N/A | `"extract"` |
| `"base:group_connection_operations` | `COPER` | `boolean` | N/A | `"extract"` |
| `"base:group_connection_owner"` | `COWNER` | `string` | N/A | `"extract"` |
| `"base:group_connection_resume_date"` | `CRESUME` | `string` | N/A | `"extract"` |
| `"base:group_connection_revoke_date"` | `CREVOKE` | `string` | N/A | `"extract"` |
| `"base:group_connection_revoked"` | `CREVOKFL` | `boolean` | N/A | `"extract"` |
| `"base:group_connection_special"` | `CSPECIAL` | `boolean` | N/A | `"extract"` |
| `"base:group_connection_universal_access"` | `CUACC` | `string` | N/A | `"extract"` |
| `"base:create_date"` | `CREATDAT` | `string` | N/A | `"extract"` |
| `"base:installation_data"` | `DATA` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:default_group"` | `DFLTGRP` | `string` | `"set"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:password_expired"` | `EXPIRED` | `boolean` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"` |
| `"base:mfa"` | `FACTORN` | `array` | N/A | `"extract"` |
| `"base:mfa_factor"` | `FACTOR` | `string` | `"set"`<br>`"remove"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:mfa_factor_tag_*"` | `FACTAG*` | `string` | N/A | `"extract"` |
| `"base:mfa_factor_value_*"` | `FACVAL*` | `string` | N/A | `"extract"` |
| `"base:group"` | `GROUP` | `string` | `"set"` | `"add"`<br>`"alter"` |
| `"base:group_data_set_access"` | `GRPACC` | `boolean` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:has_passphrase"` | `HASPHRAS` | `boolean` | N/A | `"extract"` |
| `"base:has_password"` | `HASPWD` | `boolean` | N/A | `"extract"` |
| `"base:last_access_date"` | `LASTDATE` | `string` | N/A | `"extract"` |
| `"base:last_access_time"` | `LASTTIME` | `string` | N/A | `"extract"` |
| `"base:mfa_password_fallback"` | `MFAFLBK` | `boolean` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:mfa_policy"` | `MFAPOLNM` | `string` | `"add"`<br>`"remove"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:mfa_policies"` | `MFAPOLN` | `array` | N/A | `"extract"` |
| `"base:model_data_set"` | `MODEL` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:name"` | `NAME` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:require_operator_id_card"` | `OIDCARD` | `boolean` | `"delete"` | `"add"`<br>`"alter"` |
| `"base:operations"` | `OPER` | `boolean` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:owner"` | `OWNER` | `string` | `"set"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:password_change_date"` | `PASSDATE` | `string` | N/A | `"extract"` |
| `"base:password_change_interval"` | `PASSINT` | `number` | N/A | `"extract"` |
| `"base:password"` | `PASSWORD` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"` |
| `"base:passphrase"` | `PHRASE` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"` |
| `"base:passphrase_change_date"` | `PHRDATE` | `string` | N/A | `"extract"` |
| `"base:passphrase_change_interval"` | `PHRINT` | `number` | N/A | `"extract"` |
| `"base:passphrase_enveloped"` | `PPHENV` | `boolean` | N/A | `"extract"` |
| `"base:protected"` | `PROTECTD` | `boolean` | N/A | `"extract"` |
| `"base:password_enveloped"` | `PWDENV` | `boolean` | N/A | `"extract"` |
| `"base:restrict_global_access_checking"` | `REST` | `boolean` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:resume_date"` | `RESUME` | `string` | `"set"`<br>`"delete"` |  `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:revoke_date"` | `REVOKE` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:revoked"` | `REVOKEFL` | `boolean` | N/A | `"extract"` |
| `"base:audit_responsibility"` | `ROAUDIT` | `boolean` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:security_label"` | `SECLABEL` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:security_level"` | `SECLEVEL` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:special"` | `SPECIAL` | `boolean` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:universal_access"` | `UACC` | `string` | `"set"` | `"add"`<br>`"alter"` |
| `"base:audit_logging"` | `UAUDIT` | `boolean` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:logon_allowed_day"` | `WHENDAYS` | `string` | `"set"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:logon_allowed_days"` | `WHENDYCT` | `array` | N/A | `"extract"` |
| `"base:logon_allowed_when_service"` | `WHENSRV` | `string` | `"set"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"base:logon_allowed_when_time"` | `WHENTIME` | `string` | `"set"` | `"add"`<br>`"alter"`<br>`"extract"` |

## OMVS Segment

| **Trait** | **RACF Key** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"omvs:max_address_space_size"` | `ASSIZE` | `number` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"omvs:auto_uid"` | `AUTOUID` | `boolean` | `"set"` | `"add"`<br>`"alter"` |
| `"omvs:max_cpu_time"` | `CPUTIME` | `number` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"omvs:max_files_per_process"` | `FILEPROC` | `number` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `omvs:home_directory` | `HOME` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"omvs:max_non_shared_memory"` | `MEMLIMIT` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"omvs:max_file_mapping_pages"` | `MMAPAREA` | `number` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"omvs:max_processes"` | `PROCUSER` | `number` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"omvs:default_shell"` | `PROGRAM` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"omvs:shared"` | `SHARED` | `boolean` | `"set"` | `"add"`<br>`"alter"` |
| `"omvs:max_shared_memory"` | `SHMEMMAX` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"omvs:max_threads"` | `THREADS` | `number` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract'` |
| `"omvs:uid"` | `UID` | `number` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |

## TSO Segment

| **Trait** | **RACF Key** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"tso:account_number"` | `ACCTNUM` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:logon_command"` | `COMMAND` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:sysout_destination_id"` | `DEST` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:hold_class"` | `HLDCLASS` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:job_class"` | `JOBCLASS` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:max_region_size"` | `MAXSIZE` | `number` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:message_class"` | `MSGCLASS` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:logon_procedure"` | `PROC` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:security_label"` | `SECLABEL` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:default_region_size"` | `SIZE` | `number` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:sysout_class"` | `SYSOUTCL` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:data_set_allocation_unit"` | `UNIT` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
| `"tso:user_data"` | `USERDATA` | `string` | `"set"`<br>`"delete"` | `"add"`<br>`"alter"`<br>`"extract"` |
