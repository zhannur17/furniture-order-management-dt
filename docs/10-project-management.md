# Project Management Plan

**Author:** Ayazhan Orynbasar

## 1. Purpose

This document outlines who will be doing work for various tasks on a project, how the main phases of the plan will be, the issues that might occur, dependencies between different tasks. We consider it the working plan. Whenever something changes, we update the document.

## 2. Project Links

| What | Link |
|---|---|
| Repository | https://github.com/zhannur17/furniture-order-management-dt |
| YouTrack project (all tasks) | https://furniture-dt.youtrack.cloud/issues?q=project:%20DIP |
| YouTrack board | https://furniture-dt.youtrack.cloud/agiles/204-1/current |
| Documents | folder `docs/` in the repository |
| Interface mockups | folder `docs/mockups/` (the Figma link is in its README) |

## 3. Team and Responsibilities

There are two of us in the team. Every task in YouTrack has one person who does it. She writes the files and makes the commits from her own account. The other person checks the pull request and merges it. Nobody merges her own pull request.

| Member | What she is responsible for | What she has done so far | What she will do next |
|---|---|---|---|
| Zhannur Meirambek | Requirements, architecture, digital twin, frontend, statistics | Literature review of original articles, proposal, technology comparison, requirements, architecture with component diagram, interface mockups | Digital twin in SimPy, Monte Carlo runs, manager web interface, statistical analysis |
| Ayazhan Orynbasar | Backend, emulator, experiments, project plan | Literature review of review articles, comparison of existing systems, context and use case diagrams, API examples, verification plan, this plan | Backend and database, factory emulator, order generator, baselines B1 and B2, experiment runner, Docker Compose |

Some things we do together:

- We both write the report and keep it up to date, and both prepare for the defense.
- We both keep YouTrack up to date: the stage, the due date and the link to the pull request.
- We send updates to the supervisor and write down her feedback in `docs/11-supervisor-feedback.md`.

### 3.1 How we work

| Rule | What it means for us |
|---|---|
| One task, one person | The person assigned to the task does it and makes the commits |
| One branch for each task | The branch is called `DIP-N-short-name` and the commit messages start with `DIP-N:` |
| Check before merge | The other person looks at the pull request, compares it with the acceptance criteria and then merges |
| Link to the work | The link to the pull request is added as a comment to the task, and after the merge the task goes to Done |
| Main branch works | Only checked work goes to `main`. When we have code, tests run on every pull request |
| Tags | Every submission gets its own tag (`pre-defense-1`, `pre-defense-2`, `final-pre-defense`). We do not move a tag after it is made |

## 4. Main Phases and Dates

The first date is fixed by the deadline. The other dates follow the weekly plan from the project proposal, where week 1 starts on 2 October 2026 and every week runs from Friday to Thursday. We will change the dates if the official schedule of the department is different.

| # | Phase | Date | What should be ready |
|---|---|---|---|
| M1 | First pre-defense submission (tag `pre-defense-1`) | 24 Oct 2026 | Proposal, evidence of relevance, literature review, system and technology comparison, requirements, architecture, API examples and mockups, verification plan, this plan, supervisor feedback, report and YouTrack screenshots |
| M2 | Digital twin, first version (weeks 9–11) | 17 Dec 2026 | Model of the production line, Monte Carlo runs, first check of the 10 seconds limit (NFR-01) |
| M3 | Factory emulator and order generator (weeks 9–11) | 17 Dec 2026 | Emulator that is separate from the twin, generator of synthetic orders |
| M4 | Backend, database and manager interface (weeks 9–12) | 24 Dec 2026 | Order check, saving orders, endpoints for orders, catalog and factory status, tests for the main parts, five screens connected to the API |
| M5 | Second pre-defense submission (tag `pre-defense-2`) | Date from the department | The system works from the interface to the twin, first experiment on one scenario, updated report |
| M6 | Baselines, experiments and statistics (weeks 13–14) | 7 Jan 2027 | B1 and B2, experiment runner, 6 scenarios with about 30 replications, metrics, Wilcoxon tests with Holm correction, tables and plots |
| M7 | Article (week 15) | 14 Jan 2027 | Text of the article with the results |
| M8 | Final pre-defense submission (tag `final-pre-defense`) | Date from the department | Finished system, results of the experiments, final report, limitations and conclusions |
| M9 | Final defense | Date from the department | Presentation and demo |

