---
layout: default
has_toc: false
parent: Python
---


# System options

Valid operators for this type of request

<div class="valid-operation-table" markdown="block">

| Operator | Valid |
|----------|-------|
| add      | ❌    |
| alter    | ✅    |
| delete   | ❌    |
| extract  | ✅    |
| search   | ❌    |

</div>

## Extracting information

SEAR provides the `extract` operator to gather information about the RACF database.

### Extracting RACF system options

The sample below returns all of the RACF system options.

```python

from sear import sear

result = sear(
    {
        "operation": "extract",
        "admin_type": "racf-options"
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
    "base:active_classes": [
        "DATASET",
        "USER",
        "GROUP",
        "ACCTNUM",
        "ACEECHK",
        "ACICSPCT",
        "AIMS",
        "ALCSAUTH",
        "APPCLU",
        "APPCPORT",
        "APPCSI",
        "APPL",
        "BCICSPCT",
        "CACHECLS",
        "CBIND",
        "CCICSCMD",
        "CDT",
        "CFIELD",
        "CIMS",
        "COMMAND",
        "CPSMOBJ",
        "CPSMXMP",
        "CRYPTOZ",
        "CSFKEYS",
        "CSFSERV",
        "DASDVOL",
        "DASNAMES",
        "DBNFORM",
        "DCEUUIDS",
        "DCICSDCT",
        "DEVICES",
        "DIGTCERT",
        "DIGTCRIT",
        "DIGTNMAP",
        "DIGTRING",
        "DIMS",
        "DLFCLASS",
        "DSNADM",
        "DSNR",
        "ECICSDCT",
        "EJBROLE",
        "ELIJTEST",
        "FACILITY",
        "FCICSFCT",
        "FIELD",
        "FIMS",
        "FSACCESS",
        "FSEXEC",
        "GCICSTRN",
        "GCPSMOBJ",
        "GCSFKEYS",
        "GDASDVOL",
        "GDSNBP",
        "GDSNCL",
        "GDSNDB",
        "GDSNGV",
        "GDSNJR",
        "GDSNPK",
        "GDSNPN",
        "GDSNSC",
        "GDSNSG",
        "GDSNSM",
        "GDSNSP",
        "GDSNSQ",
        "GDSNTB",
        "GDSNTS",
        "GDSNUF",
        "GDSNUT",
        "GEJBROLE",
        "GIMS",
        "GINFOMAN",
        "GLOBAL",
        "GMBR",
        "GMQADMIN",
        "GMQNLIST",
        "GMQPROC",
        "GMQQUEUE",
        "GSDSF",
        "GSOMDOBJ",
        "GTERMINL",
        "GXCSFKEY",
        "GXFACILI",
        "GZMFAPLA",
        "HBRADMIN",
        "HBRCMD",
        "HBRCONN",
        "HCICSFCT",
        "HIMS",
        "IBMOPC",
        "IDIDMAP",
        "IDTDATA",
        "IIMS",
        "ILMADMIN",
        "INFOMAN",
        "JAVA",
        "JCICSJCT",
        "JESSPOOL",
        "JIMS",
        "KCICSJCT",
        "KERBLINK",
        "LDAP",
        "LDAPBIND",
        "LFSCLASS",
        "LIMS",
        "LOGSTRM",
        "MCICSPPT",
        "MDSNBP",
        "MDSNCL",
        "MDSNDB",
        "MDSNGV",
        "MDSNJR",
        "MDSNPK",
        "MDSNPN",
        "MDSNSC",
        "MDSNSG",
        "MDSNSM",
        "MDSNSP",
        "MDSNSQ",
        "MDSNTB",
        "MDSNTS",
        "MDSNUF",
        "MDSNUT",
        "MFADEF",
        "MGMTCLAS",
        "MIMS",
        "MQADMIN",
        "MQCMDS",
        "MQCONN",
        "MQNLIST",
        "MQPROC",
        "MQQUEUE",
        "NCICSPPT",
        "NDSLINK",
        "NETCMDS",
        "NETSPAN",
        "NODES",
        "NODMBR",
        "NOTELINK",
        "NVASAPDT",
        "OIMS",
        "OMCANDL$",
        "OPERCMDS",
        "PCICSPSB",
        "PERFGRP",
        "PIMS",
        "PKISERV",
        "PMBR",
        "PRINTSRV",
        "PROGRAM",
        "PROPCNTL",
        "PTKTDATA",
        "PTKTVAL",
        "QCICSPSB",
        "QIMS",
        "RACFEVNT",
        "RACFVARS",
        "RACGLIST",
        "RAUDITX",
        "RCICSRES",
        "RDATALIB",
        "REALM",
        "RIMS",
        "RMTOPS",
        "RODMMGR",
        "RRSFDATA",
        "RVARSMBR",
        "SCDMBR",
        "SCICSTST",
        "SDSF",
        "SECDATA",
        "SERVAUTH",
        "SERVER",
        "SHELCIT",
        "SIMS",
        "SMESSAGE",
        "SOMDOBJS",
        "STARTED",
        "STARWARS",
        "STORCLAS",
        "SUBSYSNM",
        "SURROGAT",
        "SYSAUTO",
        "SYSMVIEW",
        "TAPEVOL",
        "TCICSTRN",
        "TERMINAL",
        "TIMS",
        "TSOAUTH",
        "TSOPROC",
        "UCICSTST",
        "UIMS",
        "UNIXMAP",
        "UNIXPRIV",
        "VCICSCMD",
        "VMBATCH",
        "VMBR",
        "VMCMD",
        "VMDEV",
        "VMEVENT",
        "VMLAN",
        "VMMDISK",
        "VMNODE",
        "VMPOSIX",
        "VMRDR",
        "VMSEGMT",
        "VMXEVENT",
        "VTAMAPPL",
        "VXMBR",
        "WBEM",
        "WCICSRES",
        "WIMS",
        "XCSFKEY",
        "XFACILIT",
        "ZMFAPLA",
        "ZMFCLOUD"
    ],
    "base:add_creator_to_access_list": true,
    "base:application_logon_auditing": true,
    "base:audit_log_always_classes": [
        "DIGTCERT",
        "DIGTRING"
    ],
    "base:audit_log_default_classes": [
        "DATASET",
        "ACCTNUM",
        "ACEECHK",
        "ACICSPCT",
        "AIMS",
        "ALCSAUTH",
        "APPCLU",
        "APPCPORT",
        "APPCSERV",
        "APPCSI",
        "APPCTP",
        "APPL",
        "BCICSPCT",
        "CACHECLS",
        "CBIND",
        "CCICSCMD",
        "CDT",
        "CFIELD",
        "CIMS",
        "COMMAND",
        "CONSOLE",
        "CPSMOBJ",
        "CPSMXMP",
        "CRYPTOZ",
        "CSFKEYS",
        "CSFSERV",
        "DASDVOL",
        "DASNAMES",
        "DBNFORM",
        "DCEUUIDS",
        "DCICSDCT",
        "DEVICES",
        "DIGTCRIT",
        "DIGTNMAP",
        "DIMS",
        "DIRACC",
        "DIRAUTH",
        "DIRECTRY",
        "DIRSRCH",
        "DLFCLASS",
        "DSNADM",
        "DSNR",
        "ECICSDCT",
        "EJBROLE",
        "ELIJTEST",
        "FACILITY",
        "FCICSFCT",
        "FIELD",
        "FILE",
        "FIMS",
        "FSACCESS",
        "FSEXEC",
        "FSOBJ",
        "FSSEC",
        "GCICSTRN",
        "GCPSMOBJ",
        "GCSFKEYS",
        "GDASDVOL",
        "GDSNBP",
        "GDSNCL",
        "GDSNDB",
        "GDSNGV",
        "GDSNJR",
        "GDSNPK",
        "GDSNPN",
        "GDSNSC",
        "GDSNSG",
        "GDSNSM",
        "GDSNSP",
        "GDSNSQ",
        "GDSNTB",
        "GDSNTS",
        "GDSNUF",
        "GDSNUT",
        "GEJBROLE",
        "GIMS",
        "GINFOMAN",
        "GLOBAL",
        "GMBR",
        "GMQADMIN",
        "GMQCHAN",
        "GMQNLIST",
        "GMQPROC",
        "GMQQUEUE",
        "GMXADMIN",
        "GMXNLIST",
        "GMXPROC",
        "GMXQUEUE",
        "GMXTOPIC",
        "GSDSF",
        "GSOMDOBJ",
        "GTERMINL",
        "GXCSFKEY",
        "GXFACILI",
        "GZMFAPLA",
        "HBRADMIN",
        "HBRCMD",
        "HBRCONN",
        "HCICSFCT",
        "HIMS",
        "IBMOPC",
        "IDIDMAP",
        "IDTDATA",
        "IIMS",
        "ILMADMIN",
        "INFOMAN",
        "IPCOBJ",
        "IZP",
        "JAVA",
        "JCICSJCT",
        "JESINPUT",
        "JESJOBS",
        "JESSPOOL",
        "JIMS",
        "KCICSJCT",
        "KERBLINK",
        "KEYSMSTR",
        "LDAP",
        "LDAPBIND",
        "LFSCLASS",
        "LIMS",
        "LOGSTRM",
        "MCICSPPT",
        "MDSNBP",
        "MDSNCL",
        "MDSNDB",
        "MDSNGV",
        "MDSNJR",
        "MDSNPK",
        "MDSNPN",
        "MDSNSC",
        "MDSNSG",
        "MDSNSM",
        "MDSNSP",
        "MDSNSQ",
        "MDSNTB",
        "MDSNTS",
        "MDSNUF",
        "MDSNUT",
        "MFADEF",
        "MGMTCLAS",
        "MIMS",
        "MQADMIN",
        "MQCHAN",
        "MQCMDS",
        "MQCONN",
        "MQNLIST",
        "MQPROC",
        "MQQUEUE",
        "MXADMIN",
        "MXNLIST",
        "MXPROC",
        "MXQUEUE",
        "MXTOPIC",
        "NCICSPPT",
        "NDSLINK",
        "NETCMDS",
        "NETSPAN",
        "NODES",
        "NODMBR",
        "NOTELINK",
        "NVASAPDT",
        "OIMS",
        "OMCANDL$",
        "OPERCMDS",
        "OPTAUDIT",
        "PCICSPSB",
        "PERFGRP",
        "PIMS",
        "PKISERV",
        "PMBR",
        "PRINTSRV",
        "PROCACT",
        "PROCESS",
        "PROGRAM",
        "PROPCNTL",
        "PSFMPL",
        "PTKTDATA",
        "PTKTVAL",
        "QCICSPSB",
        "QIMS",
        "RACFEVNT",
        "RACFHC",
        "RACFVARS",
        "RACGLIST",
        "RACHCMBR",
        "RAUDITX",
        "RCICSRES",
        "RDATALIB",
        "REALM",
        "RIMS",
        "RMTOPS",
        "RODMMGR",
        "ROLE",
        "RRSFDATA",
        "RVARSMBR",
        "SCDMBR",
        "SCICSTST",
        "SDSF",
        "SECDATA",
        "SECLABEL",
        "SECLMBR",
        "SERVAUTH",
        "SERVER",
        "SFSCMD",
        "SHELCIT",
        "SIMS",
        "SMESSAGE",
        "SOMDOBJS",
        "STARTED",
        "STARWARS",
        "STORCLAS",
        "SUBSYSNM",
        "SURROGAT",
        "SYSAUTO",
        "SYSMVIEW",
        "TAPEVOL",
        "TCICSTRN",
        "TEMPDSN",
        "TERMINAL",
        "TIMS",
        "TMEADMIN",
        "TSOAUTH",
        "TSOPROC",
        "UCICSTST",
        "UIMS",
        "UNIXMAP",
        "UNIXPRIV",
        "VCICSCMD",
        "VMBATCH",
        "VMBR",
        "VMCMD",
        "VMDEV",
        "VMEVENT",
        "VMLAN",
        "VMMAC",
        "VMMDISK",
        "VMNODE",
        "VMPOSIX",
        "VMRDR",
        "VMSEGMT",
        "VMXEVENT",
        "VTAMAPPL",
        "VXMBR",
        "WBEM",
        "WCICSRES",
        "WIMS",
        "WRITER",
        "XCSFKEY",
        "XFACILIT",
        "ZMFAPLA",
        "ZMFCLOUD",
        "ZOWE"
    ],
    "base:automatic_dataset_protection": false,
    "base:enhanced_generic_naming": true,
    "base:erase_datasets_on_delete": false,
    "base:generic_command_classes": [
        "DATASET",
        "ACCTNUM",
        "ACICSPCT",
        "AIMS",
        "APPCLU",
        "APPCPORT",
        "APPCSERV",
        "APPCSI",
        "APPCTP",
        "APPL",
        "CBIND",
        "CCICSCMD",
        "CIMS",
        "COMMAND",
        "CONSOLE",
        "CPSMOBJ",
        "CPSMXMP",
        "CSFKEYS",
        "CSFSERV",
        "DASDVOL",
        "DASNAMES",
        "DBNFORM",
        "DCICSDCT",
        "DEVICES",
        "DIRACC",
        "DIRAUTH",
        "DIRSRCH",
        "DLFCLASS",
        "DSNR",
        "EJBROLE",
        "ELIJTEST",
        "FACILITY",
        "FCICSFCT",
        "FIELD",
        "FIMS",
        "FSOBJ",
        "FSSEC",
        "GMBR",
        "IBMOPC",
        "INFOMAN",
        "JCICSJCT",
        "JESINPUT",
        "JESJOBS",
        "JESSPOOL",
        "LDAP",
        "LFSCLASS",
        "LOGSTRM",
        "MCICSPPT",
        "MGMTCLAS",
        "MQADMIN",
        "MQCHAN",
        "MQCMDS",
        "MQCONN",
        "MQNLIST",
        "MQPROC",
        "MQQUEUE",
        "NETCMDS",
        "NETSPAN",
        "NODES",
        "NODMBR",
        "NVASAPDT",
        "OIMS",
        "OMCANDL$",
        "OPERCMDS",
        "PCICSPSB",
        "PERFGRP",
        "PIMS",
        "PMBR",
        "PROCACT",
        "PROCESS",
        "PROPCNTL",
        "PSFMPL",
        "PTKTDATA",
        "PTKTVAL",
        "RACFVARS",
        "RACGLIST",
        "RCICSRES",
        "RMTOPS",
        "RODMMGR",
        "RVARSMBR",
        "SCDMBR",
        "SCICSTST",
        "SDSF",
        "SECLMBR",
        "SERVAUTH",
        "SERVER",
        "SHELCIT",
        "SIMS",
        "SMESSAGE",
        "SOMDOBJS",
        "STARTED",
        "STARWARS",
        "STORCLAS",
        "SUBSYSNM",
        "SURROGAT",
        "TAPEVOL",
        "TCICSTRN",
        "TEMPDSN",
        "TERMINAL",
        "TIMS",
        "TSOAUTH",
        "TSOPROC",
        "UNIXPRIV",
        "VMBATCH",
        "VMBR",
        "VMCMD",
        "VMMAC",
        "VMMDISK",
        "VMNODE",
        "VMRDR",
        "VMSEGMT",
        "VTAMAPPL",
        "VXMBR",
        "WRITER",
        "XCSFKEY",
        "XFACILIT",
        "ZMFAPLA",
        "ZMFCLOUD"
    ],
    "base:generic_owner": false,
    "base:generic_profile_checking_classes": [
        "DATASET",
        "ACCTNUM",
        "ACICSPCT",
        "AIMS",
        "APPCLU",
        "APPCPORT",
        "APPCSERV",
        "APPCSI",
        "APPCTP",
        "APPL",
        "CBIND",
        "CCICSCMD",
        "CIMS",
        "COMMAND",
        "CONSOLE",
        "CPSMOBJ",
        "CPSMXMP",
        "CSFKEYS",
        "CSFSERV",
        "DASDVOL",
        "DASNAMES",
        "DBNFORM",
        "DCICSDCT",
        "DEVICES",
        "DIRACC",
        "DIRAUTH",
        "DIRSRCH",
        "DLFCLASS",
        "DSNR",
        "EJBROLE",
        "FACILITY",
        "FCICSFCT",
        "FIELD",
        "FIMS",
        "FSOBJ",
        "FSSEC",
        "GMBR",
        "IBMOPC",
        "INFOMAN",
        "JCICSJCT",
        "JESINPUT",
        "JESJOBS",
        "JESSPOOL",
        "LDAP",
        "LFSCLASS",
        "LOGSTRM",
        "MCICSPPT",
        "MGMTCLAS",
        "MQADMIN",
        "MQCHAN",
        "MQCMDS",
        "MQCONN",
        "MQNLIST",
        "MQPROC",
        "MQQUEUE",
        "NETCMDS",
        "NETSPAN",
        "NODES",
        "NODMBR",
        "NVASAPDT",
        "OIMS",
        "OMCANDL$",
        "OPERCMDS",
        "PCICSPSB",
        "PERFGRP",
        "PIMS",
        "PMBR",
        "PROCACT",
        "PROCESS",
        "PROPCNTL",
        "PSFMPL",
        "PTKTDATA",
        "PTKTVAL",
        "RACFVARS",
        "RACGLIST",
        "RCICSRES",
        "RMTOPS",
        "RODMMGR",
        "RVARSMBR",
        "SCDMBR",
        "SCICSTST",
        "SDSF",
        "SECLMBR",
        "SERVAUTH",
        "SERVER",
        "SIMS",
        "SMESSAGE",
        "SOMDOBJS",
        "STARTED",
        "STORCLAS",
        "SUBSYSNM",
        "SURROGAT",
        "TAPEVOL",
        "TCICSTRN",
        "TEMPDSN",
        "TERMINAL",
        "TIMS",
        "TSOAUTH",
        "TSOPROC",
        "UNIXPRIV",
        "VMBATCH",
        "VMBR",
        "VMCMD",
        "VMMAC",
        "VMMDISK",
        "VMNODE",
        "VMRDR",
        "VMSEGMT",
        "VTAMAPPL",
        "VXMBR",
        "WRITER",
        "XCSFKEY",
        "XFACILIT",
        "ZMFAPLA",
        "ZMFCLOUD"
    ],
    "base:global_access_classes": [
        "DATASET",
        "DSNR",
        "SDSF",
        "SURROGAT"
    ],
    "base:jes_batch": true,
    "base:jes_early_verification": false,
    "base:jes_execution_batch_monitoring": false,
    "base:jes_network_user": "????????",
    "base:jes_undefined_user": "++++++++",
    "base:kerberos_encryption_level": 0,
    "base:list_of_groups_access_checking": true,
    "base:log_commands_issued_by_special_users": true,
    "base:log_operator_actions": false,
    "base:log_racf_command_violations": true,
    "base:log_real_dataset_name": false,
    "base:max_password_change_interval": 186,
    "base:max_session_key_interval": 30,
    "base:min_password_change_interval": 0,
    "base:mixed_case_password_support": false,
    "base:multi_level_security_file_names": false,
    "base:multi_level_security_file_system": "INACTIVE",
    "base:multi_level_security_interprocess": "INACTIVE",
    "base:multi_level_security_label_alteration": false,
    "base:multi_level_security_logon": false,
    "base:password_encryption_algorithm": "LEGACY",
    "base:password_expiration_warning": 10,
    "base:password_rule_1": "4:8 ********",
    "base:primary_language": "ENU",
    "base:profile_modelling_generation_data_group": true,
    "base:profile_modelling_group": true,
    "base:profile_modelling_user": true,
    "base:program_control": true,
    "base:raclist": [
        "ACCTNUM",
        "ACEECHK",
        "APPL",
        "CBIND",
        "CDT",
        "CPSMOBJ",
        "CRYPTOZ",
        "CSFKEYS",
        "CSFSERV",
        "DIGTCERT",
        "DIGTCRIT",
        "DIGTNMAP",
        "DIGTRING",
        "DSNR",
        "EJBROLE",
        "ELIJTEST",
        "FACILITY",
        "JESSPOOL",
        "OPERCMDS",
        "PERFGRP",
        "PTKTDATA",
        "PTKTVAL",
        "RACFVARS",
        "RDATALIB",
        "REALM",
        "SDSF",
        "SERVAUTH",
        "SERVER",
        "SHELCIT",
        "SOMDOBJS",
        "STARTED",
        "STARWARS",
        "SURROGAT",
        "TSOAUTH",
        "TSOPROC",
        "UNIXPRIV",
        "WBEM",
        "XCSFKEY",
        "XFACILIT",
        "ZMFAPLA",
        "ZMFCLOUD"
    ],
    "base:record_user_verification_statistics": true,
    "base:revoke_inactive_userids_interval": 255,
    "base:rvary_status_password": "DEFAULT",
    "base:rvary_status_password_format": "LEGACY",
    "base:rvary_switch_password_format": "LEGACY",
    "base:secondary_language": "ENU",
    "base:security_label_auditing": false,
    "base:security_label_compatibility_mode": false,
    "base:security_label_control": false,
    "base:security_label_system": false,
    "base:special_character_password_support": false,
    "base:tape_dataset_protection": true,
    "base:tape_dataset_security_retention_period": 0,
    "base:terminal_universal_access": "READ"
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

## Updating the RACF system options

You can update the RACF system options through SEAR, the only valid operator is "alter" in this case.

### Altering the RACF system options

The sample below updates the amount of incorrect password attempts allowed on the system to 5.

```python

from sear import sear

result = sear(
    {
        "operation": "alter",
        "admin_type": "racf-options",
        "traits": {
            "base:max_incorrect_password_attempts": 5,
        },
    },
)

print(result.result)
```

You can see the full list of traits in [the traits/racf_options section](https://mainframe-renewal-project.github.io/sear-docs/traits/racf_options/)
