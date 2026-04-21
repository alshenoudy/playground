# Playground

Personal learning repo. Medical imaging is the domain — everything else is in service of it.

The rule: implement, implement, implement.

---

## Before anything else — the boring stuff

Fundamentals that make you faster everywhere else.

**Python — the parts you skip when things are working**
- [ ] The GIL: what it actually prevents and why `multiprocessing` exists
- [ ] Generators and `yield from` — when they matter for memory
- [ ] How `@property`, `@staticmethod`, `@classmethod` work under the hood
- [ ] Python's memory model: reference counting, cyclic GC, `__slots__`
- [ ] Context managers: write one with `__enter__`/`__exit__`, then with `contextlib.contextmanager`
- [ ] Decorators with arguments — write one from scratch, not from memory
- [ ] `asyncio`: when it helps and when it doesn't
- [ ] The import system: `sys.path`, `__init__.py`, relative imports, circular import failures

Full learning plan: [engineering/software-engineering/python](./engineering/software-engineering/python/README.md)

**Data structures and algorithms**
Not for interviews. For the moments when your data pipeline is mysteriously O(n²).
- [ ] Complexity by feel: O(1), O(log n), O(n log n), O(n²) — know which operations fall where in Python
- [ ] Implement: dynamic array, linked list, stack, queue, min-heap
- [ ] Hash maps: collision resolution, load factor, why dict lookup is O(1) amortised not O(1) always
- [ ] Trees: BST insert/search/delete, DFS/BFS traversal, height, balance
- [ ] Graphs: adjacency list vs matrix, BFS, DFS, shortest path (Dijkstra)
- [ ] Dynamic programming: memoisation vs tabulation; solve 5 problems

**Linux**
Your models run on Linux. Know the OS.
- [ ] `htop`, `nvidia-smi`, `iostat`, `nethogs` — read these fluently while a training job runs
- [ ] `tmux`: never lose a training run to a dropped SSH connection
- [ ] `find`, `grep`, `awk`, `xargs` — compose them to answer dataset questions in seconds
- [ ] `CUDA_VISIBLE_DEVICES`, `LD_LIBRARY_PATH`, `PATH` — understand what they do, don't just copy-paste
- [ ] Write a bash script: end-to-end dataset preprocessing, with error handling and logging
- [ ] `strace`, `lsof`, `ps aux` — when Python tracebacks stop being enough

Full learning plan: [engineering/software-engineering/linux](./engineering/software-engineering/linux/README.md)

**Git**
Your commit history is your intellectual audit trail. Treat it that way.
- [ ] `git rebase` vs `git merge` — know when to use each
- [ ] `git bisect` — binary search through commits to find a regression
- [ ] `git reflog` — how to recover from the mistakes that feel unrecoverable
- [ ] Commit message discipline: one idea per commit, written so future-you isn't confused
- [ ] Tagging: `v1.0-miccai-submission` is a real workflow

Full learning plan: [engineering/software-engineering/git](./engineering/software-engineering/git/README.md)

---

## Medical Imaging

The domain. Everything else feeds into this.

| | |
|---|---|
| [foundations](./medical-imaging/foundations/README.md) | DICOM/NIfTI, coordinate systems, preprocessing |
| [segmentation](./medical-imaging/segmentation/README.md) | U-Net family, nnU-Net, loss functions, evaluation |
| [detection](./medical-imaging/detection/README.md) | 3D lesion detection, FROC, nnDetection |
| [registration](./medical-imaging/registration/README.md) | ANTs, VoxelMorph, TransMorph |
| [synthesis](./medical-imaging/synthesis/README.md) | CycleGAN, diffusion models, domain adaptation |
| [representation](./medical-imaging/representation/README.md) | Contrastive SSL, DINO, medical foundation models |

---

## Foundations

The math behind the models. Implementations in Python, applied to medical imaging problems.

| | |
|---|---|
| [linear-algebra](./foundations/math/linear-algebra/README.md) | Vectors, matrices, decompositions |
| [calculus-optimization](./foundations/math/calculus-optimization/README.md) | Autodiff from scratch, gradient-based optimizers |
| [probability-statistics](./foundations/math/probability-statistics/README.md) | Bayesian inference, MCMC, uncertainty quantification |

---

## Engineering

How to build systems that actually work in production.

**Systems**
| | |
|---|---|
| [go](./engineering/systems/go/README.md) | Go fundamentals → concurrency → gRPC services |

**ML Systems**
| | |
|---|---|
| [inference](./engineering/ml-systems/inference/README.md) | Model serving, batching, DICOM-aware deployment |
| [pipelines](./engineering/ml-systems/pipelines/README.md) | Feature pipelines, data versioning, orchestration |
| [distributed](./engineering/ml-systems/distributed/README.md) | Distributed training, gradient compression |

**Software Engineering**
| | |
|---|---|
| [design-patterns](./engineering/software-engineering/design-patterns/README.md) | Patterns in Python and Go |
| [distributed-systems](./engineering/software-engineering/distributed-systems/README.md) | Consensus, replication, message queues |
| [devops](./engineering/software-engineering/devops/README.md) | Docker, Kubernetes, CI/CD, Terraform |

---

## Research

Methodology — the parts of research that aren't taught but matter.

| | |
|---|---|
| [experiment-tracking](./research/experiment-tracking/README.md) | W&B, MLflow, Hydra |
| [reproducibility](./research/reproducibility/README.md) | Seeds, determinism, Docker, DVC |
| [evaluation](./research/evaluation/README.md) | Statistical testing, bootstrap CI, clinical metrics |
| [ablations](./research/ablations/README.md) | Ablation design, pre-experiment planning |
| [paper-reproduction](./research/paper-reproduction/README.md) | Workflow for reproducing published results |

---

## Projects + Notes

| | |
|---|---|
| [projects](./projects/README.md) | End-to-end projects crossing multiple domains |
| [notes](./notes/resources.md) | Resources, paper summaries, weekly research log |