After the first submission we keep working in the same repository. The tags we already submitted stay where they are.

## 5. Dependencies Between Tasks

| Task | Needs first | Why |
|---|---|---|
| Architecture and diagrams | Requirements | The components come from the requirements |
| API examples and mockups | Requirements, architecture | The fields and screens follow the digital order |
| Verification plan | Requirements | The metrics and scenarios must fit the research question |
| Backend | Architecture, API examples | The endpoints and the error format are described there |
| Digital twin | Requirements, assumptions about the factory | We must decide the stations and the route before modelling |
| Estimation in the backend | Backend, digital twin | It calls the twin for every estimate |
| Factory emulator | Assumptions about the factory | It has the same stations, but with more detail and without using the twin |
| Baselines B1 and B2 | Verification plan | The formulas are fixed there |
| Experiment runner | Twin, emulator, baselines | It runs all of them on the same orders |
| Statistical analysis | Experiment runner | We need the results of the experiments |
| Manager interface | Backend, mockups | It uses the API and follows the screens |
| Final report | Everything above | It contains the results, limitations and conclusions |

The longest chain is: requirements, architecture, twin, emulator, experiment runner, statistics, final report. If the twin or the emulator is late, everything after them is late too. So we do these two before the interface.

## 6. Risks

Likelihood and impact are Low, Medium or High.

| # | Risk | Likelihood | Impact | What we will do | Who |
|---|---|---|---|---|---|
| R1 | **No real factory data.** We do not have data from a real furniture factory, so processing times and breakdowns are assumptions | High | High | Write the assumptions down in the model and in the report, take values from the literature, test several values, and say clearly that the result is for a simulated factory | Both |
| R2 | **Gap between twin and reality.** The emulator is not a real factory, so results may be different in real life | High | Medium | Make the emulator separate from the twin, with more detail and its own random numbers. Write this in the limitations and do not claim results for real factories | Zhannur |
| R3 | **Too much work.** We are two people with little time, and we need both documents and a working system | High | High | Keep the project small (one product family, six stations, five screens), do the main chain first, keep the interface simple and check the plan every week | Both |
| R4 | **The twin is too slow.** About 200 runs may take more than 10 seconds (NFR-01) | Medium | Medium | Measure it on the first version, make the model simpler or use fewer runs, run replications in parallel | Zhannur |
| R5 | **The twin is not better than the baselines.** H1 and H2 may not be confirmed | Medium | Medium | Report the result as it is and look at where and why the twin helps or does not. The metrics and tests are fixed in advance, so we cannot change them after seeing the results | Both |
| R6 | **Someone is ill or not available** | Medium | High | Everything is in the repository, so the other person can continue. The tasks in YouTrack have acceptance criteria | Both |
| R7 | **Parts do not work together** (backend, twin, emulator, interface) | Medium | Medium | Use one order format, agree on the API examples early, and run everything with Docker Compose from the first working version | Ayazhan |
| R8 | **Mistakes in the statistics** | Low | High | Follow the verification plan, use fixed seeds, and the other person checks the scripts and the tables | Zhannur |
| R9 | **Supervisor feedback comes late** and we must change things just before a deadline | Medium | Medium | Send results early and often, and write down the questions and answers | Both |

## 7. How We Keep Track

| What | When | How |
|---|---|---|
| Status of tasks | All the time | YouTrack board, with the stage and the due date up to date |
| Short meeting | Every week | What is done, what is stuck, what is next, and we look at the risks again |
| Update for the supervisor | Before each submission and when we have a result | Short message with links, answers are written down |
| Quality check | For every pull request | The other person compares the work with the acceptance criteria |
| Changing the plan | When a date is missed or a risk happens | We change this file with a pull request |

## 8. Limitations

- The dates after M1 come from the weekly plan in the proposal. They depend on the official schedule and on how fast we can build the twin. The weeks 9–14 are close to the holidays, so we may lose some working days.
- The plan assumes that both of us work at the same time. If one of us is away for a long time, we will have to make the project smaller.
- We do not count hours. We follow the progress by tasks that are finished and checked.
