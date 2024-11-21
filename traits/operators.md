---
layout: default
parent: Traits
---

# Operators

The following operators can be used to tell RACF how a trait should be processed by add and alter oprations.
{: .fs-6 .fw-300 }

&nbsp;

Operators are specified using the format `<operator>:<segment>:<trait>`, where the `<operator>` token is the **Operator**, the `<segment>` token is the **RACF Segment**, and the `<trait>` token is the **Trait**.

&nbsp;

{: .note }
> _**Operators** can and should be omitted for `"set"` and `"delete"` operations, where setting a **Trait** to a value that is **NOT** `null` results in the **Trait** being **Set** to that value, and setting a **Trait** to `null` results in the **Trait** being **Deleted**._

&nbsp;

{: .note }
> _Every **Operator** is not supported for every **Trait**. Check the corresponding [Trait Table](../../traits/) to see what **Operators** are supported for a given **Trait**._

&nbsp;

| **Operator** | **Description** |
| `"set"` | **Set** A **Trait** to a value. |
| `"add"` | **Add** one or more values to an existing *"list"* **Trait**. |
| `"remove"` | **Remove** one or more values from an existing *"list"* **Trait**. |
| `"delete"`| **Delete** the existing value for a **Trait** if there is one. |

&nbsp;

## 💻 Example

&nbsp;

The following **RACFu Trait JSON** describes modifications to the following **User Traits**:
* **Set** the **OMVS UID** to `24`.
* **Add** `FACILITY` and `XFACILIT` to the existing **Class Authorizations** list.
* **Remove** `TERMINAL` from the existing **Class Authorizations** list.
* **Delete** the existing value for **TSO User Data** if there is one.

###### JSON
```json
{
  "set:omvs:uid": 24,
  "add:base:class_authorizations": ["FACILITY", "XFACILIT"],
  "remove:base:class_authorizations": "TERMINAL",
  "delete:tso:user_data": null
}
```

The following **RACFu Trait JSON** describes modifications to the following **User Traits** **Without** the use of **Operators**:
* **Set** the **OMVS UID** to `24`.
* **Delete** the existing value for **TSO User Data** if there is one.

###### JSON
```json
{
  "omvs:uid": 24,
  "tso:user_data": null
}
```
