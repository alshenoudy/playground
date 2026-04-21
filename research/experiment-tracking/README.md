# Experiment Tracking

Running experiments without proper tracking is how you lose months of work — unable to reproduce a result, unsure which hyperparameter caused an improvement, with no audit trail of what you actually tried. This track builds the discipline and tooling to make your experiments reproducible, comparable, and auditable.

---

## Goal

- Set up a robust experiment tracking workflow using W&B and/or MLflow
- Manage complex hyperparameter configurations cleanly with Hydra
- Compare experiments systematically — not by memory, but by data
- Design experiments so that results are interpretable and reproducible by others

---

## Prerequisites

- Python proficiency, familiarity with writing training loops
- Basic YAML/config file experience

---

## Learning Path

### 1. What to Track and Why
- [ ] The cost of poor tracking: failed reproductions, wasted compute, lost results
- [ ] What to log: hyperparameters, metrics, artifacts (model checkpoints, sample outputs), system info (GPU, library versions), git commit hash
- [ ] The difference between a *run*, an *experiment*, and a *project*
- [ ] Logging strategy: log frequently during training (per-step), summarise per-epoch, save artifacts at checkpoints

### 2. Weights & Biases (W&B)
- [ ] Project setup, run initialisation, automatic environment capture
- [ ] Logging scalars, images, 3D volumes, segmentation masks, confusion matrices
- [ ] W&B Artifacts: versioning datasets, models, and preprocessing outputs
- [ ] W&B Sweeps: hyperparameter search (grid, random, Bayesian) — define a sweep config and run it
- [ ] Comparing runs: parallel coordinates plots, scatter plots, custom panels
- [ ] **Implementation:** Instrument an existing training script — add W&B logging, log per-step loss, per-epoch metrics, sample predictions as images, and final model as an artifact

### 3. MLflow (Alternative / Complement)
- [ ] MLflow tracking: experiments, runs, parameters, metrics, artifacts
- [ ] MLflow Model Registry: versioning and staging models (None → Staging → Production)
- [ ] When to use MLflow vs. W&B: self-hosted vs. cloud, open-source requirements
- [ ] **Implementation:** Set up a local MLflow tracking server, log an experiment, register a model

### 4. Configuration Management with Hydra
- [ ] Why config files beat argparse at scale: composability, overrides, multirun
- [ ] Hydra basics: config groups, defaults list, config composition
- [ ] Structured configs with dataclasses: type-safe configuration
- [ ] Hydra + W&B: log the full composed config to W&B at run start
- [ ] **Implementation:** Refactor a training script to use Hydra — define config groups for model, optimizer, dataset, and augmentation. Run a multirun sweep from the command line.

### 5. Experiment Design Discipline
- [ ] One variable at a time: why changing multiple things simultaneously makes results uninterpretable
- [ ] Baseline first, always: establish a strong, reproducible baseline before any ablations
- [ ] Budgeting compute: when to run full experiments vs. proxy tasks (smaller dataset, fewer epochs)
- [ ] Recording negative results: failed experiments are data — log them properly
- [ ] **Implementation:** Write an experiment plan template — a structured document you fill in before running any experiment, specifying hypothesis, variables, controls, and success criteria

---

## Projects

| Project | Description |
|---|---|
| Instrumented training pipeline | Full W&B integration: metrics, images, artifacts, git hash |
| MLflow local server | Self-hosted tracking + model registry |
| Hydra-configured trainer | Config-driven training with composable groups and multirun |
| Experiment plan template | A reusable pre-experiment document (see `research/ablations/`) |

---

## Resources

**Documentation**
- W&B docs — docs.wandb.ai (excellent, with medical imaging examples)
- Hydra docs — hydra.cc/docs
- MLflow docs — mlflow.org/docs

**Posts**
- *Reproducibility in ML* — Papers With Code reproducibility checklist
- W&B Reports gallery — example well-documented experiments

---

## Progress

- [ ] What to track and why
- [ ] W&B setup and logging
- [ ] W&B Artifacts and Sweeps
- [ ] MLflow tracking and model registry
- [ ] Hydra configuration management
- [ ] Experiment design discipline
- [ ] Project: Instrumented training pipeline
- [ ] Project: MLflow local server
- [ ] Project: Hydra-configured trainer
- [ ] Project: Experiment plan template
