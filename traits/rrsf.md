---
layout: default
parent: Traits
nav_order: 8
---

# RRSF Options Traits

{: .warning }

> Please note RRSF support is exclusive to SEAR 0.4.0 and later, earlier versions do not support this feature.

The following tables describes the RRSF options traits that are returned by extract operations.

## `base`

| **Trait** | **RACF Key** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"base:subsystem_name"` | `N/A` | `string` | N/A | `"extract"` |
| `"base:subsystem_userid"` | `N/A` | `string` | N/A | `"extract"` |
| `"base:subsystem_operator_prefix"` | `N/A` | `string` | N/A | `"extract"` |
| `"base:number_of_defined_nodes"` | `N/A` | `uint` | N/A | `"extract"` |
| `"base:nodes"` | `N/A` | `repeat` | N/A | `"extract"` |
| `"base:full_rrsf_communication_active"` | `N/A` | `bool` | N/A | `"extract"` |
| `"base:full_autodirect_active"` | `N/A` | `bool` | N/A | `"extract"` |
| `"base:autodirect_application_updates"` | `N/A` | `bool` | N/A | `"extract"` |
| `"base:autodirect_passwords"` | `N/A` | `bool` | N/A | `"extract"` |
| `"base:appc_trace_active"` | `N/A` | `bool` | N/A | `"extract"` |
| `"base:image_trace_active"` | `N/A` | `bool` | N/A | `"extract"` |
| `"base:ssl_trace_active"` | `N/A` | `bool` | N/A | `"extract"` |
| `"base:privileged_attribute_on"` | `N/A` | `bool` | N/A | `"extract"` |
| `"base:trusted_attribute_on"` | `N/A` | `bool` | N/A | `"extract"` |
