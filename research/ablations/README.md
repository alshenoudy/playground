# Ablation Studies

An ablation study systematically removes or replaces components of a method to establish what actually contributes to performance. Done well, ablations are the most convincing part of a paper. Done poorly, they are a table of numbers that proves nothing. This track builds the discipline to design, run, and present ablations that are scientifically rigorous.

---

## Goal

- Design ablation studies that isolate variables and produce interpretable conclusions
- Avoid the common pitfalls: underpowered ablations, cherry-picked baselines, unfair comparisons
- Present results in tables and visualisations that communicate clearly
- Develop a pre-experiment planning habit that forces clarity before you run anything

---

## Prerequisites

- Experiment tracking setup (complete `experiment-tracking/` first)
- Reproducibility setup (complete `reproducibility/` first)
- Evaluation methodology (complete `evaluation/` first — ablations must use proper statistical testing)

---

## Learning Path

### 1. What an Ablation Is (and Isn't)
- [ ] The purpose: establish the contribution of each component — not just show that the full method is best
- [ ] Ablation vs. hyperparameter search: ablations vary *what* you do; hyperparameter search varies *how much*
- [ ] The baseline is the most important run: it must be fair, strong, and reproducible
- [ ] What counts as a component: loss term, architectural block, augmentation strategy, training trick, data preprocessing step
- [ ] Common mistake: ablating components that were already tuned together — confounds are everywhere

### 2. Designing a Clean Ablation
- [ ] **One variable at a time:** change exactly one thing per ablation condition
- [ ] **Control the confounds:** same seed, same data split, same number of epochs, same compute budget
- [ ] **Statistical power:** with small medical datasets, a single run per condition is insufficient — run multiple seeds, report mean ± std, apply Wilcoxon test
- [ ] **Fair baselines:** the baseline should be as strong as possible — a weak baseline makes your contribution look larger than it is
- [ ] **Negative ablations matter:** if removing a component doesn't hurt performance, either the component doesn't help or the ablation is underpowered
- [ ] **Implementation:** Before every ablation experiment, fill in the pre-experiment plan template — forces you to state the hypothesis, expected direction of effect, and what you will conclude if the result is null

### 3. Pre-Experiment Plan Template

Use this before every ablation run. Commit it to the repo alongside the experiment config.

```markdown
## Experiment Plan

**Date:**
**Hypothesis:** Removing/changing X will decrease performance because Y
**Variable being changed:** (exactly one thing)
**Everything held constant:** seed, split, epochs, batch size, ...
**Metric(s) to evaluate:** DSC, HD95 (primary), ...
**Expected direction of effect:** + / - / unclear
**Number of runs:** (minimum 3 seeds for medical imaging with small datasets)
**Statistical test:** Wilcoxon signed-rank, paired across test cases
**Decision rule:** What result would cause you to include/exclude this component?
**What does a null result mean?** (don't leave this blank — null results are informative)
```

### 4. Presenting Ablation Results
- [ ] Table structure: rows = ablation conditions, columns = metrics; clearly mark the proposed method
- [ ] Statistical annotations: indicate significance (*, **, ***) with a footnote defining the threshold
- [ ] Report mean ± std across seeds or folds, not a single run
- [ ] Visualise beyond tables: bar plots with error bars, violin plots for distribution, qualitative examples for segmentation
- [ ] The narrative: each ablation should map to a sentence in the paper — "removing X decreases DSC by Y points (p < 0.05), confirming its contribution"
- [ ] **Implementation:** Take a past experiment's results and produce a publication-quality ablation table using matplotlib/seaborn — include error bars, significance stars, and bold the best result per column

### 5. Common Ablation Antipatterns to Avoid
- [ ] **Post-hoc ablations:** designing the ablation after seeing results to justify choices already made
- [ ] **Inconsistent compute:** comparing a method trained for 200 epochs against a baseline trained for 100
- [ ] **Testing only upward ablations:** only showing components that help; not showing what you tried that didn't work
- [ ] **Missing the interaction effect:** components that only work together — ablating them independently misses the interaction
- [ ] **Overfitting the ablation to the validation set:** ablations must be evaluated on held-out data

---

## Projects

| Project | Description |
|---|---|
| Pre-experiment plan template | A filled-in example plan for a real past or current experiment |
| Publication-quality ablation table | Formatted results table with stats annotations in matplotlib |
| Ablation audit | Critically review the ablation section of 2–3 MICCAI papers — what's rigorous, what's weak? |

---

## Resources

**Papers (study the ablation sections, not just the contributions)**
- nnU-Net — Isensee et al., Nature Methods 2021 — well-designed ablations on training components
- *What makes for good views for contrastive learning?* — Tian et al., NeurIPS 2020 — ablation-heavy paper; good template
- Any MICCAI best paper — pay attention to how they structure their experimental section

**Books**
- *Designing Experiments and Analysing Data* — Maxwell & Delaney (statistical foundations of experimental design)

---

## Progress

- [ ] What an ablation is and isn't
- [ ] Designing clean ablations (one variable, controlled confounds, powered tests)
- [ ] Pre-experiment plan template
- [ ] Presenting ablation results (tables, plots, narrative)
- [ ] Common ablation antipatterns
- [ ] Project: Pre-experiment plan template (filled example)
- [ ] Project: Publication-quality ablation table
- [ ] Project: Ablation audit of 2–3 MICCAI papers
