# Projects

End-to-end projects that cross domain boundaries. Each project is self-contained with its own subfolder, README, and code. These are the capstone efforts where math, systems, ML engineering, and medical imaging knowledge converge.

---

## How to Use This Folder

When starting a project:
1. Create a subfolder: `projects/<project-name>/`
2. Write a `README.md` in the project folder covering: goal, scope, domains crossed, success criteria, and progress
3. Treat it as production code — proper structure, tests, reproducibility setup
4. Link it back here when complete

---

## Suggested Projects

Projects are ordered roughly by scope and dependency. Earlier projects can be done with less prerequisite knowledge.

---

### 1. Loss Function Benchmark for Segmentation
**Domains:** `medical-imaging/segmentation` + `foundations/math/calculus-optimization`

Implement Dice, Generalised Dice, Tversky, Focal, Boundary, and combined losses from scratch. Train a baseline U-Net on an MSD task under each. Produce a comparison table with DSC, HD95, and learning curves. Write a short analysis of when each loss helps.

**Success criteria:** Reproducible results across 3 seeds; statistical comparison with Wilcoxon test; publication-quality comparison table.

---

### 2. nnU-Net Self-Configuring Pipeline Reimplementation
**Domains:** `medical-imaging/segmentation` + `engineering/ml-systems/pipelines` + `research/reproducibility`

Reimplement the core of nnU-Net's self-configuration logic from scratch: dataset fingerprinting, patch size determination, network topology selection, and augmentation pipeline. You do not need to match every detail — the goal is to understand the decisions deeply enough to explain and extend them.

**Success criteria:** Your configuration decisions match nnU-Net's on at least 3 MSD tasks; documented technical note explaining the logic.

---

### 3. VoxelMorph Reimplementation + ANTs Benchmark
**Domains:** `medical-imaging/registration` + `foundations/math/linear-algebra` + `research/evaluation`

Implement VoxelMorph from scratch in PyTorch. Train on brain MRI (OASIS or IXI). Benchmark against ANTs SyN. Evaluate: Dice on propagated labels, % folding, runtime. Document where each approach excels and fails.

**Success criteria:** Results within 2% Dice of reported VoxelMorph numbers; statistical comparison with ANTs; folding analysis.

---

### 4. Contrastive Pretraining on Medical Data
**Domains:** `medical-imaging/representation` + `foundations/math/probability-statistics` + `research/experiment-tracking`

Implement SimCLR or MoCo pretraining on unlabelled 3D medical data. Design augmentations appropriate for volumetric images. Evaluate transfer via linear probe and fine-tuning at 10/50/100% label fractions. Compare against ImageNet init and Models Genesis.

**Success criteria:** Pretraining code is clean and reusable; downstream evaluation is patient-level split; results tracked in W&B with full config logging.

---

### 5. Deformable Registration as a gRPC Service
**Domains:** `medical-imaging/registration` + `engineering/systems/go` + `engineering/ml-systems/inference`

Wrap a trained registration model (from Project 3) behind a gRPC service. Define a `.proto` schema for: send a fixed + moving image pair, receive a deformation field and warped image. Implement the server in Python (model inference) and a Go client for integration testing. Benchmark latency.

**Success criteria:** Working gRPC service; Go client calls it and receives correct output; p95 latency benchmarked.

---

### 6. Uncertainty-Aware Segmentation with Conformal Prediction
**Domains:** `medical-imaging/segmentation` + `foundations/math/probability-statistics` + `research/evaluation`

Implement MC Dropout and deep ensembles on a segmentation model. Then implement conformal prediction to produce statistically guaranteed prediction sets. Evaluate: calibration curves, coverage at guaranteed coverage levels, the correlation between uncertainty and segmentation error.

**Success criteria:** Conformal sets achieve nominal coverage (e.g., 90%) on held-out test cases; uncertainty maps are visually sensible; calibration analysis is complete.

---

### 7. Diffusion-Based MRI Synthesis + Downstream Evaluation
**Domains:** `medical-imaging/synthesis` + `foundations/math/probability-statistics` + `research/ablations`

Train a 2D LDM or DDPM on an MRI dataset. Evaluate synthesis quality (FID, SSIM). Then use generated images to augment a segmentation task — measure whether synthetic augmentation improves performance, especially at low label fractions. Run a proper ablation: augmentation ratio, generation quality threshold, conditioning.

**Success criteria:** Downstream segmentation improvement demonstrated with statistical testing; ablation table with at least 4 conditions.

---

### 8. Federated Learning Prototype for Medical Imaging
**Domains:** `medical-imaging/segmentation` + `engineering/ml-systems/distributed` + `engineering/software-engineering/devops`

Implement a simple federated learning setup: 3 simulated "sites" (processes or containers), each with a disjoint subset of a medical dataset. Implement FedAvg. Compare against centralised training and local-only training. Simulate heterogeneous data distributions across sites.

**Success criteria:** FedAvg converges; comparison against centralised baseline is fair (same total compute); data heterogeneity experiment shows degradation and quantifies it.

---

### 9. Full ML Pipeline: Research to Deployment
**Domains:** All `engineering/ml-systems/` + `engineering/software-engineering/devops` + `medical-imaging/foundations`

Take a trained segmentation or registration model from a previous project and build the full path to deployment:
- ONNX export with parity testing
- Dockerised inference server with DICOM-aware input/output
- Kubernetes deployment with health probes and HPA
- CI/CD pipeline (GitHub Actions) that runs tests and rebuilds on push
- Prometheus + Grafana observability dashboard

**Success criteria:** End-to-end pipeline from DICOM input to DICOM-SEG output; deployed on local K8s; observable with a working dashboard.

---

## Completed Projects

> Move projects here when done, with a link and one-line summary of what was built.

| Project | Completed | Summary |
|---|---|---|
| | | |
