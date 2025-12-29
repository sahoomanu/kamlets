# ERPNext Kamelet Connectors

This module provides two modular Kamelets that can be composed with other Kamlet connectors to integrate with ERPNext using its REST API:

- **`erpnext-source`** polls a DocType at a configurable interval and emits the JSON response.
- **`erpnext-sink`** pushes data into ERPNext by creating or updating a DocType record.

## Configuration Overview

| Kamelet | Key properties | Notes |
| --- | --- | --- |
| `erpnext-source` | `baseUrl`, `apiKey`, `apiSecret`, `docType`, `period`, optional `filters`, `fields`, `pageLength` | Builds an authorized GET request and unmarshals the ERPNext JSON payload. |
| `erpnext-sink` | `baseUrl`, `apiKey`, `apiSecret`, `docType`, `operation` (`create`/`update`), optional `resourceId` for updates | Marshals messages to JSON and issues a POST or PUT to ERPNext. |

Both Kamelets set the `Authorization` header using the ERPNext `token <apiKey>:<apiSecret>` pattern so they can be freely combined with transformation or routing Kamelets in a pipeline.
