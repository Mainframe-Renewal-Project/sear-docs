---
layout: default
---

# Request Format

SEAR provides the following standardized JSON schema for issuing security requests to RACF.
{: .fs-6 .fw-300 }

## Parameters *(JSON Keys)*

&nbsp;

* `"operation"`<br>
  A `string` value describing the **Security Management Function** to perform. The following table describes all of the valid values for `"operation"`.

  &nbsp;

  {: .note }
  > Only the `"alter"` and `"extract"` **Operations** are allowed for the `"racf-options"` **Admin Type**.

  &nbsp;

  {: .note }
  > Only the `"alter"`, `"extract"`, and `"delete"` **Operations** are allowed for the `"permission"` **Admin Type**.

  &nbsp;

  | **Operation** | **Description** |
  | `"add"` | **Add/Create** a new security profile. |
  | `"alter"` | **Alter** an existing security profile. |
  | `"extract"` | **Extract** a security profile's data. |
  | `"delete"` | **Delete** a security profile. |

* `"admin_type"`<br>
  A `string` value describing the type of **Security Administration Request** to issue. The following table describes all of the valid values for `"admin_type"`.

  &nbsp;

  {: .note }
  > _The `"permission"` **Admin Type** is **NOT** allowed for `"extract"` **Operations**._

  &nbsp;

  | **Admin Type** | **Description** |
  | `"user"` | Used for **User** administration. |
  | `"group"` | Used for **Group** administration. |
  | `"group-connection"` | Used for **Group Connection** administration. |
  | `"resource"` | Used for **General Resource Profile** administration. |
  | `"dataset"` | Used for **Data Set** administration. |
  | `"racf-options"` | Used for **RACF Options** administration. |
  | `"permission"` | Used for **Permission** administration. |

* `"profile_name"`<br>
  A `string` value identifying a **Security Profile** to **Add**, **Alter**, **Extract**, or **Delete**.

  &nbsp;

  {: .note }
  > `"profile_name"` is **NOT** allowed to be used with the `"racf-options"` **Admin Type** due to **RACF Options** being a **Singleton** for which there is **NO** concept of multiple discrete "profiles" that can be created, deleted, and managed.

  &nbsp;

  {: .note }
  > `"class_name"` **MUST** be used to indicate which **Class Name** the specified **Security Profile** is associated with for the `"resource"` and `"permission"` **Admin Types**.

  &nbsp;

* `"traits"`<br>
  An `object` describing the **Traits/Attributes** to **Add/Modify** in `"add"` and `"alter"` **Operations**. See [Traits](../traits/) for more detail about how to specify **Traits** for `"add"` and `"alter"` **Operations**, and what **Traits** are supported for each **Admin Type**.

  &nbsp;

  {: .note }
  > `"traits"` is **NOT** allowed to be used with `"extract"` and `"delete"` **Operations**.

  &nbsp;

* `"class_name"`<br>
  A `string` value identifying a **Class Name** that the specified **Security Profile** is associated with.

  &nbsp;

  {: .note }
  > `"class_name"` is **required** for and **only** allowed for the `"resource"` and `"permission"` **Admin Types**.

  &nbsp;

* `"volume"`<br>
  A `string` value identifying a **Volume**.

  &nbsp;

  {: .note }
  > Only the `"dataset"` and `"permission"` **Admin Types** can be used with `"volume"`, and **only** for `"add"`, `"alter"`, and `"delete"` **Operations**.

  &nbsp;

  {: .note }
  > _Note that for the `"permission"` **Admin Type**, this parameter will only take effect if the `"class_name"` parameter is set to `"DATASET"`.

  &nbsp;

* `"generic"`<br>
  A `string` value identifying a **Security Profile** as **Generic** or **Not Generic**.

  &nbsp;

  {: .note }
  > Only the `"dataset"` and `"permission"` **Admin Types** can be used with `"generic"`, and **only** for `"add"`, `"alter"`, and `"delete"` **Operations**.

  &nbsp;

  {: .note }
  > Note that for the `"permission"` **Admin Type**, this parameter will only take effect if the `"class_name"` parameter is set to `"DATASET"`.

  &nbsp;

  {: .note }
  > `"generic"` may **only** be set to `"yes"` or `"no"`.

  &nbsp;

* `"run_as_userid"`<br>
  A `string` value identifying a **z/OS Userid** to perform the **Security Operation** as.

  &nbsp;

  {: .note }
  > In order to use `"run_as_userid"`, the caller must have at least `UPDATE` access to the `<userid>.IRRSMO00` **General Resource Profile** in the `SURROGAT` **Class**, where `<userid>` represents the **z/OS Userid** to perform **Security Operations** as. More information about **IRRSMO00 Authorizations** can be found [in the IBM docs](https://www.ibm.com/docs/en/zos/latest?topic=operations-racf-authorization).

  &nbsp;

  {: .note }
  > `"run_as_userid"` is **NOT** allowed for `"extract"` **Operations**.

## 💻 Request Examples

&nbsp;

{: .note }
> These examples are **NOT** comprehensive and are primarily meant to show users the general structure of `"add"`, `"alter"`, `"extract"` and `"delete"` requests.

&nbsp;

The following **SEAR Request JSON** creates new new **z/OS Userid** called `ERIPLEY` with the following **Traits**:

* A **Name** of `"Ellen Ripley"`.
* An **OMVS UID** of `24`.
* An **OMVS Home Directory** of `"/u/ERIPLEY"`.

### JSON

```json
{
  "operation": "add",
  "admin_type": "user",
  "profile_name": "ERIPLEY",
  "traits": {
    "base:name": "Ellen Ripley",
    "omvs:uid": 24,
    "omvs:home_directory": "/u/ERIPLEY"
  }
}
```

The following **SEAR Request JSON** alters an exsting **z/OS Userid** called `ESATTLER` by **Changing/Setting** the **Name Trait** to `"Ellie Sattler"`.

### JSON

```json
{
  "operation": "alter",
  "admin_type": "user",
  "profile_name": "ESATTLER",
  "traits": {
    "base:name": "Ellie Sattler"
  }
}
```

The following **SEAR Request JSON** deletes an exsting **z/OS Userid** called `MRAINES`.

### JSON

```json
{
  "operation": "delete",
  "admin_type": "user",
  "profile_name": "MRAINES"
}
```

The following **SEAR Request JSON** extracts the **Profile Data** for a **z/OS Userid** called `CDEARING`.

###### JSON

```json
{
  "operation": "extract",
  "admin_type": "user",
  "profile_name": "CDEARING"
}
```
