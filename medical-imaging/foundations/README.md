# Medical Imaging — Foundations

The technical bedrock of working with medical images: formats, coordinate systems, preprocessing, and the tooling ecosystem. Even experienced practitioners have gaps here — understanding DICOM internals, orientation conventions, and resampling correctly prevents subtle bugs that corrupt experiments silently.

---

## Goal

- Handle DICOM and NIfTI files confidently, including edge cases (multi-frame, compressed, broken headers)
- Understand image coordinate systems and orientation — and never mix them up in a pipeline
- Build reusable, correct preprocessing pipelines for MRI and CT
- Know when to use SimpleITK vs. MONAI vs. nibabel vs. pydicom and why

---

## Papers to Read

| Paper | Why |
|---|---|
| *MONAI: An open-source framework for deep learning in healthcare* — Cardoso et al. (2022) | Framework overview and design philosophy |
| *Clinically applicable deep learning for diagnosis and referral in retinal disease* — De Fauw et al., Nature Medicine (2018) | Landmark example of clinical ML pipeline; read for the preprocessing and evaluation sections |

---

## Key Concepts to Know

- **DICOM:** SOP classes, series/study/instance hierarchy, transfer syntaxes, tag structure, multi-frame vs. single-frame, DICOM-SEG and DICOM-RT for segmentation outputs
- **NIfTI:** header fields (pixdim, sform/qform, dim), affine matrix, orientation codes (RAS, LAS, etc.)
- **Coordinate systems:** voxel space vs. world/physical space vs. scanner space; the affine transform connecting them
- **Orientation:** RAS+ convention, the confusion between radiological and neurological display conventions
- **Resampling:** trilinear, nearest-neighbour, B-spline — when each is appropriate (especially for label maps vs. images)
- **Intensity normalization:** z-score, percentile clipping, histogram matching, N4 bias field correction for MRI
- **CT-specific:** Hounsfield units, windowing, table/bed removal, lung/bone/soft tissue windows
- **MRI-specific:** sequence types (T1, T2, FLAIR, DWI, ADC), field strength effects, scanner variability

---

## Projects

### 1. DICOM → NIfTI preprocessing pipeline
Build a robust pipeline that:
- Reads a DICOM series (handle multi-frame and single-frame)
- Converts to NIfTI preserving the physical affine
- Validates orientation and reorients to RAS+
- Applies modality-specific normalization (z-score for MRI, HU windowing for CT)
- Saves with correct header metadata
- Handles and logs edge cases rather than silently failing

Tools: `pydicom`, `SimpleITK`, `nibabel`

### 2. Preprocessing audit tool
Build a CLI tool that takes a directory of NIfTI files and produces a report covering:
- Spacing/resolution distribution
- Orientation consistency
- Intensity statistics (mean, std, percentiles, histogram)
- Anisotropy flags (highly anisotropic volumes)
- Missing slices or corrupted files

This is the kind of tool you will use at the start of every new dataset.

---

## Tooling Reference

| Tool | Use case |
|---|---|
| `pydicom` | Read/write DICOM files, access tags |
| `SimpleITK` | Image I/O, resampling, registration, format conversion |
| `nibabel` | NIfTI/MGH I/O, affine manipulation |
| `MONAI` | Medical imaging transforms, dataloaders, training infrastructure |
| `itk` | Low-level ITK bindings, advanced filtering |
| `totalsegmentator` | Rapid anatomical segmentation for preprocessing/cropping |

---

## Datasets to Know

| Dataset | Modality | Task | Access |
|---|---|---|---|
| Medical Segmentation Decathlon (MSD) | MRI, CT | Multi-organ segmentation | medicaldecathlon.com |
| TCIA collections | Multi | Various | cancerimagingarchive.net |
| ADNI | MRI | Alzheimer's / neuroimaging | adni.loni.usc.edu |
| UK Biobank | MRI, CT | Population imaging | ukbiobank.ac.uk |
| LIDC-IDRI | CT | Lung nodule detection | TCIA |

---

## Progress

- [ ] Understand DICOM hierarchy and tag structure
- [ ] Understand NIfTI affine and orientation conventions
- [ ] Understand coordinate system transforms (voxel ↔ world)
- [ ] Know resampling strategies for images vs. label maps
- [ ] MRI normalization and bias field correction
- [ ] CT Hounsfield units and windowing
- [ ] Project: DICOM → NIfTI preprocessing pipeline
- [ ] Project: Preprocessing audit CLI tool
