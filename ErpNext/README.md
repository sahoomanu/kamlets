# ERPNext Kamelet Connectors

This module provides entity-focused Kamelets that can be composed with other
Kamelet connectors to integrate with ERPNext using its REST API. Each connector
is preconfigured for a popular ERPNext DocType so you can avoid passing generic
paths while keeping a consistent authentication model (`token <apiKey>:<apiSecret>`).

## Available connectors

| Kamelet | Direction | Purpose | Key properties |
| --- | --- | --- | --- |
| `erpnext-customer-source` | Source | Poll customers on a schedule | `baseUrl`, `apiKey`, `apiSecret`, optional `filters`, `fields`, `pageLength`, `period` |
| `erpnext-customer-sink` | Sink | Create or update customers | `baseUrl`, `apiKey`, `apiSecret`, `operation` (`create`/`update`), optional `resourceId` for updates |
| `erpnext-item-source` | Source | Poll items on a schedule | `baseUrl`, `apiKey`, `apiSecret`, optional `filters`, `fields`, `pageLength`, `period` |
| `erpnext-item-sink` | Sink | Create or update items | `baseUrl`, `apiKey`, `apiSecret`, `operation` (`create`/`update`), optional `resourceId` for updates |
| `erpnext-sales-order-source` | Source | Poll sales orders on a schedule | `baseUrl`, `apiKey`, `apiSecret`, optional `filters`, `fields`, `pageLength`, `period` |
| `erpnext-sales-order-sink` | Sink | Create or update sales orders | `baseUrl`, `apiKey`, `apiSecret`, `operation` (`create`/`update`), optional `resourceId` for updates |

All connectors use the same REST authentication headers but fix the ERPNext
DocType endpoint to the relevant entity so they can be composed with other
Kamelets without repeatedly configuring resource paths.
