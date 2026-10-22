# Interface Mockups

Mockups of the manager web interface. They show the layout and the data on each screen; they are not a working application. The data in the pictures is illustrative.

Editable design: (https://www.figma.com/design/BRRnwpSaQywG8WqEQt53VU/Furmiture_Manufacturing?node-id=6-1147&t=7x8G33Hh77DRR9jf-1)

| Screen | File | What it shows | API calls |
|---|---|---|---|
| New order | [01-new-order.png](01-new-order.png) | Customer data, requested date, item specification | GET /catalog/products, POST /orders/estimate |
| Delivery estimate | [02-delivery-estimate.png](02-delivery-estimate.png) | Date range, probability of meeting the requested date, main reasons, confirmation | POST /orders |
| Factory status | [03-factory-status.png](03-factory-status.png) | Load by station, bottleneck, orders in progress | GET /factory/status |
| Orders | [04-orders.png](04-orders.png) | Order list with requested and committed dates and status | GET /orders |

Related requirements: FR-01, FR-04 to FR-08. API examples: [prototype-and-api.md](../prototype-and-api.md).