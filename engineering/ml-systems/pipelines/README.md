# ML Pipelines

ML pipelines are the infrastructure that takes raw data and turns it into features, models, and predictions — reliably, repeatably, and at scale. This track covers feature engineering systems, data versioning, and pipeline orchestration as practiced in production ML teams.

---

## Goal

By the end of this track you will be able to:
- Design and build feature pipelines that are testable, versioned, and reusable
- Understand the architecture of a feature store and when you need one
- Build and orchestrate multi-step ML pipelines with dependency management
- Apply software engineering best practices (testing, versioning, observability) to data and ML workflows

---

## Prerequisites

- Python proficiency, including dataclasses and type hints
- Basic familiarity with Pandas and NumPy
- Exposure to SQL (basic SELECT, GROUP BY)
- Docker basics (will be used for running orchestration tools)

---

## Learning Path

### 1. Data Engineering Fundamentals
- [ ] Batch vs. streaming data: architecture differences and tradeoffs
- [ ] Data formats: CSV vs. Parquet vs. Arrow — when to use each and why
- [ ] Schema management: why schemas matter, schema evolution, validation with Pydantic
- [ ] Data quality: nulls, outliers, distribution drift, silent corruption
- [ ] **Implementation:** Build a data validation library — define schemas with Pydantic, write validators for common issues (nulls, type mismatches, range violations), run against a sample dataset and produce a quality report

### 2. Feature Engineering
- [ ] Feature types: numerical, categorical, temporal, embeddings
- [ ] Transformation patterns: normalization, encoding, binning, interactions
- [ ] Training/serving skew: why features computed differently at train vs. serve time cause bugs
- [ ] Point-in-time correctness: using only data available at prediction time
- [ ] **Implementation:** Build a feature transformation pipeline using sklearn-compatible transformers — support fit/transform semantics, serialize fitted transformers, verify training/serving parity

### 3. Feature Stores
- [ ] What a feature store is and what problem it solves
- [ ] Online vs. offline store: latency requirements, storage backends
- [ ] Feature registry: naming, versioning, documentation
- [ ] Feast: architecture, feature views, entity definitions, materialization
- [ ] **Project:** Build a minimal feature store from scratch — a Python class that supports: defining feature groups, computing and storing features offline (Parquet), serving features online (Redis or in-memory dict), and retrieving historical features for training

### 4. Data Versioning
- [ ] Why versioning datasets matters (reproducibility, debugging, rollbacks)
- [ ] DVC: data version control, remote storage, pipelines as DAGs
- [ ] Experiment tracking vs. data versioning — how they relate
- [ ] **Project:** Set up DVC on a real dataset — version a dataset, define a multi-step pipeline (ingest → clean → featurize → train), run it end-to-end, reproduce from a previous version

### 5. Pipeline Orchestration
- [ ] DAG-based orchestration: tasks, dependencies, scheduling
- [ ] Prefect: flows, tasks, deployments, retries, observability
- [ ] Airflow: DAGs, operators, sensors — conceptual comparison with Prefect
- [ ] Triggering strategies: cron, event-driven, manual
- [ ] **Project:** Orchestrate a full ML pipeline with Prefect — ingest data, validate, featurize, train, evaluate, and conditionally promote a model based on metrics. Add email/Slack alerting on failure.

### 6. Testing ML Pipelines
- [ ] Unit testing transformations: input/output contracts
- [ ] Integration testing pipelines end-to-end with synthetic data
- [ ] Data drift detection: statistical tests (KS test, PSI), monitoring in production
- [ ] **Implementation:** Add a test suite to your feature pipeline — unit tests for each transformer, integration test for the full pipeline, and a drift detector using KS test

---

## Projects

| Project | Description | Key concepts |
|---|---|---|
| Data validation library | Schema-based validation with quality reporting | Pydantic, data quality |
| Feature transformation pipeline | Sklearn-compatible fit/transform with serialization | Training/serving parity |
| Minimal feature store | Offline + online feature store from scratch | Feature stores, Redis, Parquet |
| DVC pipeline | Versioned, reproducible ML pipeline with DVC | Data versioning, reproducibility |
| Prefect orchestrated pipeline | Full ML pipeline with scheduling, retries, alerting | Orchestration, observability |
| Test suite for ML pipeline | Unit + integration tests + drift detection | ML testing, statistical tests |

---

## Resources

**Books**
- *Designing Machine Learning Systems* — Chip Huyen (the most practical ML systems book)
- *Fundamentals of Data Engineering* — Reis & Housley (data engineering foundations)

**Tools Documentation**
- DVC docs — dvc.org
- Prefect docs — docs.prefect.io
- Feast docs — docs.feast.dev

**Papers**
- *Hidden Technical Debt in Machine Learning Systems* — Sculley et al., Google (2015) — essential reading
- *Towards ML Engineering: A Brief History Of TFX* — Baylor et al. (2022)

---

## Progress

- [ ] Data engineering fundamentals
- [ ] Feature engineering
- [ ] Feature stores
- [ ] Data versioning
- [ ] Pipeline orchestration
- [ ] Testing ML pipelines
- [ ] Project: Data validation library
- [ ] Project: Feature transformation pipeline
- [ ] Project: Minimal feature store
- [ ] Project: DVC pipeline
- [ ] Project: Prefect orchestrated pipeline
- [ ] Project: Test suite for ML pipeline
