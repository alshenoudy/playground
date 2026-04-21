# Resources

Curated references across all learning domains. Organized by domain. Quality over quantity — only resources worth your time are listed here.

---

## Mathematics

### Linear Algebra
| Resource | Type | Notes |
|---|---|---|
| *Mathematics for Machine Learning* — Deisenroth, Faisal, Ong | Book (free PDF) | Start here. ML-focused, covers all three math domains |
| *Introduction to Linear Algebra* — Gilbert Strang | Book | Best applied linear algebra text. Pairs with MIT 18.06 |
| *Linear Algebra Done Right* — Axler | Book | Proof-based, builds deep theoretical intuition |
| MIT 18.06 Linear Algebra — Gilbert Strang | Course (OCW, free) | Best lecture series on the subject |
| 3Blue1Brown: Essence of Linear Algebra | Video series | Watch before coding — builds geometric intuition |
| *The Matrix Cookbook* | Reference PDF | Dense reference for matrix identities and derivatives |

### Calculus & Optimization
| Resource | Type | Notes |
|---|---|---|
| *Mathematics for Machine Learning* — Deisenroth et al. | Book (free PDF) | Chapters 5–7 |
| *Convex Optimization* — Boyd & Vandenberghe | Book (free PDF) | The definitive reference on convex opt |
| *Deep Learning* — Goodfellow, Bengio, Courville | Book (free online) | Chapters 4 and 8 for optimization |
| Andrej Karpathy: micrograd | Code + video | Watch before building your own autodiff engine |
| Stanford CS229 Lecture Notes | Notes (free) | Concise, ML-focused treatment of optimization |

### Probability & Statistics
| Resource | Type | Notes |
|---|---|---|
| *Pattern Recognition and Machine Learning* — Bishop | Book | Probabilistic ML bible. Dense but comprehensive. |
| *Information Theory, Inference, and Learning Algorithms* — MacKay | Book (free PDF) | Unique perspective connecting information theory and inference |
| *Bayesian Data Analysis* — Gelman et al. | Book | Deep Bayesian intuition and practice |
| Cambridge MacKay Lectures | Video (YouTube) | Companion to the book above |
| Coursera: Probabilistic Graphical Models — Koller | Course | Rigorous treatment of graphical models and inference |

---

## Systems

### Go
| Resource | Type | Notes |
|---|---|---|
| *The Go Programming Language* — Donovan & Kernighan | Book | The definitive Go reference |
| *Concurrency in Go* — Katherine Cox-Buday | Book | Deep dive into Go's concurrency model |
| *100 Go Mistakes and How to Avoid Them* — Harsanyi | Book | Read after basics, prevents bad habits |
| go.dev/tour | Interactive | Day-one introduction |
| Effective Go — go.dev/doc/effective_go | Guide | Idiomatic Go patterns. Read early, revisit often. |
| Rob Pike: Concurrency is not Parallelism | Talk (YouTube) | Essential mental model for goroutines |

---

## ML Systems

### Inference
| Resource | Type | Notes |
|---|---|---|
| *Designing Machine Learning Systems* — Chip Huyen | Book | Most practical ML systems book. Start with chapters on serving. |
| ONNX Runtime documentation | Docs | onnxruntime.ai |
| NVIDIA Triton Inference Server documentation | Docs | For production multi-model serving |
| *Clipper: A Low-Latency Online Prediction Serving System* — Crankshaw et al. | Paper (2017) | Foundational inference serving paper |
| *Orca: Continuous Batching for LLM Serving* | Paper (2022) | Key paper on continuous batching |

### Pipelines
| Resource | Type | Notes |
|---|---|---|
| *Designing Machine Learning Systems* — Chip Huyen | Book | Chapters on feature stores, pipelines, and monitoring |
| *Fundamentals of Data Engineering* — Reis & Housley | Book | Data engineering foundations |
| *Hidden Technical Debt in ML Systems* — Sculley et al. (Google) | Paper (2015) | Essential reading. Read this early. |
| DVC documentation | Docs | dvc.org |
| Prefect documentation | Docs | docs.prefect.io |

### Distributed Training
| Resource | Type | Notes |
|---|---|---|
| PyTorch Distributed documentation | Docs | pytorch.org/tutorials/distributed |
| *Accurate, Large Minibatch SGD* — Goyal et al. | Paper (2017) | Training at scale, learning rate scaling rules |
| *ZeRO: Memory Optimizations Toward Training Trillion Parameter Models* — Rajbhandari et al. | Paper (2020) | Foundation of modern large model training |
| *Horovod: fast and easy distributed deep learning* — Sergeev & Del Balso | Paper (2018) | Ring all-reduce in practice |
| *Deep Gradient Compression* — Lin et al. | Paper (2018) | Gradient sparsification with error feedback |
| *GPipe: Pipeline Parallelism* — Huang et al. | Paper (2019) | Pipeline parallel training |

---

## Software Engineering

### Design Patterns
| Resource | Type | Notes |
|---|---|---|
| *Design Patterns* — Gang of Four | Book | Original reference. Language-agnostic. |
| *Head First Design Patterns* — Freeman & Robson | Book | More accessible entry point |
| *A Philosophy of Software Design* — Ousterhout | Book | Higher-level design principles beyond patterns |

