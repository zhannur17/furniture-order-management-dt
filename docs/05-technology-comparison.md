# Technology Comparison

**Author:** Zhannur Meirambek

## 1. Purpose

This document describes which technologies we selected for this project. For each technical choice we analyze two or three practical alternatives and evaluate them against the requirements of the project ([06-requirements.md](06-requirements.md)). The tools were not chosen based on their popularity; we chose those that help solve the particular problem of the system: taking custom furniture orders, simulating the factory so that we can return a range of dates for delivery along with their reasons in an environment that may be utilized anywhere.

## 2. Decisions Overview

| # | Decision | Choice | Alternatives considered |
|---|---|---|---|
| D1 | Backend framework | FastAPI (Python) | Django REST Framework, Flask |
| D2 | Database | PostgreSQL (with SQLAlchemy) | SQLite, MongoDB |
| D3 | Simulation engine for the digital twin | SimPy (Python) | AnyLogic, Salabim |
| D4 | Frontend | React with TypeScript and Vite | Vue 3, server-rendered pages (Jinja2 with HTMX) |

Supporting tools that we use without a separate comparison: Docker Compose (one-command start, NFR-06), pytest and GitHub Actions (tests and checks, NFR-05), and Git with GitHub and YouTrack for project management.

## 3. Requirements That Drive the Choice

The decisions below refer to these requirements from [06-requirements.md](06-requirements.md).

| ID | Requirement in short |
|---|---|
| FR-02, NFR-03 | Validate every order; invalid input must never cause a server error |
| FR-03 | Store each order as a structured JSON digital order |
| FR-09, FR-13 | Simulate the production route with random times and breakdowns, run Monte Carlo experiments in bulk |
| NFR-01 | An estimate for one order in 10 seconds or less (about 200 Monte Carlo runs) |
| NFR-02 | A manager can enter and confirm an order in under 3 minutes, using at most 5 screens |
| NFR-04 | Experiments are reproducible: fixed random seeds, one command |
| NFR-05 | Core modules covered by automated tests (at least 70%) |
| NFR-06 | The whole system starts with `docker compose up` |

## 4. D1: Backend Framework

**Context.** The backend receives an order, validates it, calls the digital twin and returns the estimate. It also exposes the API that the interface and the experiments use.

| Criterion | FastAPI | Django REST Framework | Flask |
|---|---|---|---|
| Automatic input validation (FR-02, NFR-03) | Yes: request models are validated automatically | Yes: through serializers | Partly: needs an extra library |
| Automatic API documentation for examples and testing | Yes: OpenAPI page is generated | Partly: needs an extra package | No: needs an extra package |
| Same language as the simulation (Python) | Yes | Yes | Yes |
| Weight of the framework for a small API | Light | Heavy: full web framework with its own ORM and admin | Light |
| Fit for a typed JSON order schema (FR-03) | Strong: schema is written once as a model | Medium | Medium |

**Choice: FastAPI.** The order schema embedded in the requirements can be formulated in one go as a typed model, after which FastAPI performs the necessary input verification, denies incorrect data with the corresponding message, and prepares the API documentation. This approach successfully deals with the issues of FR-02, FR-03, and NFR-03 practically without writing any additional code, not to mention that the API page generated during this process may serve as the “API examples” for the prototype. Thanks to its integration with Python, the backend achieves direct access to the simulation. Django REST Framework would be suitable too, yet its excessive functionality includes many features we will hardly need (which is a templating engine, an administrator panel, and its own ORM). Flask is easy to use but requires creating the validation and documentation features manually.


**Trade-off.** FastAPI is younger than Django and has fewer built-in features (no admin site, no user management). Our project needs none of them.

## 5. D2: Database

**Context.** We store orders (with the JSON digital order), the factory state used by the twin, and the results of experiments.

| Criterion | PostgreSQL | SQLite | MongoDB |
|---|---|---|---|
| Store the JSON digital order and still query it (FR-03) | Yes: JSON column type | Partly: JSON support is limited | Yes: documents are JSON |
| Relations between orders, stations and results | Yes | Yes | Partly: no joins in the usual sense |
| Several clients at once (backend and experiment runner) | Yes | Partly: one writer at a time | Yes |
| Runs in Docker Compose without extra effort (NFR-06) | Yes: official image | Yes: it is just a file | Yes: official image |
| Works with the chosen backend stack (SQLAlchemy) | Yes | Yes | Needs a different library |

**Choice: PostgreSQL with SQLAlchemy.** An order consists of fixed fields, such as customer data and dates, along with flexible fields that provide added details. Therefore, PostgreSQL is employed because it offers a good balance between normalization, where fixed data is stored in regular columns, and making use of the JSON column to store the digital order. PostgreSQL also allows for writing data to the database from both the backend and the experiment runner at the same time. SQLite may be the easiest solution. However, it only permits single process writing, which could be a problem. Even though MongoDB works well with the JSON orders, our data presents a good set of relations that would be more easily managed with relational databases.

**Trade-off.** PostgreSQL needs a separate container, which adds a little to the setup. Docker Compose hides this cost.

## 6. D3: Simulation Engine for the Digital Twin

