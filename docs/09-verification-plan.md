# Verification and Evaluation Plan

**Author:** Ayazhan Orynbasar

## 1. Purpose

This plan describes how we will check that the system works and how we will test the research hypotheses. It fixes the baseline methods, the metrics, the experiment conditions and the statistical tests before any experiment is run, so that the results cannot be tuned to look good afterwards.

The research hypotheses are:

- **H1.** The mean absolute deviation between the committed and the actual completion date is smaller for the proposed system than for each baseline (B1 and B2).
- **H2.** A larger share of orders is completed by the committed date under the proposed system than under each baseline.

Related documents: [06-requirements.md](06-requirements.md) (requirements FR-11 to FR-16 and NFR-04), [07-architecture.md](07-architecture.md) (components: digital twin, emulator, baselines, experiment runner).

## 2. What Is Verified

| Level | Question | How |
|---|---|---|
| Components | Does each part work as specified? | Unit and API tests (pytest), run in GitHub Actions |
| Digital twin | Is the model reasonable and stable? | Calibration against the emulator, sensitivity analysis, review of assumptions |
| Whole system | Can a manager enter an order and get an estimate in time? | End-to-end test, timing test, walkthrough with testers |
| Research hypotheses | Is the twin estimate more accurate than B1 and B2? | Controlled simulation experiment and statistical tests (Sections 4 to 8) |

## 3. Notation

For each order *i* in an experiment:

| Symbol | Meaning |
|---|---|
| *t<sub>i</sub>* | Day when the order is accepted |
| *A<sub>i</sub>* | Actual completion day, produced by the factory emulator |
| *Ê<sub>i</sub>* | Committed (estimated) completion day produced by a method |
| *e<sub>i</sub>* = *Ê<sub>i</sub>* − *A<sub>i</sub>* | Signed error in days. Positive means the commitment is later than the actual date, negative means the order is late |
| *L<sub>i</sub>* = *A<sub>i</sub>* − *t<sub>i</sub>* | Actual lead time in days (at least 1) |
| *n* | Number of orders in the sample |

Days are counted in working days of the factory calendar. All methods are evaluated on the same orders and compare their *Ê<sub>i</sub>* to the same *A<sub>i</sub>*.

## 4. The Compared Methods

### 4.1 Proposed method: digital twin

For an order accepted on day *t<sub>i</sub>*, the twin runs *R* = 200 Monte Carlo simulations starting from the current factory state (queues, orders in progress, machine states, material stock). Each run gives a completion day *S<sub>i,1</sub>, …, S<sub>i,R</sub>*.

The committed date is a quantile of this distribution:

*Ê<sub>i</sub><sup>twin</sup>* = ⌈ *Q<sub>q</sub>*( *S<sub>i,1</sub>, …, S<sub>i,R</sub>* ) ⌉, with *q* = 0.80 as the default

The value *q* = 0.80 means that the twin commits to a date that 80% of the simulated runs meet. The estimate also reports the earliest (5th percentile), most likely (median) and latest (95th percentile) dates to the manager. The choice of *q* is part of the sensitivity analysis (Section 9).

### 4.2 Baseline B1: average lead time plus a fixed buffer

B1 imitates a manager who promises the typical lead time and adds a safety margin. It does not look at the capacity or at the order.

*Ê<sub>i</sub><sup>B1</sup>* = *t<sub>i</sub>* + ⌈ *L̄* + *b* ⌉

where

- *L̄* = (1 / *m*) · Σ *L<sub>j</sub>*, the mean actual lead time of *m* completed historical orders from a separate history sample (not from the orders being evaluated),
- *b* = 0.20 · *L̄*, a fixed buffer of 20% of the mean lead time.

B1 gives the same lead time for every order in a scenario.

### 4.3 Baseline B2: static capacity check without feedback

B2 imitates a planner who checks the nominal capacity of the stations against the order book, but ignores random variation and does not use the actual state of the shop floor.

Let the route of the order have stations *k* = 1, …, *K* in production order. For each station:

