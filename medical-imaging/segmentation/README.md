# Medical Imaging — Segmentation

Segmentation is the most prevalent task in medical imaging. This track builds deep understanding of the architecture and training decisions behind state-of-the-art methods — from the original U-Net through nnU-Net's self-configuring approach to modern transformer-based architectures.

---

## Goal

- Understand the architectural decisions in U-Net variants and why they matter for medical images
- Know the loss function landscape and when each loss is appropriate
- Evaluate segmentation models correctly — not just Dice, but the full picture
- Understand nnU-Net's self-configuring pipeline deeply enough to extend it
- Be current on transformer-based and foundation model approaches to segmentation

---

## Paper Reading List

Work through roughly in order. Papers marked **[core]** are essential before moving on.

### Foundational Architecture
| Paper | Notes |
|---|---|
| **[core]** *U-Net: Convolutional Networks for Biomedical Image Segmentation* — Ronneberger et al., MICCAI 2015 | The baseline everything is compared against |
| **[core]** *3D U-Net: Learning Dense Volumetric Segmentation from Sparse Annotation* — Çiçek et al., MICCAI 2016 | Extension to volumetric data |
| *V-Net: Fully Convolutional Neural Networks for Volumetric Medical Image Segmentation* — Milletari et al., 3DV 2016 | Introduces Dice loss; residual connections in 3D |
| *nnU-Net: a self-configuring method for deep learning-based biomedical image segmentation* — Isensee et al., Nature Methods 2021 | **[core]** The current gold standard baseline; study the self-configuration logic |
| *Swin-UNETR: Swin Transformers for Semantic Segmentation of Brain Tumors* — Hatamizadeh et al., MICCAI 2022 | Transformer encoder + U-Net decoder |
| *UNETR: Transformers for 3D Medical Image Segmentation* — Hatamizadeh et al., WACV 2022 | Pure transformer approach |
| *Segment Anything Model (SAM)* — Kirillov et al. (2023) | Foundational; read before medical SAM variants |
| *SAM-Med3D* — Wang et al. (2023) | SAM adapted for volumetric medical segmentation |

### Loss Functions
| Paper | Notes |
|---|---|
| **[core]** *Generalised Dice overlap as a deep learning loss function for highly unbalanced segmentations* — Sudre et al., MICCAI 2017 | Generalised Dice loss derivation |
| *Combo Loss: Handling input and output imbalance in multi-organ segmentation* — Taghanaki et al. (2019) | Combining Dice + cross-entropy |
| *Boundary loss for highly unbalanced segmentation* — Kervadec et al., MIDL 2019 | Distance-based boundary loss |
| *Exponential Logarithmic Loss for Small Lesion Segmentation* — Wong et al., MICCAI 2018 | Handling small, rare structures |

### Semi-supervised and Weakly-supervised
| Paper | Notes |
|---|---|
| *Mean Teacher for Semi-supervised Segmentation* — Tarvainen & Valpola (2017) + medical imaging adaptations | Consistency regularization |
| *Uncertainty-aware Self-ensembling for Semi-supervised Segmentation* — Yu et al., MICCAI 2019 | Uncertainty-guided pseudo-labelling |
| *Scribble-based Segmentation* — Lin et al. (2016) | Weak supervision from scribbles |

---

## Projects

### 1. Loss function benchmark
Implement from scratch: Dice loss, Generalised Dice, Tversky loss, Focal loss, Boundary loss, and a combined Dice + CE loss. Train a baseline 2D U-Net on a small MSD task under each loss. Plot learning curves and final Dice/HD95 scores in a comparison table. Understand empirically, not just theoretically, when each matters.

### 2. nnU-Net dissection
Run nnU-Net on an MSD task. Then read the source code and document:
- How it determines patch size, batch size, and network topology from dataset fingerprint
- How it handles anisotropic spacing (2D vs. 3D vs. cascade)
- How its data augmentation pipeline works
- Where you would inject a custom architecture or loss

Write a technical note summarising your findings. The goal is to understand it well enough to modify it.

---

## Evaluation Reference

Always report beyond Dice alone:

| Metric | What it captures | Notes |
|---|---|---|
| Dice Similarity Coefficient (DSC) | Volumetric overlap | Sensitive to large structures; insensitive to boundary errors |
| Hausdorff Distance 95th percentile (HD95) | Worst-case boundary error | Use 95th not max — max is too sensitive to outliers |
| Average Surface Distance (ASD) | Mean boundary error | Complementary to HD95 |
| Normalised Surface Distance (NSD) | Clinically-tolerable boundary error | Tolerance threshold must be justified clinically |
| Volume similarity | Systematic over/under-segmentation | Important for volumetric analysis downstream |

Always run statistical significance testing across folds. Report mean ± std across cross-validation folds, not a single hold-out split.

---

## Progress

- [ ] U-Net and 3D U-Net (core)
- [ ] nnU-Net (core) — read paper + run on MSD task
- [ ] Loss function landscape
- [ ] Transformer-based architectures (Swin-UNETR, UNETR)
- [ ] SAM and medical SAM variants
- [ ] Semi/weakly supervised methods
- [ ] Project: Loss function benchmark
- [ ] Project: nnU-Net dissection + technical note
