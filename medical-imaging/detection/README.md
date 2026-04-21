# Medical Imaging — Detection

Detection in medical imaging means localizing pathologies, lesions, and anatomical structures in 2D and 3D images. The field has unique challenges compared to natural image detection: extreme class imbalance (most voxels are background), 3D volumetric data, small and subtle targets, and the need for calibrated confidence scores.

---

## Goal

- Understand 2D and 3D object detection architectures adapted for medical imaging
- Know the detection evaluation landscape: FROC, AFROC, JAFROC, mAP — and when to use each
- Be able to design detection pipelines for lesion/nodule detection tasks
- Understand the tradeoffs between detection and segmentation approaches for the same problem

---

## Paper Reading List

### Foundational Detection (General)
| Paper | Notes |
|---|---|
| **[core]** *Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks* — Ren et al., NeurIPS 2015 | Anchor-based two-stage baseline |
| **[core]** *Feature Pyramid Networks for Object Detection* — Lin et al., CVPR 2017 | Multi-scale features — standard in medical detection |
| *RetinaNet: Focal Loss for Dense Object Detection* — Lin et al., ICCV 2017 | Focal loss to handle extreme class imbalance |
| *DETR: End-to-End Object Detection with Transformers* — Carion et al., ECCV 2020 | Transformer-based; growing influence in medical detection |

### Medical Imaging Detection
| Paper | Notes |
|---|---|
| **[core]** *DeepLung: Deep 3D Dual Path Nets for Automated Pulmonary Nodule Detection and Classification* — Zhu et al. (2018) | Comprehensive 3D nodule detection pipeline |
| *3D Context Enhanced Region-based Convolutional Neural Network for End-to-End Lesion Detection* — Yan et al., MICCAI 2018 | 3D detection with contextual features |
| *nnDetection: a Self-configuring Method for Medical Object Detection* — Baumgartner et al., MICCAI 2021 | The nnU-Net equivalent for detection — essential read |
| *Towards Large-Scale Small Object Detection: Survey and Benchmarks* — Cheng et al. (2023) | Directly relevant to small lesion detection |
| *Universal Lesion Detection in CT Scans using Neural Network Ensemble* — Yan et al. (2019) | Multi-class lesion detection; DeepLesion dataset |
| *Anchor-free 3D Single Stage Detector with Mask-Guided Attention for Medical Imaging* — Zhang et al., MICCAI 2022 | Anchor-free approach for 3D medical detection |

### Evaluation Methodology
| Paper | Notes |
|---|---|
| **[core]** *The FROC methodology* — Chakraborty (review chapter) | Free-response ROC — standard for detection evaluation in radiology |
| *Optimizing the free-response receiver operating characteristic curve* — Chakraborty (2011) | JAFROC figure of merit — read before designing any detection evaluation |

---

## Projects

### 1. 3D nodule/lesion detector
Implement a 3D detection pipeline on the LIDC-IDRI (CT lung nodules) or a relevant MSD detection task:
- Data preprocessing: resample to isotropic spacing, normalize HU
- Architecture: 3D FPN backbone + anchor-based detection head (or adapt nnDetection)
- Training: focal loss or sampling strategy to handle extreme background imbalance
- Evaluation: FROC curve, sensitivity at fixed false positive rates (0.125, 0.25, 0.5, 1, 2, 4, 8 FPs/scan)

### 2. Detection vs. segmentation comparison
Pick a task where both detection and segmentation are feasible (e.g., brain metastases, liver lesions). Train both a detection model and a segmentation model. Compare:
- Clinical utility: which output is more actionable?
- Annotation cost: what does each approach require?
- Performance: which finds small lesions better?

Write a short technical note on the tradeoffs.

---

## Evaluation Reference

| Metric | Context |
|---|---|
| FROC curve | Primary evaluation for detection tasks in radiology — plots sensitivity vs. FP/scan |
| Sensitivity @ N FPs/scan | Point metrics from FROC (standard reporting: 0.5, 1, 2, 4 FPs/scan) |
| JAFROC Figure of Merit | Single-number summary of FROC; preferred over AUC of FROC |
| mAP (IoU-based) | Use only when bounding boxes are appropriate; less common in 3D medical detection |
| CPM (Competition Performance Metric) | Average sensitivity at 7 fixed FP rates — used in LUNA16 challenge |

---

## Progress

- [ ] Faster R-CNN and FPN (foundational understanding)
- [ ] Focal loss and RetinaNet
- [ ] DETR and transformer-based detection
- [ ] nnDetection — read paper and run on a task
- [ ] Medical detection papers (DeepLung, lesion detection)
- [ ] FROC methodology and JAFROC
- [ ] Project: 3D nodule/lesion detector with FROC evaluation
- [ ] Project: Detection vs. segmentation comparison + technical note
