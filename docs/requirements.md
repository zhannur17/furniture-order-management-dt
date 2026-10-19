# Functional and Non-Functional Requirements

**Author:** Zhannur Meirambek

---

## 1. Purpose and Scope

The system allows for one decision to be made – the delivery-date commitment given to the client by the showroom manager at the time the custom furniture order is created. The system includes the minimalist web interface for the managers, backend with the database and API, and the digital twin of the factory based on simulations. Other functions such as pricing, product design automation, scheduling of the work on the shop floor, and in actual factories deployment are not considered in this context.

## 2. Stakeholders and Users

| Role | Description | Main needs |
|---|---|---|
| Showroom manager | Accepts orders from customers | Enter an order quickly, get a date range with reasons, confirm the order |
| Production planner | Knows the factory load | See current load and bottlenecks; understand why a date is late |
| Researcher (project team) | Evaluates the method | Run experiments, compare the twin with baselines B1 and B2, export results |
| Supervisor / committee | Assesses the work | Reproducible results, clear documentation |

## 3. Functional Requirements

Priority: **M** = must, **S** = should, **C** = could.

| ID | Requirement | Priority | Objective |
|---|---|---|---|
| FR-01 | The manager can create an order from a product catalog (product type, dimensions, material, finish, quantity, customer name, requested date). | M | O4 |
| FR-02 | The system validates the order (required fields, allowed value ranges, material availability) and shows clear error messages. | M | O4 |
| FR-03 | The system stores each order as a structured digital order in JSON format (see Section 6). | M | O4 |
| FR-04 | For a valid order the system returns an estimated completion date as a range (earliest, most likely, latest) and the probability of meeting the requested date. | M | O3, O4 |
| FR-05 | The result includes reasons: the main bottleneck stations, queue lengths and material delays that affect the date. | M | O4 |
| FR-06 | The manager can confirm an order with a committed date; the confirmed order is saved with the estimate. | M | O4 |
| FR-07 | The manager can view a list of orders with status, requested date, committed date and estimate. | M | O4 |
| FR-08 | The manager can view the current factory status: load by station, orders in progress, expected free capacity. | S | O4 |
| FR-09 | The digital twin simulates the production route of an order (panel cutting, edge banding, drilling, CNC, painting, staging) with stochastic processing times and breakdowns, using Monte Carlo runs. | M | O2 |
| FR-10 | The twin takes the current factory state (orders in progress, queues, stock) as input and updates it when the order status changes. | M | O2 |
| FR-11 | The system provides baselines B1 (average historical lead time plus a fixed buffer) and B2 (static capacity check without feedback) for the same orders. | M | O3 |
| FR-12 | An independent factory emulator generates the "actual" completion dates used for evaluation. | M | O3 |
| FR-13 | An experiment runner executes all scenarios (3 load levels × 2 disturbance settings × about 30 replications × about 200 orders) and stores results. | M | O3 |
| FR-14 | The system computes MAE, MAPE, bias, on-time share and estimation time for the twin, B1 and B2, and exports them as CSV. | M | O3 |
| FR-15 | The manager can change the estimate when the requested date or order parameters are edited. | S | O4 |
| FR-16 | Results of the statistical comparison (Wilcoxon signed-rank test with Holm correction) are reproducible with a single command. | S | O3 |
| FR-17 | The interface shows a comparison of the twin estimate with B1 and B2 for the same order (for demonstration). | C | O4 |

## 4. Non-Functional Requirements

| ID | Category | Requirement | Verification |
|---|---|---|---|
| NFR-01 | Performance | An estimate for one order is returned within 10 seconds for 200 Monte Carlo runs. | Timing test |
| NFR-02 | Usability | A new manager can enter and confirm an order in under 3 minutes without training, using at most 5 screens. | Usability walkthrough with 3 testers |
| NFR-03 | Reliability | Invalid input never causes a server error; the API returns a 4xx code with a message. | API tests |
| NFR-04 | Reproducibility | All experiments use fixed random seeds and can be repeated with one command and the same data. | Re-run and compare results |
| NFR-05 | Maintainability | Backend code follows PEP 8; unit-test coverage of core modules at least 70%. | CI report |
| NFR-06 | Portability | The whole system starts with `docker compose up` on a clean machine. | Clean-install test |
| NFR-07 | Transparency | Every model assumption (processing times, breakdowns, working hours) is documented and configurable. | Documentation review |
| NFR-08 | Security | No real customer data is stored; user input is validated and parameterised queries are used. | Code review |
| NFR-09 | Traceability | Every task, commit and pull request carries a DIP-N identifier. | Repository check |

## 5. Constraints and Assumptions

- Without access to actual factory data, the evaluation relies on a synthetic data set; therefore, the results are specific to the simulated environment.
- The link between the twin and the factory is established through simulation, no live connection to machines is established.
- Only one family of furniture products (cabinet and panels) is modelled with a total of 6 assembly stations.
- The following technology stack is used: FastAPI, PostgreSQL with SQLAlchemy, SimPy, React with TypeScript and Vite, Docker Compose, pytest and GitHub Actions. 
- Development is confined to the duration of the project with a very simple interface.

## 6. Digital Order Schema (JSON)

```json
{
  "order_id": "ORD-2026-0001",
  "created_at": "2026-10-20T10:15:00Z",
  "customer": { "name": "string", "contact": "string" },
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
  ],
  "status": "draft",
  "estimate": {
    "earliest": "2026-11-24",
    "most_likely": "2026-11-28",
    "latest": "2026-12-04",
    "probability_on_requested_date": 0.72,
    "reasons": [
      { "station": "painting", "effect_days": 3, "note": "queue of 7 orders" }
    ]
  },
  "committed_date": null
}
```

Validation rules:

| Field | Rule |
|---|---|
| `requested_date` | Later than the creation date |
| `items` | At least 1 item; at most 20 |
| `dimensions_mm` | Width 300–3000, height 300–2800, depth 200–1000 |
| `quantity` | Integer 1–50 |
| `material`, `finish` | One of the catalog values |
| `status` | `draft`, `estimated`, `confirmed`, `in_production`, `completed` |

## 7. Main Use Scenario

1. The manager opens the new-order screen and enters the customer's request.
2. The system validates the order and calls the digital twin.
3. The twin simulates the order in the current factory state and returns a date range, a probability and reasons.
4. The manager tells the customer a date and confirms the order.
5. The order is saved; the factory status is updated.

## 8. Acceptance Criteria

| Requirement group | Criterion |
|---|---|
| FR-01 to FR-03 | An order with valid data is saved and returned unchanged by the API; invalid data is rejected with a clear message. |
| FR-04 to FR-06 | Each estimate has three dates, a probability and at least one reason; confirming saves the committed date. |
| FR-09 to FR-10 | In 100 test runs the twin finishes every order and results change when load or breakdown settings change. |
| FR-11 to FR-14 | For the same orders the system outputs MAE, MAPE, bias and on-time share for the twin, B1 and B2. |
| NFR-01 | 95% of estimates are returned in 10 seconds or less. |
| NFR-06 | A reviewer starts the system from the repository README with documented commands only. |

## 9. Traceability

| Objective | Requirements |
|---|---|
| O1 (analysis of the problem and existing work) | Literature review, system comparison |
| O2 (digital twin model) | FR-09, FR-10, NFR-07 |
| O3 (evaluation against baselines) | FR-11 to FR-14, FR-16, NFR-04 |
| O4 (prototype with minimal manager interface) | FR-01 to FR-08, FR-15, FR-17, NFR-01 to NFR-03, NFR-06 |
| O5 (conclusions and limitations) | Verification plan, project report |