### Distributed Systems
| Resource | Type | Notes |
|---|---|---|
| *Designing Data-Intensive Applications* — Kleppmann | Book | Read cover to cover. Best distributed systems book for practitioners. |
| *The Raft Consensus Algorithm* — Ongaro & Ousterhout | Paper (2014) | Read alongside your Raft implementation |
| *Dynamo: Amazon's Highly Available Key-value Store* | Paper (2007) | Foundational paper on eventual consistency |
| *Kafka: a Distributed Messaging System for Log Processing* — Kreps et al. | Paper (2011) | Kafka architecture |
| MIT 6.824 Distributed Systems | Course (free, labs in Go) | Best distributed systems course. Labs are essential. |

### DevOps & Infrastructure
| Resource | Type | Notes |
|---|---|---|
| *Kubernetes: Up and Running* — Burns, Beda, Hightower | Book | Practical Kubernetes reference |
| *Terraform: Up and Running* — Brikman | Book | Hands-on IaC with Terraform |
| *The DevOps Handbook* — Kim, Humble, Debois | Book | Culture, practices, and philosophy |
| Kubernetes the Hard Way — Kelsey Hightower | Guide (GitHub) | Set up K8s from scratch to understand internals |
| Kubernetes official documentation | Docs | kubernetes.io/docs — excellent official docs |

---

## Medical Imaging & Domain-Specific

### Books & Reference
| Resource | Type | Notes |
|---|---|---|
| *Deep Learning for Medical Image Analysis* — Zhou, Greenspan, Shen | Book | Comprehensive DL in medical imaging coverage |
| *Medical Image Analysis* — Sonka, Hlavac, Boyle | Book | Classical methods; essential background |
| MONAI documentation and tutorials | Docs + code | PyTorch-based medical imaging framework |
| SimpleITK documentation + Jupyter notebooks | Docs + notebooks | Best resource for image I/O, resampling, registration |
| *The Matrix Cookbook* | Reference | Useful for the linear algebra in registration and shape analysis |

### Research Venues (follow these)
| Venue | Type | Focus |
|---|---|---|
| MICCAI | Conference (top) | All medical image computing — the primary venue |
| MIDL (Medical Imaging with Deep Learning) | Conference | DL-focused; fast turnaround; good for methods work |
| Medical Image Analysis (MedIA) | Journal | High-impact journal; methods + clinical validation |
| IEEE Transactions on Medical Imaging (TMI) | Journal | Broad medical imaging methods |
| Nature Methods / Nature Medicine | Journal | High-impact clinical ML results |
| IPMI | Conference | Small, theory-heavy; registration, shape, statistical methods |

### Foundational Papers (read early in the PhD)
| Paper | Notes |
|---|---|
| *U-Net* — Ronneberger et al., MICCAI 2015 | The segmentation baseline |
| *nnU-Net* — Isensee et al., Nature Methods 2021 | Current gold standard; study the method deeply |
| *VoxelMorph* — Balakrishnan et al., TMI 2019 | Foundational learning-based registration |
| *Models Genesis* — Zhou et al., MICCAI 2019 | Medical SSL pretraining |
| *Hidden Technical Debt in ML Systems* — Sculley et al. (2015) | Essential for any production ML work |
| *Transfusion* — Raghu et al., NeurIPS 2019 | Transfer learning realities for medical imaging |
| *Common Limitations of Image Processing Metrics* — Reinke et al., Nature Methods 2022 | Read before designing any evaluation |

### Datasets
| Dataset | Modality | Task | Access |
|---|---|---|---|
| Medical Segmentation Decathlon (MSD) | MRI + CT | Multi-organ segmentation (10 tasks) | medicaldecathlon.com |
| TCIA (The Cancer Imaging Archive) | Multi | Various oncology tasks | cancerimagingarchive.net |
| ADNI (Alzheimer's Disease Neuroimaging Initiative) | MRI | Neuroimaging, longitudinal | adni.loni.usc.edu |
| UK Biobank | MRI + CT | Large-scale population imaging | ukbiobank.ac.uk (access required) |
| LIDC-IDRI | CT | Lung nodule detection (4 radiologist annotations) | TCIA |
| OASIS | MRI | Brain aging + Alzheimer's; used in registration benchmarks | oasis-brains.org |
| IXI | MRI | Healthy brain MRI; common registration benchmark | brain-development.org |
| ACDC (Automated Cardiac Diagnosis Challenge) | MRI | Cardiac segmentation | creatis.insa-lyon.fr/Challenge/acdc |
| BraTS (Brain Tumor Segmentation Challenge) | MRI (multi-modal) | Glioma segmentation | synapse.org/brats |
| Gold Atlas | MRI + CT | Head & neck, prostate; used in registration | goldatlas.org |

### Clinical Context
| Resource | Type | Notes |
|---|---|---|
| *Artificial Intelligence in Medicine* — Topol | Book | Broad clinical AI landscape and its limits |
| *Proposed Regulatory Framework for Modifications to AI/ML-Based SaMD* — FDA | Regulatory doc | How AI gets approved for clinical use in the US |
| *A guide to deep learning in healthcare* — Esteva et al., Nature Medicine 2019 | Review paper | Overview of DL across clinical domains |

---

## Cross-Cutting

| Resource | Type | Notes |
|---|---|---|
| *The Pragmatic Programmer* — Hunt & Thomas | Book | Software craftsmanship principles |
| *Clean Code* — Robert Martin | Book | Writing maintainable code — controversial but useful |
| *Systems Performance* — Brendan Gregg | Book | Deep performance engineering reference |
| Papers With Code — paperswithcode.com | Site | Track SOTA, find implementations |
