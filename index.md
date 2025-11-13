---
layout: page
nav_exclude: true
---

![SEAR logo](/assets/images/logo.svg)

&nbsp;

Security API for RACF (SEAR) - A standardized JSON interface for RACF that enables seamless exploitation by programming languages that have a foreign language interface for C/C++ and native or third-party JSON support. SEAR is a fork of RACFu, an abandoned RACF API created by IBM.
{: .fs-6 .fw-300 }

&nbsp;

{: .development_status }
> _**SEAR** is currently in **Alpha**, meaning that some core functionality may still be missing, unstable, and or may still need more thorough testing._

&nbsp;

{: .warning }

> * SEAR encodes the data it passes to RACF in Code Page `IBM-1047`.
> * _If you are entering information with special or national characters, users viewing or altering this information from terminals using different or international codepages may see unexpected data._
> * _Please consult a list of invariant characters to use for such information if this applies to you._

## Mission Statement

As automation becomes more and more prevalent, the need to manage the security environment programmatically increases. On z/OS that means managing a security product like the IBM **Resource Access Control Facility** _(RACF)_. RACF is the primary facility for managing identity, authority, and access control for z/OS. There are more than 50 callable services with assembler interfaces that are part of the RACF API. The complete set of interfaces can be found [in the IBM documentation](https://www.ibm.com/docs/en/zos/latest?topic=racf-zos-security-server-callable-services).

&nbsp;

While there are a number of languages that can be used to manage RACF, _(from low level languages like Assembler to higher level languages like REXX)_, the need to be able to easily exploit RACF management functions using existing industry standard programming languages and even programming languages that don't exist yet is paramount. The SEAR project is focused on making RACF management functions available to all programming languages that have native or third-party JSON support and a foreign language interface for C/C++. This will make it easier to pivot to new tools and programming languages as technology, skills, and business needs continue to evolve in the foreseeable future.

## Minimum z/OS & Language Versions

All versions of **z/OS** and the **IBM Open Enterprise SDK for Python** that are fully supported by IBM are supported by SEAR.

* [z/OS Product Lifecycle](https://www.ibm.com/support/pages/lifecycle/search/?q=5655-ZOS,%205650-ZOS)
* [IBM Open Enterprise SDK for Python Product Lifecycle](https://www.ibm.com/support/pages/lifecycle/search?q=5655-PYT)

## Dependencies

* **R_SecMgtOper (IRRSMO00)**: Security Management Operations.
* **R_Admin (IRRSEQ00)**: RACF Administration API.
* **R_Datalib (IRRSEQ00)**: RACF Certificate data library.
* **RACF Subsystem Address Space**: This is a dependency for both **IRRSMO00** and **IRRSEQ00**. More information can be found [in the IBM documentation](https://www.ibm.com/docs/en/zos/latest?topic=considerations-racf-subsystem).

## Authorizations

The following authorizations are required in order to exploit some of the basic the functionality that SEAR provides.

| **Access** | **General Resource Profile** | **Class** | **Functionality** |
| `READ` | `IRR.RADMIN.LISTUSER` | `FACILITY` | Extract **User Profiles** |
| `READ` | `IRR.RADMIN.LISTGRP` | `FACILITY` | Extract **Group Profiles** |
| `READ` | `IRR.RADMIN.RLIST` | `FACILITY` | Extract **General Resource Profiles** |
| `READ` | `IRR.RADMIN.LISTDSD` | `FACILITY` | Extract **Data Set Profiles** |
| `READ` | `IRR.RADMIN.SETROPTS.LIST` | `FACILITY` | List **RACF Options** |
| `READ` | `IRR.IRRSMO00.PRECHECK` | `XFACILIT` | **Add**, **Alter** and **Delete** Profiles |
| `UPDATE` | `<userid>.IRRSMO00` | `SURROGAT` | Run **Add**, **Alter**, and **Delete** **Commands** as a **Specific Userid** |

See the full list in the [Required authorizations](./authorizations.md) page, as it contains information on authorizations required for certificate and keyring requests as well as more information in general.

## Installing the Python interface

{: .note }
> _You may also optionally [Download SEAR From GitHub](https://github.com/Mainframe-Renewal-Project/sear/releases)._

You can install SEAR with the following command:

```shell
pip install pysear
```

If the command fails you might need to set up artifactory access to your mainframe or download SEAR from [PyPi](https://pypi.org/project/pysear/) or [GitHub](https://github.com/Mainframe-Renewal-Project/sear/releases).

## Testing SEAR

After you have installed it you can test it from a z/OS Unix shell environment

```python
python
>>> from sear import sear
>>> result = sear({"operation": "extract", "admin_type": "user", "userid": "SQUIDWRD"})
>>> result.result
{'profile': {'base': {'base:audit_logging': False, 'base:read_only_auditor': False, 'base:auditor': False, 'base:automatic_dataset_protection': False, 'base:create_date': '09/13/24', 'base:default_group': 'SYS1', 'base:group_connections': [{'base:group_connection_auditor': False, 'base:group_connection_automatic_dataset_protection': False, 'base:group_connection_create_date': '09/13/24', 'base:group_connection_dataset_access': False, 'base:group_connection_group': 'SYS1', 'base:group_connection_last_connect_date': None, 'base:group_connection_last_connect_time': None, 'base:group_connection_operations': False, 'base:group_connection_owner': 'LEONARD', 'base:group_connection_resume_date': None, 'base:group_connection_revoke_date': None, 'base:group_connection_revoked': False, 'base:group_connection_special': False, 'base:group_connection_universal_access': 'NONE', 'base:group_connection_used_count': 0}], 'base:group_dataset_access': False, 'base:has_passphrase': False, 'base:has_password': False, 'base:logon_allowed_days': [{'base:logon_allowed_day': 'SUNDAY'}, {'base:logon_allowed_day': 'MONDAY'}, {'base:logon_allowed_day': 'TUESDAY'}, {'base:logon_allowed_day': 'WEDNESDAY'}, {'base:logon_allowed_day': 'THURSDAY'}, {'base:logon_allowed_day': 'FRIDAY'}, {'base:logon_allowed_day': 'SATURDAY'}], 'base:logon_allowed_time': 'ANYTIME', 'base:mfa_password_fallback': False, 'base:name': 'SQUIDWARD', 'base:operations': False, 'base:owner': 'LEONARD', 'base:passphrase_change_interval': 0, 'base:passphrase_enveloped': False, 'base:password_change_interval': 186, 'base:password_enveloped': False, 'base:protected': True, 'base:restrict_global_access_checking': False, 'base:revoked': False, 'base:special': False}, 'omvs': {'omvs:home_directory': '/u/squidwrd', 'omvs:uid': 24}}, 'return_codes': {'racf_reason_code': 0, 'racf_return_code': 0, 'sear_return_code': 0, 'saf_return_code': 0}}
```

## Architecture

{: .warning }
> _Just because a **Programming Language Exploiter** is shown on this architecture diagram does not mean that there is or will be an interface created, maintained, and distributed by the SEAR team for that programming language. The interfaces currently maintained and distributed by the SEAR team can be found [in the interfaces page](./interfaces/)._

&nbsp;

<pre class="mermaid">
flowchart TB
 subgraph s1["C/C++"]
        n1["Security API for RACF (SEAR)"]
        n2@{ label: "<span style=\"padding-left:\">IRRSMO00 (64-bit OSLINK EBCDIC)</span>" }
        n5["Setropts, user, group, dataset, and resource operation (Add, alter, delete)"]
        n11["IRRSDL64 (64 bit OSLINK EBCDIC)"]
        n12["Certificate managment operation (Add, extract, delete)"]
        n7@{ label: "<span style=\"padding-left:\">Setropts, user, group, dataset, and resource operation</span>(Extract or Search)" }
  end
 subgraph s2["HLASM"]
        n4["IRRSEQ00 (31-bit OSLINK EBCDIC)"]
  end
 subgraph s3["SEAR project"]
        s1
        s2
        n3@{ label: "<span style=\"padding-left:\">JSON (UTF-8)</span>" }
        A["SEAR Python JSON interface"]
        n6["Binary (EBCDIC)"]
        n8["Binary (EBCDIC)"]
        n9["RACF"]
        n10["SAF"]
        n14@{ label: "<span style=\"padding-left:\">JSON (UTF-8)</span>" }
        n13@{ label: "<span style=\"padding-left:\">SEAR Golang JSON interface (future interface)</span>" }
        n16@{ label: "<span style=\"padding-left:\">JSON (UTF-8)</span>" }
        n15["SEAR Java JSON interface (future interface)"]
        n18@{ label: "<span style=\"padding-left:\">JSON (UTF-8)</span>" }
        n17["SEAR Node.js JSON interface (future interface)"]
        n19["Binary (EBCDIC)"]
        n21@{ label: "<span style=\"padding-left:\">JSON (UTF-8)</span>" }
        n20["SEAR C/C++ JSON interface"]
  end
    n23["Abstracted Python API (future inteface)"] --- A
    n24["Ansible inteface (future inteface)"] --- n23
    A --- n3
    n3 --- n1
    n1 --- n5 & n7 & n12
    n5 --- n2
    n2 --- n6
    n6 --- n4
    n7 --- n8
    n8 --- n4
    n10 --- n9
    n4 --- n10
    n12 --- n11
    n13 --- n14
    n14 --- n1
    n15 --- n16
    n16 --- n1
    n17 --- n18
    n18 --- n1
    n11 --- n19
    n19 --- n10
    n20 --- n21
    n21 --- n1

    n1@{ shape: rounded}
    n2@{ shape: rounded}
    n5@{ shape: rounded}
    n11@{ shape: rounded}
    n12@{ shape: rounded}
    n7@{ shape: rounded}
    n4@{ shape: rounded}
    n3@{ shape: text}
    A@{ shape: rounded}
    n6@{ shape: text}
    n8@{ shape: text}
    n9@{ shape: cyl}
    n10@{ shape: rounded}
    n14@{ shape: text}
    n13@{ shape: rounded}
    n16@{ shape: text}
    n15@{ shape: rounded}
    n18@{ shape: text}
    n17@{ shape: rounded}
    n19@{ shape: text}
    n21@{ shape: text}
    n20@{ shape: rounded}
    n23@{ shape: rounded}
    n24@{ shape: rounded}
     n1:::Class_08
     n2:::Class_06
     n5:::Class_07
     n11:::Class_06
     n12:::Class_07
     n7:::Class_07
     n4:::Class_06
     n3:::Ash
     A:::Pine
     A:::Class_01
     A:::Class_01
     A:::Class_01
     n6:::Ash
     n8:::Ash
     n9:::Class_05
     n10:::Class_05
     n14:::Ash
     n13:::Pine
     n13:::Class_01
     n13:::Class_02
     n16:::Ash
     n15:::Pine
     n15:::Class_01
     n15:::Class_02
     n15:::Class_03
     n15:::Class_03
     n18:::Ash
     n17:::Pine
     n17:::Class_01
     n17:::Class_02
     n17:::Class_03
     n17:::Class_03
     n17:::Class_04
     n19:::Ash
     n21:::Ash
     n20:::Pine
     n20:::Class_01
     n20:::Class_01
     n20:::Class_01
     n20:::Class_09
    classDef Pine stroke-width:1px, stroke-dasharray:none, stroke:#254336, fill:#27654A, color:#FFFFFF
    classDef Class_02 fill:#68d7e2, color:#000000
    classDef Class_03 fill:#ec2025, color:#FFFFFF, stroke:#000000
    classDef Class_01 fill:#FFD600, color:#000000
    classDef Class_04 fill:#417e38, color:#FFFFFF, stroke:transparent
    classDef Ash stroke-width:1px, stroke-dasharray:none, stroke:#999999, fill:#EEEEEE, color:#000000
    classDef Class_06 stroke:#2962FF, fill:#2962FF, color:#FFFFFF
    classDef Class_05 fill:#757575, color:#FFFFFF
    classDef Class_07 fill:#FF6D00, color:#FFFFFF
    classDef Class_08 fill:#FFFFFF, color:#000000, stroke:#000000
    classDef Class_09 fill:#00559e, stroke:transparent, color:#FFFFFF
    style A stroke:none
    style n13 stroke-width:2px,stroke-dasharray: 2,stroke:#FFFFFF
    style n15 stroke-width:2px,stroke-dasharray: 2,stroke:#FFFFFF
    style n17 stroke-width:2px,stroke-dasharray: 2,stroke:#FFFFFF
    style n20 stroke:none
    style n23 fill:#FFD600,stroke-width:2px,stroke-dasharray: 2,color:#000000,stroke:#FFFFFF
    style n24 fill:#AA00FF,color:#FFFFFF,stroke-width:2px,stroke-dasharray: 2,stroke:#FFFFFF

</pre>
