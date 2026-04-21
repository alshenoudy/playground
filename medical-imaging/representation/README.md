# Medical Imaging — Representation Learning

Learning good representations from medical images — especially with limited labels — is one of the most active research areas in the field. This track covers self-supervised learning, contrastive methods, and the emerging medical foundation models that are redefining what's possible with small labelled datasets.

---

## Goal

- Understand contrastive and self-supervised learning at a level sufficient to design and implement new pretraining strategies
- Know the landscape of medical foundation models and their limitations
- Implement a contrastive pretraining pipeline on medical data and measure its transfer value
- Critically evaluate claims about foundation models in medical imaging — there is significant hype to cut through

---

## Paper Reading List

### Self-Supervised Learning Foundations
| Paper | Notes |
|---|---|
| **[core]** *A Simple Framework for Contrastive Learning of Visual Representations (SimCLR)* — Chen et al., ICML 2020 | Clean, well-explained contrastive learning baseline |
| **[core]** *Momentum Contrast for Unsupervised Visual Representation Learning (MoCo)* — He et al., CVPR 2020 | Memory bank approach; more efficient than SimCLR |
| *Bootstrap Your Own Latent (BYOL)* — Grill et al., NeurIPS 2020 | Contrastive learning without negative pairs |
| *Exploring Simple Siamese Representation Learning (SimSiam)* — Chen & He, CVPR 2021 | Simplified further; understand collapse prevention |
| **[core]** *Emerging Properties in Self-Supervised Vision Transformers (DINO)* — Caron et al., ICCV 2021 | Self-supervised ViT with strong properties — widely used |
| *Masked Autoencoders Are Scalable Vision Learners (MAE)* — He et al., CVPR 2022 | Masking-based SSL; strong results with ViT |

### Medical Imaging SSL
| Paper | Notes |
|---|---|
| **[core]** *Models Genesis: Generic Autodidactic Models for 3D Medical Image Analysis* — Zhou et al., MICCAI 2019 | Seminal medical self-supervised pretraining paper |
| *Preservational Learning Improves Self-supervised Medical Image Models by Reconstructing Diverse Contexts* — Zhou et al., ICCV 2021 | Extension of Models Genesis |
| *Self-supervised Learning for Medical Image Analysis using Image Context Restoration* — Chen et al., Medical Image Analysis 2019 | Context restoration as a pretext task |
| *C2L: Contrastive Learning for Cross-domain Medical Image Segmentation* | Domain-invariant representations |
| *nnCLR and Medical Contrastive Learning* — various (2021–2023) | See papers/representation/ for growing list |

### Foundation Models in Medical Imaging
| Paper | Notes |
|---|---|
| **[core]** *Segment Anything (SAM)* — Kirillov et al. (2023) | General segmentation foundation model — baseline for all medical adaptations |
| *MedSAM: Segment Anything in Medical Images* — Ma et al. (2023) | SAM fine-tuned on large medical dataset |
| *SAM-Med2D / SAM-Med3D* — (2023) | 2D and 3D medical adaptations of SAM |
| *BioViL-T: Learning to Exploit Temporal Structure for Biomedical Vision-Language Processing* — Bannur et al., CVPR 2023 | Vision-language pretraining on medical reports |
| *CONCH: A Vision-Language Foundation Model for Computational Pathology* — Lu et al. (2023) | Domain-specific VL foundation model |
| *Universal and Extensible Language-Vision Models for Medical Image Analysis* — (ongoing, 2023–2024) | Track the evolving space |

### Transfer Learning and Fine-Tuning
| Paper | Notes |
|---|---|
| *Transfusion: Understanding Transfer Learning for Medical Imaging* — Raghu et al., NeurIPS 2019 | Critical analysis of ImageNet pretraining for medical imaging — surprises here |
| *Big Self-Supervised Models Advance Medical Image Classification* — Azizi et al., ICCV 2021 | Large-scale SSL pretraining for medical imaging |
| *Low-Shot Learning via Covariate-Preserving Mixup* — relevant for few-shot medical settings | |

---

## Projects

### 1. Contrastive pretraining on medical data
Implement SimCLR or MoCo pretraining on a volumetric medical dataset (e.g., unlabelled CT from TCIA):
- Design augmentation strategies appropriate for medical images (not natural image augmentations blindly applied)
- Evaluate transfer: linear probe and fine-tuning on a downstream segmentation or classification task with 10%, 50%, 100% of labels
- Compare against: random init, ImageNet pretrained, Models Genesis pretrained
- Document which augmentations help and which hurt (this is non-obvious for medical images)

### 2. SAM adaptation for volumetric segmentation
Adapt SAM (or a medical SAM variant) to a 3D segmentation task:
- Implement prompt engineering strategies: point prompts, box prompts, propagation across slices
- Compare interactive (prompt-based) vs. fully automatic segmentation performance
- Evaluate on a multi-structure segmentation task; identify which structures SAM handles well vs. poorly and hypothesise why

---

## Critical Perspectives

Medical foundation models are a rapidly growing area with significant hype. Read critically:

- Most medical foundation models are evaluated on benchmarks that may not reflect clinical utility
- SAM's zero-shot performance on medical images is often poor for small or ambiguous structures — fine-tuning is required
- "Foundation model" claims often rest on breadth of training data, not generalisation in the rigorous sense
- The right question is: does pretraining actually help on *your* target task with *your* available labels?

---

## Progress

- [ ] SimCLR and MoCo (core contrastive methods)
- [ ] BYOL, SimSiam — negative-free methods
- [ ] DINO and MAE — ViT-based SSL
- [ ] Models Genesis and medical SSL
- [ ] SAM and medical SAM variants
- [ ] Medical foundation models landscape
- [ ] Transfusion paper — transfer learning realities
- [ ] Project: Contrastive pretraining pipeline on medical data
- [ ] Project: SAM adaptation for volumetric segmentation
