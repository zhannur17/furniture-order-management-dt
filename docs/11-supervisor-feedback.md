# Supervisor Feedback

**Authors:** Zhannur Meirambek, Ayazhan Orynbasar

## 1. Purpose

This document records what our supervisor said about the key materials and what we decided to do about each comment.

## 2. What Was Sent and When

| Item | Detail |
|---|---|
| Materials sent | Proposal, literature review, comparisons, requirements, architecture and diagrams, mockups, verification plan, presentation |
| Date sent | 20 October 2026 |
| Feedback received | 24 October 2026 |

## 3. Comments and Decisions

| # | Comment | Decision | What we do |
|---|---|---|---|
| 1 | Collect a dataset and define it by features and categories | **Accepted** | We will build a synthetic dataset of orders and describe its features and categories in the data section of the verification plan. Order features: product type, dimensions, material, finish, quantity, options. Factory features: queue and utilisation of stations, material stock. Target: actual completion date from the emulator. |
| 2 | Find machine learning and deep learning models | **Accepted in part** | We will add a short review of ML and deep learning models for lead-time prediction. If time allows, we will add one simple ML baseline (B3), for example gradient boosting. We will not train a deep learning model: we only have synthetic data, so a neural network would learn our own generator and show nothing about real accuracy. |

## 4. Next Steps

| Step | Who | When |
|---|---|---|
| Add the dataset description to the verification plan | Ayazhan | Before the order generator is built |
| Write the review of ML and deep learning models | Zhannur | Before the second pre-defense |
| Decide about baseline B3 and update the verification plan | Both | After the first working version of the twin |
