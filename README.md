# Development of an Intelligent Order Management System with Digital Twin Integration for Furniture Manufacturing

Diploma project, Software Engineering

Zhannur Meirambek, Ayazhan Orynbasar, group SE-2412.

## Problem
Customized furniture orders combine many dimensions, materials, components and fittings, so each order is effectively a small engineering task. The delivery date is usually promised in the showroom before anyone has checked factory capacity and material availability. This leads to missed deadlines, rescheduling and expediting.

## Goal
Design and evaluate a system that takes a structured showroom order and, using a simulation-based digital twin of the factory together with material-availability data, returns a delivery-date commitment at order acceptance. Its accuracy is compared with two baseline methods:
- **B1**: average historical lead time plus a fixed buffer (no capacity check)
- **B2**: static capacity check without factory feedback

## Target users
Showroom managers and production planners of small and medium make-to-order furniture manufacturers.

## Expected results
- Prototype: manager web interface, backend API, digital twin
- Factory emulator that provides the "actual" completion dates for evaluation
- Reproducible experiments comparing the twin with B1 and B2 (MAE, on-time share, Wilcoxon test)
- Final article

## Scope
Included: structured digital order, order validation, digital-twin-based delivery-date estimation, minimal manager interface, evaluation on synthetic data.
Not included: pricing, engineering design automation, shop-floor schedule optimisation, deployment in a live factory. The twin is simulation-based and is not connected to physical machines.

## Team
| Member | Responsibility |
|---|---|
| Zhannur Meirambek | Digital twin, statistical evaluation, manager web interface, order schema |
| Ayazhan Orynbasar | Factory emulator, synthetic order generator, baselines B1/B2, experiment runner, backend API and database |
| Both | Requirements, architecture and diagrams, verification plan, final article |

Supervisor: Shyryn Tutkyshbayeva

## Planned technologies
Python, SimPy, FastAPI, PostgreSQL, React/TypeScript, Docker. The final choice is justified in `docs/`.

## Repository structure
- `docs/` research documents, comparisons, requirements, decisions
- `diagrams/` architecture diagrams (sources and exports)
- `backend/` API and database
- `frontend/` manager interface
- `twin/` digital twin
- `emulator/` factory emulator
- `experiments/` evaluation scripts
- `config/` configuration examples (placeholder values only)

## Status
Analysis and design stage. Setup and test instructions will be added when code appears.

## Links
- YouTrack: https://furniture-dt.youtrack.cloud/projects/DIP
- Documentation: `docs/`