# Medical Imaging — Synthesis & Generation

Synthesis addresses a core challenge in medical imaging: data scarcity, annotation cost, and domain shift. This track covers the progression from GANs to diffusion models, with a focus on medical applications — cross-modal synthesis, data augmentation, domain agit codaptation, and anomaly detection.

---

## Goal

- Understand generative model architectures from GANs through diffusion models at a level sufficient to modify and extend them
- Know the evaluation landscape for medical image synthesis — and its pitfalls
- Apply synthesis for practical research goals: augmenting scarce datasets, unpaired domain adaptation, and generating realistic pathology
- Understand when synthesis helps downstream tasks and when it does not

---

## Paper Reading List

### GAN Foundations
| Paper | Notes |
|---|---|
| **[core]** *Generative Adversarial Networks* — Goodfellow et al., NeurIPS 2014 | Original GAN paper |
| **[core]** *Image-to-Image Translation with Conditional Adversarial Networks (Pix2Pix)* — Isola et al., CVPR 2017 | Paired image translation |
| **[core]** *Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks (CycleGAN)* — Zhu et al., ICCV 2017 | Unpaired translation — widely used for cross-modal synthesis |
| *Progressive Growing of GANs for Improved Quality, Stability, and Variation* — Karras et al., ICLR 2018 | High-resolution synthesis technique |

### Medical GAN Applications
| Paper | Notes |
|---|---|
| **[core]** *MedGAN: Medical Image Translation using GANs* — Armanious et al., Computerized Medical Imaging and Graphics 2020 | Comprehensive medical image synthesis framework |
| *Synthetic Data Augmentation using GAN for Improved Liver Lesion Classification* — Frid-Adar et al., ISBI 2018 | GAN augmentation for rare pathology |
| *Unsupervised Anomaly Detection with Generative Adversarial Networks* — Schlegl et al., IPMI 2017 (AnoGAN) | Anomaly detection via reconstruction error |
| *MRI to CT Synthesis using Deep Learning* — various; compare 2–3 approaches | Cross-modal synthesis for radiotherapy planning |

### Diffusion Models
| Paper | Notes |
|---|---|
| **[core]** *Denoising Diffusion Probabilistic Models (DDPM)* — Ho et al., NeurIPS 2020 | Foundational diffusion model paper |
| *Diffusion Models Beat GANs on Image Synthesis* — Dhariwal & Nichol, NeurIPS 2021 | Classifier guidance; quality milestone |
| **[core]** *High-Resolution Image Synthesis with Latent Diffusion Models (LDM/Stable Diffusion)* — Rombach et al., CVPR 2022 | Latent space diffusion — basis for most recent medical work |
| *Solving Inverse Problems in Medical Imaging with Score-Based Generative Models* — Song et al., ICLR 2022 | Diffusion for reconstruction (MRI, CT) |
| *MedDiffusion / MONAI Generative* — (2023, ongoing) | Medical imaging diffusion model frameworks |

### Domain Adaptation
| Paper | Notes |
|---|---|
| *Domain Randomization and Pyramid Consistency: Simulation-to-Real Generalization Without Accessing Target Domain Data* — Yue et al., ICCV 2019 | Domain randomization for robustness |
| *Unsupervised Domain Adaptation by Backpropagation* — Ganin & Lempitsky, ICML 2015 | Gradient reversal for domain-invariant features |
| *Generalizable Cross-modality Medical Image Segmentation via Style Augmentation and Dual Normalization* — Zhou et al., CVPR 2022 | Style-based domain adaptation for segmentation |

---

## Projects

### 1. CycleGAN for cross-modal synthesis
Implement CycleGAN for unpaired MRI ↔ CT synthesis:
- Train on an unpaired MRI/CT dataset (e.g., Gold Atlas or synthRAD)
- Evaluate with FID, SSIM, PSNR — and critically, evaluate downstream task performance (register or segment using synthetic images)
- Ablate the cycle-consistency loss weight: what happens without it?

### 2. Diffusion model for medical image generation
Train a 2D DDPM or LDM on a medical imaging dataset:
- Use MONAI Generative or implement a simplified DDPM from scratch
- Evaluate: FID, MS-SSIM, perceptual quality — but also clinical realism (do generated images contain plausible anatomy?)
- Use generated images for data augmentation and measure downstream segmentation improvement

---

## Evaluation Reference

Synthesis evaluation is notoriously unreliable — pixel metrics don't correlate with clinical utility.

| Metric | What it measures | Caveat |
|---|---|---|
| FID (Fréchet Inception Distance) | Feature-space distribution similarity | Uses ImageNet features — not calibrated for medical images |
| SSIM / MS-SSIM | Structural similarity | Only valid for paired synthesis tasks |
| PSNR | Pixel-level reconstruction error | Only valid for paired tasks; insensitive to clinical quality |
| Downstream task performance | Does synthesis improve segmentation/detection? | The only metric that actually matters for augmentation use cases |
| Expert evaluation / Turing test | Radiologist preference or detection of synthetic images | Gold standard but expensive |

**Rule:** always evaluate synthesis by its downstream effect, not synthesis metrics alone.

---

## Progress

- [ ] GAN foundations (GAN, Pix2Pix, CycleGAN)
- [ ] Medical GAN applications
- [ ] DDPM and diffusion model foundations
- [ ] Latent diffusion models
- [ ] Diffusion for medical imaging
- [ ] Domain adaptation methods
- [ ] Project: CycleGAN cross-modal synthesis
- [ ] Project: Diffusion model for medical image generation
