# Medical Imaging — Registration

Image registration aligns two or more images into a common coordinate space. It is foundational for longitudinal analysis, atlas construction, multi-modal fusion, and surgical planning. This track covers classical methods (ANTs), learning-based deformable registration, and the emerging diffeomorphic deep learning approaches.

---

## Goal

- Understand the mathematics of image registration: similarity metrics, deformation models, regularization
- Know when to use classical (ANTs, Elastix) vs. learning-based (VoxelMorph) approaches
- Implement a learning-based registration network and understand its limitations
- Reason correctly about diffeomorphic constraints and topology preservation

---

## Paper Reading List

### Classical Registration (Background)
| Paper | Notes |
|---|---|
| **[core]** *A survey of medical image registration* — Maintz & Viergever, Medical Image Analysis (1998) | Classic survey; builds the vocabulary and taxonomy |
| *Symmetric diffeomorphic image registration with cross-correlation* — Avants et al. (ANTs), Medical Image Analysis (2008) | ANTs SyN — the classical gold standard for brain MRI registration |
| *elastix: A Toolbox for Intensity-Based Medical Image Registration* — Klein et al. (2010) | Widely used classical toolkit |

### Learning-Based Registration
| Paper | Notes |
|---|---|
| **[core]** *VoxelMorph: A Learning Framework for Deformable Medical Image Registration* — Balakrishnan et al., TMI 2019 | The foundational learning-based registration paper — read carefully |
| **[core]** *Unsupervised Learning of Probabilistic Diffeomorphic Registration for Images and Surfaces* — Dalca et al., MICCAI 2019 | Probabilistic and diffeomorphic extension of VoxelMorph |
| *TransMorph: Transformer for Unsupervised Medical Image Registration* — Chen et al., Medical Image Analysis 2022 | Transformer-based registration — strong recent baseline |
| *ViT-V-Net: Vision Transformer for Unsupervised Volumetric Medical Image Registration* — Chen et al. (2021) | ViT applied to registration |
| *Recursive Cascaded Networks for Unsupervised Medical Image Registration* — Zhao et al., ICCV 2019 | Cascaded approach for large deformations |
| *Learning-based Image Registration with Meta-Regularization* — Jia et al., CVPR 2021 | Meta-learning for registration regularization |

### Multimodal Registration
| Paper | Notes |
|---|---|
| *Multimodal Image Registration with Deep Context Reinforcement Learning* — Ma et al. (2017) | Cross-modality (MRI-CT) registration |
| *Synthesis-based MRI-CT registration* — various; see notes/papers/registration | Synthesis as a proxy for cross-modal registration |

### Evaluation
| Paper | Notes |
|---|---|
| *Evaluation of Registration Methods on Thoracic CT: The EMPIRE10 Challenge* — Murphy et al., TMI 2011 | Standard evaluation methodology for registration |

---

## Projects

### 1. VoxelMorph reimplementation
Implement VoxelMorph from scratch in PyTorch (without using the original codebase):
- U-Net-based displacement field predictor
- Spatial transformer network (differentiable warping)
- Loss: NCC or MSE for similarity + diffusion regularization on displacement field
- Train on brain MRI (e.g., OASIS or IXI dataset)
- Evaluate: Dice of propagated labels, % folding voxels (non-diffeomorphic regions), runtime vs. ANTs SyN

### 2. Classical vs. learned registration benchmark
Register a set of MRI scans using ANTs SyN and your VoxelMorph implementation. Compare:
- Dice scores on anatomical structures
- Registration runtime (ANTs is slow; VoxelMorph is fast at inference)
- Failure modes: what cases does each approach handle poorly?
- Folding/non-diffeomorphic deformations

---

## Key Concepts Reference

| Concept | Description |
|---|---|
| Similarity metric | NCC (normalised cross-correlation), MSI, MI for multi-modal, NMI |
| Deformation model | Dense displacement field, B-spline FFD, stationary velocity field (SVF) |
| Diffeomorphic | Smooth, invertible, topology-preserving deformation — critical for anatomical plausibility |
| Spatial transformer | Differentiable image warping — the enabling component for end-to-end learning |
| Regularization | Diffusion, bending energy, total variation — penalises unrealistic deformations |
| Atlas | A reference image (template) representing a population; used for normalisation and label propagation |

---

## Progress

- [ ] Registration survey and vocabulary
- [ ] ANTs SyN — understand the algorithm, run on a dataset
- [ ] VoxelMorph (core) — read carefully
- [ ] Diffeomorphic extensions (Dalca et al.)
- [ ] Transformer-based registration (TransMorph)
- [ ] Multimodal registration
- [ ] Project: VoxelMorph reimplementation from scratch
- [ ] Project: Classical vs. learned registration benchmark
