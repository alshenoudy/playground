# Reproducibility

A result you cannot reproduce is not a result. Reproducibility in deep learning is harder than it looks: randomness is everywhere, environments drift, and implicit assumptions are easy to miss. This track builds the habits and infrastructure to make your research reproducible by default — not as an afterthought.

---

## Goal

- Understand and control all sources of non-determinism in PyTorch experiments
- Containerise experiments so the environment is fully specified and portable
- Version data and code together so any historical result can be reproduced exactly
- Write research code that others (and future you) can run without archaeology

---

## Prerequisites

- Python and PyTorch proficiency
- Basic Docker knowledge (covered in `software-engineering/devops`)
- Git proficiency

---

## Learning Path

### 1. Sources of Non-Determinism
- [ ] Random seeds: Python `random`, NumPy, PyTorch CPU, PyTorch CUDA — all must be seeded
- [ ] CUDA non-determinism: `torch.backends.cudnn.deterministic`, `torch.backends.cudnn.benchmark` — understand the performance vs. reproducibility tradeoff
- [ ] DataLoader: `num_workers > 0` introduces ordering non-determinism; `worker_init_fn` for seeding workers
- [ ] Floating point non-determinism: operation ordering, mixed precision, atomic operations on GPU
- [ ] **Implementation:** Write a `set_reproducibility(seed)` utility function that handles all of the above correctly. Verify it produces identical results across two runs with the same seed.

### 2. Environment Reproducibility
- [ ] `requirements.txt` vs. `pip freeze` vs. `pyproject.toml` — what each captures and misses
- [ ] Conda environments: `environment.yml` with pinned versions
- [ ] Docker for experiments: base image, CUDA version, pinned dependencies, no `latest` tags
- [ ] CUDA + cuDNN versioning: why the same code can behave differently across driver versions
- [ ] **Project:** Write a `Dockerfile` for a medical imaging experiment — base CUDA image, pinned Python/PyTorch/MONAI versions, no floating dependencies. Build it and verify your training script produces identical results inside and outside the container.

### 3. Code Reproducibility
- [ ] Git discipline for research: commit before every experiment run, tag experiments with git hashes
- [ ] Never modify code between runs without committing — the diff is your experiment record
- [ ] Config-driven experiments: no hardcoded hyperparameters in code (use Hydra — see `experiment-tracking/`)
- [ ] Logging the full config + git hash + environment snapshot at the start of every run
- [ ] **Implementation:** Add a `log_run_context()` function that captures and logs: git commit hash, git diff status (clean or dirty), full Hydra config, Python/PyTorch/CUDA versions, hostname and GPU info

### 4. Data Reproducibility
- [ ] Dataset versioning with DVC: every dataset used in a published result should be versioned
- [ ] Deterministic splits: save train/val/test splits as files, never regenerate from a random seed
- [ ] Preprocessing versioning: the preprocessing applied to data should be versioned alongside the data
- [ ] **Implementation:** Set up DVC on a medical imaging dataset — version the raw data, preprocessing pipeline, and processed outputs. Reproduce the processed dataset from scratch from the DVC pipeline.

### 5. The Reproducibility Checklist
- [ ] NeurIPS/MICCAI reproducibility checklists — read and internalise
- [ ] What to include in a paper's implementation details section
- [ ] Releasing code: what to include, how to structure a research repo for others
- [ ] **Implementation:** Apply the reproducibility checklist to one of your existing projects — identify gaps and fix them

---

## Projects

| Project | Description |
|---|---|
| `set_reproducibility()` utility | Seed everything, verify identical runs |
| Experiment Dockerfile | Fully pinned container for a training experiment |
| `log_run_context()` utility | Capture git hash, config, environment at run start |
| DVC data pipeline | Versioned dataset + preprocessing pipeline |
| Reproducibility audit | Apply checklist to an existing project, document gaps |

---

## Resources

**Papers / Reports**
- *Reproducibility in Machine Learning* — Pineau et al. (NeurIPS reproducibility checklist authors)
- *A Step Toward Quantifying Independently Reproducible ML Research* — Raff (2019)
- *High Performance Python* — Gorelick & Ozsvald (chapter on profiling non-determinism)

**Tools**
- DVC — dvc.org
- `torch.use_deterministic_algorithms(True)` — PyTorch docs
- Papers With Code Reproducibility Checklist — paperswithcode.com/rc2022

---

## Progress

- [ ] Sources of non-determinism in PyTorch
- [ ] Environment reproducibility (Docker, pinned deps)
- [ ] Code reproducibility (git discipline, config-driven)
- [ ] Data reproducibility (DVC, deterministic splits)
- [ ] Reproducibility checklist
- [ ] Project: `set_reproducibility()` utility
- [ ] Project: Experiment Dockerfile
- [ ] Project: `log_run_context()` utility
- [ ] Project: DVC data pipeline
- [ ] Project: Reproducibility audit on existing project
