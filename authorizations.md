---
layout: default
has_children: false
has_toc: false
---

# Required authorizations

This page details the authorization you need to use the SEAR API. You can use the API without having access to all of these profiles at the same time, do keep in mind it might restrict which parts you can use. It's for example possible to use this granularity to give a system user only the ability to extract information with this API and deliver the RACF data as a report, since there is no need to give more permission than is necessary. Inversely it is also possible to only give a system user the ability to change things in RACF, though that is not as useful for security since being able to change things in RACF also means the user can escalate their privileges with the API.

{: .warning }

> Make sure `IRR.IRRSMO00.DISABLE.XML` is not defined in the `XFACILIT`, as it will prevent you from using non-extract/search functionality in SEAR.

{: .warning }

> In general access to the profiles listed below should only be given out to security administrators or security automation users. Even read access to the API should be given out cautiously, being able to "data mine" the RACF database is useful for bad actors. Profiles on this page should **always** have a UACC of `NONE`.

## Data extraction requests

These profiles are the ones you need access to in order to extract information out of the RACF database

| **Access** | **General Resource Profile** | **Class** | **Functionality** |
| `READ` | `IRR.RADMIN.LISTUSER` | `FACILITY` | Extract **User Profiles** |
| `READ` | `IRR.RADMIN.LISTGRP` | `FACILITY` | Extract **Group Profiles** |
| `READ` | `IRR.RADMIN.RLIST` | `FACILITY` | Extract **General Resource Profiles** |
| `READ` | `IRR.RADMIN.LISTDSD` | `FACILITY` | Extract **Data Set Profiles** |
| `READ` | `IRR.RADMIN.SETROPTS.LIST` | `FACILITY` | List **RACF Options** |
| `CONTROL` | `IRR.DIGTCERT.LIST` | `FACILITY` | List **Certificates** |
| `UPDATE` | `IRR.DIGTCERT.LISTRING` | `FACILITY` | List **Keyrings** |

If you only give `READ` access to the `IRR.DIGTCERT` profiles `in FACILITY` you will only be able to extract information on your own certificates and keyrings.

## Modifying the RACF database

These profiles are the ones you need access to in order to modify things in the RACF database, such as create a new user or delete dataset profile.

| **Access** | **General Resource Profile** | **Class** | **Functionality** |
| `READ` | `IRR.IRRSMO00.PRECHECK` | `XFACILIT` | **Add**, **Alter** and **Delete** profiles and modify the RACF database options. Similar access to system special but doesn't allow you to extract information or work with certificates. |
| `UPDATE` | `<userid>.IRRSMO00` | `SURROGAT` | Run **Add**, **Alter**, and **Delete** **Commands** as a **Specific Userid**. Doesn't affect certificate or keyring related requests. |
| `UPDATE` | `IRR.DIGTCERT.ADD` | `FACILITY` | Add a new **Certificate** |
| `UPDATE` | `IRR.DIGTCERT.DELETE` | `FACILITY` | Delete a **Certificate** |
| `UPDATE` | `IRR.DIGTCERT.ADDRING` | `FACILITY` | Add a new **Keyring** |
| `UPDATE` | `IRR.DIGTCERT.DELRING` | `FACILITY` | Delete a **Keyring** |

If you only give `READ` access to the `IRR.DIGTCERT` profiles `in FACILITY` you will only be able to modify your own certificates and keyrings.

## More details

If you want more information on the required authorizations you can find links to the IBM documentation on authorizations for each callable service SEAR uses below:

* More details about the authorizations required for **IRRSMO00** can be found [in the IBM documentation](https://www.ibm.com/docs/en/zos/latest?topic=operations-racf-authorization).
* More details about the authorizations required for **IRRSEQ00** can be found [in the IBM documentation](https://www.ibm.com/docs/en/zos/latest?topic=api-racf-authorization).
* More details about the authorizations required for **IRRSDL64** can be found [in the IBM documentation](https://www.ibm.com/docs/en/zos/latest?topic=library-racf-authorization).
