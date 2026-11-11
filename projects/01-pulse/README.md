# Project 1: Pulse (Weeks 1–5)

**Brief:** Transit riders churn when buses are late. Product wants a feature that warns riders when a stop is likely to be **more than 5 minutes late** and estimates the delay.

**Data:** [MBTA V3 API](https://api-v3.mbta.com/) (free key): predictions, schedules, vehicles.

## Deliverables
- [ ] `SPEC.md`: problem framing, target definition, success metric tied to the business goal, a baseline (W1)
- [ ] `CLAUDE.md` for this project (W1)
- [ ] `ingest/`: API → Pydantic validation → PostgreSQL `stop_events`, with idempotent upserts and a test that proves re-runs add no duplicates (W2)
- [ ] Regression (delay minutes) and classification (late?) in scikit-learn pipelines, compared against baselines (W3)
- [ ] ROC/PR curves, a chosen threshold, class imbalance handled, every run in MLflow (W4)
- [ ] PyTorch MLP comparison, plus `RESULTS.md` with the winner and why (W5)

## Done when
`docker compose up db && python -m ingest && python -m train` works from a clean clone, and the numbers in `RESULTS.md` match the runs in MLflow.
