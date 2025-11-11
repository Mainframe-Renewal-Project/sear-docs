---
layout: default
parent: Traits
nav_order: 8
---

{: .warning }

> Please note RRSF support is exclusive to SEAR 0.4.0 and later, earlier versions do not support it.

# RRSF Options Traits

The following tables describes the RRSF options traits that are returned by extract operations.

## `base`

| **Trait** | **RACF Key** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"base:subsystem_name"` | `N/A` | `string` | N/A | `"extract"` |
| `"base:subsystem_userid"` | `N/A` | `string` | N/A | `"extract"` |
| `"base:subsystem_operator_prefix"` | `N/A` | `string` | N/A | `"extract"` |
| `"base:number_of_defined_nodes"` | `N/A` | `uint` | N/A | `"extract"` |
| `"base:node_definitions"` | `N/A` | `repeat` | N/A | `"extract"` |