- *h<sub>ik</sub>* = nominal (mean) processing hours of the order at station *k* (mean time per unit × quantity),
- *c<sub>k</sub>* = nominal capacity of station *k* in hours per working day (shifts × machines, without breakdowns),
- *W<sub>k</sub>* = hours of work for station *k* already planned in the order book at the moment of acceptance (sum of nominal hours of accepted, not yet finished orders). It is taken from the order book, not measured on the shop floor.

The completion time at each station, in working days from acceptance, is:

*F<sub>0</sub>* = 0

*F<sub>k</sub>* = max( *F<sub>k−1</sub>* , *W<sub>k</sub>* / *c<sub>k</sub>* ) + *h<sub>ik</sub>* / *c<sub>k</sub>*, for *k* = 1, …, *K*

*Ê<sub>i</sub><sup>B2</sup>* = *t<sub>i</sub>* + ⌈ *F<sub>K</sub>* ⌉

In words: the order reaches station *k* when it has finished the previous station, but it can start only after the planned backlog *W<sub>k</sub>* of that station has been worked off at capacity *c<sub>k</sub>*; then it needs its own processing time.

Example with three stations: *W* = (4, 6, 2) hours, *c* = (8, 8, 8) hours per day, *h* = (4, 2, 4) hours. Then *F<sub>1</sub>* = max(0, 0.5) + 0.5 = 1.0; *F<sub>2</sub>* = max(1.0, 0.75) + 0.25 = 1.25; *F<sub>3</sub>* = max(1.25, 0.25) + 0.5 = 1.75; *Ê* = *t* + 2 days.

B2 has no feedback: *W<sub>k</sub>* is not corrected by actual breakdowns, delays or the current queue lengths, and the processing times have no variation. This is exactly what the twin adds.

### 4.4 Fairness rules

- All three methods use the same order, the same route and the same nominal processing data.
- B1 uses only history; B2 uses only the order book; the twin uses the current factory state.
- The twin never sees the emulator's code, parameters or random numbers.
- All parameters (*q*, *b*, *R*) are fixed in a configuration file before the final run and are not tuned on the evaluation orders.

## 5. Metrics

All metrics are computed for each method in each scenario and replication (Section 6).