**Context.** The twin is a discrete-event simulation of the production line (panel cutting, edge banding, drilling, CNC, painting, staging). It must use random processing times and breakdowns and be repeated many times (Monte Carlo) for every order, and the same code must also run in large experiments.

| Criterion | SimPy | AnyLogic | Salabim |
|---|---|---|---|
| Discrete-event simulation with queues and shared resources (FR-09) | Yes | Yes | Yes |
| Runs inside the backend process and can be called as a function (FR-10) | Yes: it is a Python library | Partly: separate tool, needs to be exported and wrapped | Yes: Python library |
| Scripted batch runs with fixed seeds (FR-13, NFR-04) | Yes | Partly: possible, but more work to automate | Yes |
| Works in Docker without a licensed desktop tool (NFR-06) | Yes | No: commercial desktop tool, free edition is limited | Yes |
| Cost | Free, open source | Commercial licence | Free, open source |
| Size of community and examples | Large | Large | Smaller |

**Choice: SimPy.** The twin must function as a backend component that takes in a request and a factory state before proceeding to generate a distribution of completion dates. If using SimPy, there would be nothing but Python code to handle this, which means the backend can call it directly, the experiment runner can repeat execution millions of times with fixed random numbers and tests can be executed with pytest. The entire process is open source and works in a container. AnyLogic has good visuals, but as it is a commercial software product, setting up an API that would handle every order would involve a lot of work. Salabim also uses Python and could be a suitable solution, however, since SimPy has a bigger community and lots of examples, using it is less risky given the short deadlines of the project.

**Trade-off.** SimPy has no graphical editor or animation. We accept this because the twin's result is shown as dates and reasons in the manager interface, and we do not need to watch a moving model.

**Performance note.** NFR-01 (10 seconds for about 200 runs) is a risk for any Python simulation. We plan to check it early with a first prototype of the twin and, if needed, reduce the model detail or the number of runs.

## 7. D4: Frontend

**Context.** The manager interface is minimal: about five screens (new order, estimate result, order list, order details, factory status). It talks to the backend only through the API.

| Criterion | React + TypeScript + Vite | Vue 3 | Server-rendered pages (Jinja2 + HTMX) |
|---|---|---|---|
| Typed contract with the API (fewer mismatches with the order schema) | Yes: types can be generated from the API description | Yes: with TypeScript | No |
| Interactive forms and result views (FR-01, FR-04, FR-05) | Yes | Yes | Partly: limited for richer forms |
| Easy to separate from the backend (own container) | Yes | Yes | No: tied to the backend |
| Amount of ready components and examples | Very large | Large | Small |
| Setup effort | Medium | Medium | Low |

**Choice: React with TypeScript and Vite.** The order form containing items, options and result view that includes date range and reasons are interactive enough to be able to utilize component framework. With TypeScript we can ensure that our interface corresponds to the ordering schema, so if it changes we understand right away where our interface breaks. Vite gives us a fast development environment. Vue 3 would be an appropriate option, too, but there isn’t a big distinction. We went with React for the sake of more examples and component libraries. Server-rendered pages would be the fastest option for building, but it would make the interface too tightly coupled with backend which is not suitable for the dynamic forms.

**Trade-off.** React with TypeScript has more initial setup than server-rendered pages. We limit this by keeping the interface to five screens and by using a ready component library.

## 8. How the Choices Fit Together

```
Manager (browser)
      |  HTTP/JSON
React + TypeScript (frontend)
      |  REST API (OpenAPI)
FastAPI (backend)  ---- SQLAlchemy ---->  PostgreSQL
      |  Python function call
SimPy digital twin  <----  factory state, order
```

All parts except the frontend are Python, which keeps the call from the API to the twin a normal function call and allows the same code to be used by the experiment runner. The frontend is separated and communicates only through the API. All services start with one `docker compose up`.

## 9. Risks and When We Would Reconsider

| Risk | What we would do |
|---|---|
| The twin is too slow for 200 runs in 10 seconds (NFR-01) | Reduce model detail or runs, run replications in parallel, or cache the factory state |
| FastAPI or React turns out too heavy for the time available | Keep the frontend to the five main screens; use plain templates for the least important ones |
| PostgreSQL setup problems on a team member's computer | Use the Docker Compose service only, no local install |

## 10. Limitations of This Comparison

- The comparison is based on the features of each tool and on our requirements. We did not build the same prototype in every alternative.
- The performance requirement (NFR-01) is not yet measured; it will be checked on the first version of the twin.
- Alternatives were chosen as realistic options for a small student project, not as a complete market survey.

## References

[1] FastAPI documentation. https://fastapi.tiangolo.com

[2] Django REST Framework documentation. https://www.django-rest-framework.org

[3] Flask documentation. https://flask.palletsprojects.com

[4] PostgreSQL documentation. https://www.postgresql.org/docs/

[5] SQLite documentation. https://www.sqlite.org/docs.html

[6] MongoDB documentation. https://www.mongodb.com/docs/

[7] SimPy documentation. https://simpy.readthedocs.io

[8] AnyLogic. https://www.anylogic.com

[9] Salabim documentation. https://www.salabim.org

[10] React documentation. https://react.dev

[11] Vue.js documentation. https://vuejs.org

[12] htmx documentation. https://htmx.org