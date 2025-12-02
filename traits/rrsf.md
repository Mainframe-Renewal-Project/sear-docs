---
layout: default
parent: Traits
nav_order: 8
---

# RRSF Traits

{: .warning }

> Please note RRSF support is exclusive to SEAR 0.4.0 and later, earlier versions do not support this feature.

The following tables describes the RRSF options traits that are returned by extract operations.

## `base`

| **Trait** | **RACF Key** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"base:subsystem_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:subsystem_userid"` | N/A | `string` | N/A | `"extract"` |
| `"base:subsystem_operator_prefix"` | N/A | `string` | N/A | `"extract"` |
| `"base:number_of_defined_nodes"` | N/A | `uint` | N/A | `"extract"` |
| `"base:nodes"` | N/A | `repeat` | N/A | `"extract"` |
| `"base:full_rrsf_communication_active"` | N/A | `bool` | N/A | `"extract"` |
| `"base:full_autodirect_active"` | N/A | `bool` | N/A | `"extract"` |
| `"base:autodirect_application_updates"` | N/A | `bool` | N/A | `"extract"` |
| `"base:autodirect_passwords"` | N/A | `bool` | N/A | `"extract"` |
| `"base:appc_trace_active"` | N/A | `bool` | N/A | `"extract"` |
| `"base:image_trace_active"` | N/A | `bool` | N/A | `"extract"` |
| `"base:ssl_trace_active"` | N/A | `bool` | N/A | `"extract"` |
| `"base:privileged_attribute_on"` | N/A | `bool` | N/A | `"extract"` |
| `"base:trusted_attribute_on"` | N/A | `bool` | N/A | `"extract"` |

## `base:nodes`

This structure repeats for every RRSF node defined on the system.

| `"base:node_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:multisystem_node_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:date_of_last_received_work"` | N/A | `string` | N/A | `"extract"` |
| `"base:time_of_last_received_work"` | N/A | `string` | N/A | `"extract"` |
| `"base:date_of_last_sent_work"` | N/A | `string` | N/A | `"extract"` |
| `"base:time_of_last_sent_work"` | N/A | `string` | N/A | `"extract"` |
| `"base:node_state"` | N/A | `uint` | N/A | `"extract"` |
| `"base:partner_node_operating_system_version"` | N/A | `uint` | N/A | `"extract"` |
| `"base:partner_node_template_release_level"` | N/A | `uint` | N/A | `"extract"` |
| `"base:partner_node_template_service_level"` | N/A | `uint` | N/A | `"extract"` |
| `"base:tcpip_listener_status_active"` | N/A | `bool` | N/A | `"extract"` |
| `"base:appc_listener_status_active"` | N/A | `bool` | N/A | `"extract"` |
| `"base:node_protocol"` | N/A | `string` | N/A | `"extract"` |
| `"base:requests_denied"` | N/A | `uint` | N/A | `"extract"` |