| Metric | Formula | Reading |
|---|---|---|
| **MAE** (mean absolute error), days | (1/*n*) · Σ \|*e<sub>i</sub>*\| | Average size of the miss. Smaller is better. This metric is used for H1 |
| **MAPE**, % | (100/*n*) · Σ \|*e<sub>i</sub>*\| / *L<sub>i</sub>* | Error relative to the actual lead time. Smaller is better |
| **Bias**, days | (1/*n*) · Σ *e<sub>i</sub>* | Systematic direction of the error. Positive means too late and cautious, negative means too optimistic. Close to 0 is better |
| **On-time share** | (1/*n*) · Σ **1**[ *A<sub>i</sub>* ≤ *Ê<sub>i</sub>* ] | Share of orders finished on or before the commitment. Larger is better. This metric is used for H2 |
| **Estimation time**, seconds | Wall-clock time to produce the estimate for one order (mean and 95th percentile) | Practical usability. The target is at most 10 seconds (NFR-01) |

The metrics have to be read together. A method can reach a high on-time share only by promising very late dates; this shows up as a large MAE and a large positive bias. H1 and H2 together protect against this.

## 6. Experiment Conditions

### 6.1 Factors

| Factor | Levels |
|---|---|
| Load level | Low, medium, high. Target average utilisation of the bottleneck station: 70%, 85%, 95% |
| Disturbance setting | Normal, high |

Together there are 3 × 2 = **6 scenarios**.

Initial parameter values (documented in the configuration file and fixed before the final run):

| Parameter | Normal | High |
|---|---|---|
| Machine breakdowns | about 1 per 200 working hours per machine, mean repair 3 hours | twice as frequent, mean repair 4.5 hours |
| Variation of processing time (coefficient of variation) | 0.15 | 0.30 |
| Probability that a material delivery is late | 5% | 15% |

### 6.2 Size and structure

- **Replications:** about 30 independent replications per scenario. Each replication uses its own random seed.
- **Orders:** about 200 orders per replication, generated by the order generator from the product catalog (types, dimensions, materials, finishes, quantities). Arrival times follow a random process fitted to the target load level.
- **Warm-up:** the first 20 working days of every replication are used only to fill the factory and are not evaluated.
- **History sample for B1:** *m* = 100 orders from a separate run under the same scenario.
- **Paired design:** inside a replication, the twin, B1 and B2 estimate the same orders, and the emulator provides one actual date for each order. This is a paired design with common random numbers.

Total evaluated sample: 6 scenarios × 30 replications × about 200 orders ≈ 36,000 orders per method.

### 6.3 Data

No real factory data are available, so all data are synthetic. The generator assumptions (distributions, processing times, shifts, material lead times) are documented in the repository and are based on the literature and on the interviews with practitioners where possible. Results apply to the simulated setting.

### 6.4 Independence of the "actual" dates

The actual completion date *A<sub>i</sub>* is produced by the factory emulator, which is a separate program with its own implementation and random streams, and with more detail than the twin (for example shift handling and rework). Without this separation the twin would be tested against its own logic and the comparison would be meaningless.

### 6.5 Reproducibility

Every run is defined by the scenario, the replication number and the seed, and is started with one command. The same seeds give the same results (NFR-04).

## 7. Statistical Analysis

### 7.1 Unit of analysis

The orders inside one replication are not independent of each other (they share the same factory). Therefore the unit of analysis is the **replication**: for each method and each replication, we compute one value of each metric. For a scenario this gives 30 paired values per comparison.

### 7.2 Comparisons and tests

For every scenario we compare the twin with B1 and with B2 (two comparisons per hypothesis).

- **For H1:** the paired difference in MAE per replication, *d<sub>r</sub>* = MAE<sub>baseline,r</sub> − MAE<sub>twin,r</sub>. Hypothesis tested: the median of *d<sub>r</sub>* is greater than 0 (twin is better).
- **For H2:** the paired difference in on-time share per replication, *d<sub>r</sub>* = on-time<sub>twin,r</sub> − on-time<sub>baseline,r</sub>. Hypothesis tested: the median of *d<sub>r</sub>* is greater than 0 (twin is better).
- **Test:** the one-sided **Wilcoxon signed-rank test** on the 30 paired differences, with significance level α = 0.05. It is used because the differences cannot be assumed to be normally distributed. Zero differences are dropped, as the standard method does.
- **Effect size:** the matched-pairs rank-biserial correlation *r* = (*W*<sup>+</sup> − *W*<sup>−</sup>) / (*W*<sup>+</sup> + *W*<sup>−</sup>), together with the median paired difference and its 95% bootstrap confidence interval.

### 7.3 Multiple comparisons: Holm correction

We run 6 scenarios × 2 baselines × 2 hypotheses = **24 tests**. To keep the overall error rate at α = 0.05, the p-values are corrected with the **Holm step-down procedure**:

1. Sort the *m* = 24 p-values: *p*<sub>(1)</sub> ≤ *p*<sub>(2)</sub> ≤ … ≤ *p*<sub>(m)</sub>.
2. Starting with *j* = 1, reject the null hypothesis of test (*j*) if *p*<sub>(j)</sub> ≤ α / (*m* − *j* + 1).
3. Stop at the first test that is not rejected; all following tests are also not rejected.

Both the raw and the Holm-adjusted p-values are reported.

### 7.4 Decision rule (fixed in advance)

- H1 (or H2) is considered **supported in a scenario** if the Holm-adjusted p-value is below 0.05 against both baselines.
- H1 (or H2) is considered **supported overall** if it is supported in at least 4 of the 6 scenarios.
- If the twin is not better in some scenarios (for example, when the load is low and B2 is already accurate), this is reported and discussed. It is not hidden.

### 7.5 Tools

Python with `scipy.stats.wilcoxon` for the test, `statsmodels.stats.multitest.multipletests(method="holm")` for the correction, and `pandas` for the tables. One command reproduces all tables from the raw results (FR-16).

## 8. Outputs

| Output | Content |
|---|---|
| `results/orders.csv` | One row per order and method: estimate, actual date, error, on-time flag, estimation time |
| `results/replications.csv` | One row per scenario, replication and method: MAE, MAPE, bias, on-time share |
| `results/summary.csv` | Mean and standard deviation of every metric per scenario and method |
| `results/tests.csv` | Raw and Holm-adjusted p-values, effect sizes, confidence intervals |
| Figures | Box plots of MAE and bias per scenario; on-time share per scenario; error distributions |

## 9. Sensitivity and Verification of the Model

| Check | What is varied or tested | What we look for |
|---|---|---|
| Calibration | Twin against the emulator without disturbances | Bias close to zero; if not, the twin model is wrong |
| Commitment quantile | *q* = 0.5, 0.8, 0.9 | How the trade-off between MAE and on-time share changes |
| Accuracy of inputs | Processing times and supplier lead times known with ±20% error | How robust the twin is to imperfect data |
| Number of runs | *R* = 50, 100, 200, 400 | Whether 200 runs are enough for a stable estimate and how long they take |
| Buffer of B1 | *b* = 10%, 20%, 30% | That the result does not depend on a weak baseline |
| Face validity | Short review of the model assumptions and typical outputs with practitioners | That the stations, routes and delays look plausible |

The buffer check is important: if B1 were given an unreasonable buffer, H2 would be easy to support. We therefore report B1 with several buffers.

## 10. Verification of the Software

| Requirement | Test |
|---|---|
| FR-02, NFR-03 | API tests with valid and invalid orders; invalid input returns 4xx and never a server error |
| FR-03 | An order stored and read back is unchanged |
| FR-04, FR-05 | The estimate has three dates, a probability and at least one reason |
| FR-09, FR-10 | The twin finishes every test order; results change when load or breakdown settings change |
| FR-11 | B1 and B2 reproduce hand-calculated values for small examples (including the example in Section 4.3) |
| FR-12 | The emulator gives repeatable actual dates for the same seed |
| FR-14 | Metric functions give known values for small hand-made data sets |
| NFR-01 | Timing test: 95% of estimates are returned in 10 seconds or less |
| NFR-04 | Running the same experiment twice gives identical result files |
| NFR-06 | Clean start with `docker compose up` on a new machine |

The unit-test coverage target for core modules is 70% (NFR-05). Tests run automatically on every pull request.

## 11. Threats to Validity and Limitations

- **Synthetic data.** The results show how the methods compare in the simulated factory, not in a real one. Generator parameters could favour one method; to limit this, they are fixed before the run and published.
- **Twin and emulator share assumptions.** Although they are separate programs, the same author team builds both and they model the same kind of factory. The emulator is therefore more detailed and uses its own random streams, but it cannot remove this risk completely.
- **Baselines are simple.** B1 and B2 are simple rules. A better planning tool might perform better than B2; we state this and do not claim superiority over all existing tools.
- **One product family and one factory layout.** Six stations and one family of products are modelled.
- **Choice of the commitment quantile.** The twin's result depends on *q*; this is why it is analysed separately.
- **Human decision.** The system supports the manager and does not decide for them. The experiment measures the accuracy of the commitment, not the business result.
- **Limited usability testing.** The usability requirement (NFR-02) is checked with a small number of testers.

## 12. Schedule and Responsibility

| Step | Who | When |
|---|---|---|
| Fix parameters and write the configuration | Ayazhan and Zhannur | Before the first run |
| Emulator, order generator, B1, B2 and experiment runner | Ayazhan | Weeks 13–14 of the project plan |
| Digital twin | Zhannur | Before the experiments |
| Statistical analysis and figures | Zhannur | After the final run |
| Review of this plan | Zhannur (pull request review) | Before the experiments |
