# Evidence of Project Relevance

**Authors:** Zhannur Meirambek, Ayazhan Orynbasar

## 1. Purpose

This document shows whether the problem of our project is real for the people who face it. We asked people who work with custom orders, and one customer, and compare what they told us with what we expected from the literature. The raw notes are in [interviews.md](interviews.md).

## 2. Method

- We held three discussions with people connected to LignaTech, a workshop and showroom that makes custom doors and furniture: a production owner, a showroom manager and a customer.
- The production owner has about 20 years of experience in the field.
- The answers were collected in writing in October 2026. No names of people are recorded.
- Each role had its own list of questions (see the notes). Several questions are the same for all roles, so that views can be compared.
- We separate **confirmed facts** (what participants told us) from **assumptions** (what we expect, but did not confirm).

## 3. Participants

| # | Role | Company | Experience | Format |
|---|---|---|---|---|
| 1 | Showroom manager | LignaTech | not stated | Written answers |
| 2 | Production owner | LignaTech | About 20 years in the field | Written answers |
| 3 | Customer (ordered an interior door) | LignaTech | not applicable | Written answers |

## 4. Confirmed Facts

Each statement below was said by the participants. The column "Said by" shows who.

| # | Statement | Said by | Related to |
|---|---|---|---|
| F1 | The delivery date is not given automatically. It is fixed after the order is calculated and after production is asked, and the customer expects a confirmed date | Manager, owner, customer | M2, P4, C2 |
| F2 | To give a reliable date, the manager must know the queue, the load of key stations and the availability of materials. This information is spread over tables, messages and calls, so the answer is slow | Manager, owner | M3, M6, P4 |
| F3 | Dates are missed, and the reasons are known: late materials, workshop load, equipment breakdowns, changes after approval, errors in measuring. In the customer's case an order was about 5 days later than promised because materials were late (promised about 2–3 weeks) | Manager, owner, customer | M4, P6, C3 |
| F4 | A missed date has a cost: time of the manager, lower trust of the customer, a possible discount or cancellation. The customer was dissatisfied and had to change plans | Manager, customer | M5, C5 |
| F5 | A range of dates with reasons is wanted: the manager and the owner would use it, and the customer prefers a range (for example 15–20 November) to one date | Manager, owner, customer | M7, P8, C6 |
| F6 | Trust in the estimate depends on current data and on seeing why the date changed | Manager, owner | M7, P8 |
| F7 | The customer wants a notification when the date changes. The manager wants an early warning about the risk of delay | Customer, manager | C7, M4 |

## 5. Assumptions (Not Confirmed by the Discussions)

These come from the literature review and from our own reasoning, or the participants did not give numbers. They are not evidence.

| # | Assumption | Source |
|---|---|---|
| A1 | The share of orders delivered late: no figure was given. The owner said it would need a comparison of promised and actual dates | Not measured |
| A2 | Duration of each production stage: not fixed by the company. Model values come from the literature and are documented | Literature review, [03-literature-review.md](03-literature-review.md) |
| A3 | Delivery times of each material: depend on the supplier and the item, no figures were given. In the simulation, a controlled share of late deliveries is used | Our model assumption |
| A4 | Which software is used today: the manager named tables, phone and messengers, but the exact list still has to be confirmed in the company | To be confirmed |
| A5 | A date range with reasons is more accurate and useful than a single date | Our design idea, to be tested in the experiment |
| A6 | Existing furniture software does not give delivery dates based on the simulated state of the factory | Comparison of existing systems, [04-system-comparison.md](04-system-comparison.md) |

## 6. What the Discussions Mean for the Project

All three participants described the same chain: the date is set before the current load and materials are fully known, it is sometimes missed for reasons that can be named, and the customer and the manager both pay for it. This agrees with the problem statement of the project. The wish for a date range with reasons (F5) supports the main output of the system. The need for current data (F2, F6) supports the requirements for the factory status and for the reasons in the result (FR-05, FR-08).

One thing we did not plan: the customer and the manager ask for a notification when the date changes (F7). This is not a requirement of the first version. We record it as a possible extension.

We did not get numbers (share of late orders, time per stage, supplier times). For this reason the experiment uses simulated data with documented assumptions (A1 to A3), and we do not claim that the numbers describe LignaTech.

## 7. Limitations

- Three participants from one company give an indication of relevance, not a representative survey.
- The company works mainly with doors, while the model of the project is a furniture line. The process stages (cutting, edge work, drilling, painting, assembly) are similar, but the model is not calibrated to this company.
- The customer's answers describe one order.
- The answers are opinions and memories of the participants and were not checked against company data.
- We did not ask about prices or any personal data.
