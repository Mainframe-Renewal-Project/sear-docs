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

This structure repeats for every RRSF node defined on the system. Please note that TCP/IP and APPC traits won't appear at the same time, if the node is in APPC mode then the APPC traits will appear but not TCP/IP traits and vice versa.

| **Trait** | **RACF Key** | **Data Types** | **Operators Allowed** | **Supported Operations** |
| `"base:node_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:node_description"` | N/A | `string` | N/A | `"extract"` |
| `"base:node_protocol"` | N/A | `string` | N/A | `"extract"` |
| `"base:multisystem_node_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:date_of_last_received_work"` | N/A | `string` | N/A | `"extract"` |
| `"base:time_of_last_received_work"` | N/A | `string` | N/A | `"extract"` |
| `"base:date_of_last_sent_work"` | N/A | `string` | N/A | `"extract"` |
| `"base:time_of_last_sent_work"` | N/A | `string` | N/A | `"extract"` |
| `"base:node_state"` | N/A | `uint` | N/A | `"extract"` |
| `"base:partner_node_dynamic_parse_level"` | N/A | `string` | N/A | `"extract"` |
| `"base:partner_node_operating_system_version"` | N/A | `uint` | N/A | `"extract"` |
| `"base:partner_node_template_release_level"` | N/A | `uint` | N/A | `"extract"` |
| `"base:partner_node_template_service_level"` | N/A | `uint` | N/A | `"extract"` |
| `"base:tcpip_listener_status_active"` | N/A | `bool` | N/A | `"extract"` |
| `"base:appc_listener_status_active"` | N/A | `bool` | N/A | `"extract"` |
| `"base:requests_denied"` | N/A | `uint` | N/A | `"extract"` |
| `"base:workspace_dataset_prefix"` | N/A | `string` | N/A | `"extract"` |
| `"base:workspace_dataset_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:workspace_dataset_sms_management_class"` | N/A | `string` | N/A | `"extract"` |
| `"base:workspace_dataset_sms_storage_class"` | N/A | `string` | N/A | `"extract"` |
| `"base:workspace_dataset_sms_data_class"` | N/A | `string` | N/A | `"extract"` |
| `"base:workspace_dataset_volume"` | N/A | `string` | N/A | `"extract"` |
| `"base:in_message_dataset_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:in_message_records"` | N/A | `uint` | N/A | `"extract"` |
| `"base:out_message_dataset_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:out_message_records"` | N/A | `uint` | N/A | `"extract"` |
| `"base:temporary_in_message_dataset_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:temporary_out_message_dataset_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:appc_modename"` | N/A | `string` | N/A | `"extract"` |
| `"base:appc_lu_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:appc_tp_name"` | N/A | `string` | N/A | `"extract"` |
| `"base:appc_netname"` | N/A | `string` | N/A | `"extract"` |
| `"base:resolved_tcpip_address"` | N/A | `string` | N/A | `"extract"` |
| `"base:target_tcpip_address"` | N/A | `string` | N/A | `"extract"` |
| `"base:tcpip_port"` | N/A | `string` | N/A | `"extract"` |
| `"base:tcpip_attls_rule"` | N/A | `string` | N/A | `"extract"` |
| `"base:tcpip_attls_cipher"` | N/A | `string` | N/A | `"extract"` |
| `"base:tcpip_attls_certificate_user"` | N/A | `string` | N/A | `"extract"` |
