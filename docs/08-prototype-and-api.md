# Prototype and API Examples

**Author:** Ayazhan Orynbasar

## 1. Purpose

This document shows how the backend API of the system is used. It gives example requests and responses for the main actions of the showroom manager, examples of errors, and small data samples. The structure of the order follows the digital order schema in [06-requirements.md](06-requirements.md), and the components are described in [07-architecture.md](07-architecture.md). The API itself is built with FastAPI, which also generates an interactive documentation page (`/docs`) from the same models, so the examples below can be tried directly.

All examples are illustrative. Dates, numbers and queue lengths are made up to show the format; they are not results of an experiment.

## 2. Endpoints

| Method | Path | Purpose | Screen of the interface | Requirements |
|---|---|---|---|---|
| POST | `/orders/estimate` | Validate an order and return a delivery-date estimate (does not save the order as confirmed) | New order, Estimate result | FR-02, FR-04, FR-05 |
| POST | `/orders` | Save an order, with the committed date when the manager confirms it | Estimate result | FR-03, FR-06 |
| GET | `/orders` | List orders with status and dates | Order list | FR-07 |
| GET | `/orders/{order_id}` | Get one order with its stored estimate | Order details | FR-07 |
| PUT | `/orders/{order_id}` | Change an order that is not yet in production | Order details | FR-15 |
| GET | `/factory/status` | Load by station, orders in progress | Factory status | FR-08 |
| GET | `/catalog/products` | Products, materials and finishes allowed in an order | New order | FR-01 |

Responses use JSON. Dates use the format `YYYY-MM-DD`, and timestamps use ISO 8601 in UTC.

## 3. Example: Estimating an Order

### 3.1 Request

`POST /orders/estimate`

```json
{
  "customer": { "name": "Aigerim Nurlanova", "contact": "+7 700 000 00 00" },
  "requested_date": "2026-11-30",
  "items": [
    {
      "product_type": "wardrobe",
      "dimensions_mm": { "width": 2000, "height": 2400, "depth": 600 },
      "material": "laminated_chipboard",
      "finish": "painted",
      "color": "RAL9010",
      "quantity": 2,
      "options": ["soft_close_hinges", "led_light"]
    }
  ]
}
```

Example call:

```bash
curl -X POST http://localhost:8000/orders/estimate \
  -H "Content-Type: application/json" \
  -d @order.json
```

### 3.2 Response (200 OK)

```json
{
  "order_id": "ORD-2026-0001",
  "status": "estimated",
  "requested_date": "2026-11-30",
  "estimate": {
    "earliest": "2026-11-24",
    "most_likely": "2026-11-28",
    "latest": "2026-12-04",
    "probability_on_requested_date": 0.72,
    "assessment": "at_risk",
    "reasons": [
      {
        "station": "painting",
        "effect_days": 3,
        "note": "Queue of 7 orders at the painting station"
      },
      {
        "station": "cnc",
        "effect_days": 1,
        "note": "One machine breakdown is likely in this period"
      }
    ],
    "simulation": {
      "runs": 200,
      "seed": 42,
      "factory_state_time": "2026-10-22T08:00:00Z",
      "duration_seconds": 3.4
    }
  }
}
```

What the fields mean:

| Field | Meaning |
|---|---|
| `earliest`, `most_likely`, `latest` | Range of completion dates from the simulation. The manager should not promise a single date without looking at the range |
| `probability_on_requested_date` | Share of simulation runs that finish on or before the requested date (0.72 means 72%) |
| `assessment` | `on_time`, `at_risk` or `late`, a simple label for the interface |
| `reasons` | The stations or events that influence the date most, with the delay in days |
| `simulation` | Information to repeat the estimate: number of runs, random seed and the factory state used |

### 3.3 Optional comparison with baselines

If the request has `?compare=true`, the response also contains the two baseline estimates for the same order (used for the demonstration in the interface, FR-17):

```json
"comparison": {
  "digital_twin": "2026-11-28",
  "b1_average_lead_time_plus_buffer": "2026-11-23",
  "b2_static_capacity_check": "2026-11-25"
}
```

## 4. Example: Confirming an Order

`POST /orders`

```json
{
  "order_id": "ORD-2026-0001",
  "committed_date": "2026-12-02"
}
```

Response (201 Created):

```json
{
  "order_id": "ORD-2026-0001",
  "status": "confirmed",
  "requested_date": "2026-11-30",
  "committed_date": "2026-12-02",
  "estimate": { "earliest": "2026-11-24", "most_likely": "2026-11-28", "latest": "2026-12-04" },
  "confirmed_at": "2026-10-22T08:05:12Z"
}
```

The committed date is chosen by the manager. The system does not choose it for them, but it records the estimate that was shown at that moment.

## 5. Error Examples

Every error response has the same shape:

```json
{
  "error": {
    "code": "string",
    "message": "Readable text for the manager",
    "details": []
  }
}
```

### 5.1 Invalid order (422 Unprocessable Entity)

Request with a width that is too large, an unknown finish and a requested date in the past:

```json
{
  "requested_date": "2026-10-01",
  "items": [
    {
      "product_type": "wardrobe",
      "dimensions_mm": { "width": 4500, "height": 2400, "depth": 600 },
      "material": "laminated_chipboard",
      "finish": "gold_plated",
      "quantity": 2
    }
  ]
}
```

Response:

```json
{
  "error": {
    "code": "invalid_order",
    "message": "The order has 3 problems. Please correct them and try again.",
    "details": [
      { "field": "requested_date", "problem": "Requested date must be later than today" },
      { "field": "items[0].dimensions_mm.width", "problem": "Width must be between 300 and 3000 mm" },
      { "field": "items[0].finish", "problem": "Finish must be one of: raw, painted, veneer, laminated" }
    ]
  }
}
```

The interface shows each message next to the field it belongs to (FR-02, NFR-03).

### 5.2 Material shortage (409 Conflict)

The order is correct, but the chosen material is not available in the needed amount:

```json
{
  "error": {
    "code": "material_shortage",
    "message": "Not enough of the selected material is in stock.",
    "details": [
      {
        "material": "laminated_chipboard",
        "needed": 12,
        "unit": "sheets",
        "in_stock": 5,
        "next_delivery_date": "2026-11-10"
      }
    ]
  }
}
```

The manager can then choose another material or send the request again with `"allow_backorder": true`. In that case the twin includes the waiting time for the material in the simulation, and the response lists it as a reason:

```json
{ "station": "materials", "effect_days": 6, "note": "Waiting for the delivery of laminated chipboard on 2026-11-10" }
```

### 5.3 Other errors

| Situation | HTTP code | Error code |
|---|---|---|
| Order not found | 404 | `order_not_found` |
| Order already in production, cannot be changed | 409 | `order_locked` |
| Simulation did not finish in time | 503 | `estimate_unavailable` |
| Request is not valid JSON | 400 | `bad_request` |

## 6. Data Samples

### 6.1 Product catalog

`GET /catalog/products` (shortened):

```json
{
  "products": [
    {
      "product_type": "wardrobe",
      "dimension_limits_mm": {
        "width": [300, 3000],
        "height": [300, 2800],
        "depth": [200, 1000]
      },
      "materials": ["laminated_chipboard", "mdf", "solid_wood"],
      "finishes": ["raw", "painted", "veneer", "laminated"],
      "options": ["soft_close_hinges", "led_light", "mirror_door"]
    },
    {
      "product_type": "kitchen_cabinet",
      "dimension_limits_mm": {
        "width": [300, 1200],
        "height": [300, 2400],
        "depth": [300, 700]
      },
      "materials": ["laminated_chipboard", "mdf"],
      "finishes": ["painted", "laminated"],
      "options": ["soft_close_hinges", "led_light"]
    }
  ]
}
```

### 6.2 Factory status

`GET /factory/status`:

```json
{
  "as_of": "2026-10-22T08:00:00Z",
  "stations": [
    { "station": "panel_cutting", "utilization": 0.62, "queue_length": 2, "free_capacity_hours": 14 },
    { "station": "edge_banding",  "utilization": 0.71, "queue_length": 3, "free_capacity_hours": 10 },
    { "station": "drilling",      "utilization": 0.58, "queue_length": 1, "free_capacity_hours": 16 },
    { "station": "cnc",           "utilization": 0.84, "queue_length": 5, "free_capacity_hours": 6 },
    { "station": "painting",      "utilization": 0.93, "queue_length": 7, "free_capacity_hours": 2 },
    { "station": "staging",       "utilization": 0.40, "queue_length": 1, "free_capacity_hours": 20 }
  ],
  "bottleneck": "painting",
  "orders_in_progress": 14
}
```

### 6.3 Order list

`GET /orders?status=confirmed&limit=2`:

```json
{
  "total": 9,
  "items": [
    {
      "order_id": "ORD-2026-0001",
      "customer": "Aigerim Nurlanova",
      "status": "confirmed",
      "requested_date": "2026-11-30",
      "committed_date": "2026-12-02",
      "most_likely": "2026-11-28"
    },
    {
      "order_id": "ORD-2026-0002",
      "customer": "Dana Seitkali",
      "status": "confirmed",
      "requested_date": "2026-12-10",
      "committed_date": "2026-12-09",
      "most_likely": "2026-12-06"
    }
  ]
}
```

### 6.4 Experiment output format

The experiment runner writes one row per order and method to a CSV file (FR-13, FR-14). The values below only show the layout of the file and are not real results:

```csv
scenario,replication,order_id,method,estimated_date,actual_date,abs_error_days,on_time,estimation_seconds
S1-low-calm,1,ORD-0001,twin,2026-11-28,2026-11-29,1,true,3.1
S1-low-calm,1,ORD-0001,B1,2026-11-23,2026-11-29,6,false,0.0
S1-low-calm,1,ORD-0001,B2,2026-11-25,2026-11-29,4,false,0.0
```

The summary table has one row per scenario and method with MAE, MAPE, bias and on-time share, as defined in the verification plan.

## 7. Screens and the API Calls They Use

| Screen | Calls |
|---|---|
| New order | `GET /catalog/products` to fill the lists; `POST /orders/estimate` when the manager presses the estimate button |
| Estimate result | Uses the response of the estimate call; `POST /orders` when the manager confirms |
| Order list | `GET /orders` with filters, sorting and paging |
| Order details | `GET /orders/{order_id}`; `PUT /orders/{order_id}` to change; `POST /orders/estimate` to estimate again |
| Factory status | `GET /factory/status` |

The mockups of these screens are stored together with the other design files. They show the same fields that appear in the examples above.

## 8. Notes and Limitations

- The API is not a finished product: field names may change during implementation. The interactive documentation generated by FastAPI will always show the current version.
- The numbers in the examples are invented. They are not measured values.
- The prototype does not include users, login or roles, because the project does not require them.
- A real factory would send its status through its own systems. In this project the Factory Emulator plays that role.
