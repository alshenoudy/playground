# Evaluation Methodology

Evaluation is where most medical imaging papers are weakest — and where reviewers look hardest. Reporting a single Dice score on a single split is not evaluation. This track builds rigorous evaluation methodology: statistical testing, confidence intervals, cross-validation design, clinical metrics, and the common mistakes that invalidate results.

---

## Goal

- Design evaluation protocols that produce results reviewers and clinicians can trust
- Apply appropriate statistical tests and report results with confidence intervals
- Understand the specific evaluation pitfalls in medical imaging (small datasets, class imbalance, patient-level vs. slice-level splits)
- Know the right metric for every task — and the wrong metrics to avoid

---

## Prerequisites

- Python and NumPy/SciPy proficiency
- Basic statistics: mean, variance, p-values, null hypothesis testing

---

## Learning Path

### 1. The Evaluation Pitfalls in Medical Imaging
- [ ] **Data leakage:** patient-level vs. scan-level vs. slice-level splits — why splitting at the wrong level inflates results
- [ ] **Small test sets:** why a single Dice score on 20 cases is near-meaningless without uncertainty
- [ ] **Class imbalance:** global accuracy is uninformative for rare pathologies; use appropriate metrics
- [ ] **Metric gaming:** Dice can be high with poor clinical performance; HD95 can be misleading for small structures
- [ ] **Multiple comparisons:** testing many things and reporting only what worked — inflates false positive rate
- [ ] **Implementation:** Take a real dataset, demonstrate the difference in reported performance between patient-level and slice-level splits on the same model

### 2. Cross-Validation Design
- [ ] K-fold vs. leave-one-out vs. nested cross-validation
- [ ] Stratified splits: ensuring class balance and patient balance across folds
- [ ] When to use a held-out test set vs. cross-validation
- [ ] The test set is sacred: only touch it once — when you are done with all model development
- [ ] **Implementation:** Implement a stratified patient-level k-fold splitter for a medical dataset — split at patient level, stratify by label prevalence, verify no patient overlap across folds

### 3. Statistical Significance Testing
- [ ] Why p-values alone are insufficient: effect size matters
- [ ] Parametric vs. non-parametric tests: when each applies
- [ ] **Wilcoxon signed-rank test:** compare two paired models on the same test cases — the standard in medical imaging comparison papers
- [ ] **Bootstrap confidence intervals:** resample the test set to estimate the CI of any metric
- [ ] **Bonferroni correction:** adjust for multiple comparisons
- [ ] **Implementation:** Given results from two models across N test cases, compute: Wilcoxon p-value, effect size (r), 95% bootstrap CI for both metrics, and a properly formatted results table

### 4. Metrics Reference for Medical Imaging Tasks

#### Segmentation
| Metric | Formula | When to use |
|---|---|---|
| Dice (DSC) | 2\|A∩B\| / (\|A\|+\|B\|) | Primary overlap metric; report always |
| HD95 | 95th percentile Hausdorff distance | Boundary accuracy; report alongside Dice |
| ASD | Mean surface distance | Complementary boundary metric |
| NSD | Surface Dice at tolerance τ | Clinical plausibility; τ must be justified |
| Volume similarity | 2(V_pred - V_gt) / (V_pred + V_gt) | Systematic bias detection |

#### Detection
| Metric | When to use |
|---|---|
| Sensitivity @ N FPs/scan | Standard for lesion detection; report at multiple FP rates |
| FROC curve | Show the full sensitivity/FP tradeoff |
| JAFROC FOM | Single-number summary; preferred over AUFROC |

#### Classification
| Metric | When to use |
|---|---|
| AUC-ROC | Class-imbalanced binary classification |
| AUC-PR | When positive class is rare |
| Balanced accuracy | Multi-class with imbalance |
| Calibration (ECE, reliability diagram) | When confidence matters clinically |

### 5. Clinical Validity
- [ ] Inter-rater variability: how to use it as a performance ceiling — if two radiologists disagree more than your model and the annotation, you may already be at human-level
- [ ] Intra-rater variability: repeatability of the annotation itself
- [ ] Clinical endpoints: does better Dice translate to better downstream clinical decisions? Not always.
- [ ] **Implementation:** Compute inter-rater agreement (Dice between two annotators) on a dataset with multiple annotations (e.g., LIDC has 4 radiologist annotations per nodule). Use this as context for model performance.

---

## Projects

| Project | Description |
|---|---|
| Leakage demonstration | Show split-level impact on reported performance |
| Stratified patient-level splitter | Correct k-fold with patient-level stratification |
| Statistical testing toolkit | Wilcoxon, bootstrap CI, Bonferroni — reusable functions |
| Inter-rater agreement analysis | Compute and interpret annotator agreement as performance context |

---

## Resources

**Papers**
- *Statistical methods for assessing agreement between two methods of clinical measurement* — Bland & Altman (1986) — Bland-Altman plots for method comparison
- *Clinically significant? Statistical vs. Clinical Significance* — various medical statistics papers
- *Common Limitations of Image Processing Metrics: A Picture Story* — Reinke et al. (2022, Nature Methods) — essential reading on metric pitfalls in medical imaging
- *How to (and how not to) assess the performance of a classifier* — Jeni et al.

**Books**
- *Statistics Done Wrong* — Reinhart (short, important)
- *Nonparametric Statistics for the Behavioral Sciences* — Siegel & Castellan (reference for Wilcoxon and related tests)

---

## Progress

- [ ] Evaluation pitfalls in medical imaging
- [ ] Cross-validation design
- [ ] Statistical significance testing (Wilcoxon, bootstrap CI)
- [ ] Metrics for segmentation, detection, classification
- [ ] Clinical validity and inter-rater agreement
- [ ] Project: Leakage demonstration
- [ ] Project: Stratified patient-level splitter
- [ ] Project: Statistical testing toolkit
- [ ] Project: Inter-rater agreement analysis
