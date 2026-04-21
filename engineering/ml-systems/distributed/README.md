# Distributed ML

Training large models efficiently across multiple GPUs and machines is a core skill for production ML teams. This track covers the systems and algorithms behind distributed training: communication primitives, parallelism strategies, gradient compression, and fault tolerance.

---

## Goal

By the end of this track you will be able to:
- Understand and implement the major parallelism strategies used in distributed training
- Reason about communication overhead and optimize collective operations
- Implement gradient compression techniques from the research literature
- Design fault-tolerant training systems that recover from worker failures

---

## Prerequisites

- Strong PyTorch experience, including writing custom training loops
- Basic understanding of GPU architecture (what a CUDA kernel is, memory hierarchy)
- Familiarity with Linux networking concepts (TCP, sockets) at a high level
- Complete the ML inference track first (shared systems knowledge)

---

## Learning Path

### 1. Distributed Systems Fundamentals for ML
- [ ] Process groups, ranks, world size — the vocabulary of distributed training
- [ ] Point-to-point communication: send/recv
- [ ] Collective operations: broadcast, reduce, all-reduce, all-gather, scatter
- [ ] Ring all-reduce: how Horovod and NCCL implement it efficiently
- [ ] **Implementation:** Implement ring all-reduce from scratch using Python multiprocessing — simulate N workers averaging gradients without a central parameter server

### 2. Data Parallelism
- [ ] Synchronous data parallelism: replicate model, split data, average gradients
- [ ] PyTorch `DistributedDataParallel` (DDP): how it works under the hood, gradient bucketing
- [ ] Asynchronous data parallelism: stale gradients, convergence implications
- [ ] Large-batch training challenges: generalization gap, learning rate scaling rules
- [ ] **Project:** Implement data parallel training from scratch — without DDP, manually replicate gradients across processes using `torch.distributed`, verify convergence matches single-GPU training

### 3. Model Parallelism
- [ ] Tensor parallelism: split individual layers across devices (Megatron-style)
- [ ] Pipeline parallelism: split model by layers, micro-batching to fill the pipeline
- [ ] 3D parallelism: combining data + tensor + pipeline parallelism
- [ ] **Implementation:** Implement naive pipeline parallelism — split a simple MLP across 2 GPUs (or CPU processes), implement micro-batching with GPipe-style scheduling, measure pipeline bubble overhead

### 4. Gradient Compression
- [ ] Why compression: communication is often the bottleneck, not compute
- [ ] Gradient sparsification: top-k, random-k sparsification
- [ ] Gradient quantization: 1-bit SGD, QSGD
- [ ] Error feedback: accumulating compression error to avoid divergence
- [ ] **Project:** Implement top-k gradient sparsification with error feedback — train a small network with and without compression, measure communication reduction and convergence impact

### 5. Parameter Servers
- [ ] Parameter server architecture: workers push gradients, servers apply updates
- [ ] Consistency models: synchronous (BSP), asynchronous (ASP), stale synchronous (SSP)
- [ ] Limitations of parameter servers at scale (why all-reduce won over PS for large models)
- [ ] **Project:** Build a minimal parameter server — a central server process and N worker processes. Workers compute gradients and push to the server; server applies SGD and broadcasts updated weights. Support both sync and async modes.

### 6. Fault Tolerance and Checkpointing
- [ ] Failure modes in distributed training: worker crashes, network partitions, GPU errors
- [ ] Checkpoint strategies: full checkpoints, incremental, async checkpointing
- [ ] Elastic training: adding/removing workers without restarting the job
- [ ] **Implementation:** Add fault-tolerant checkpointing to your data parallel training — detect worker failure, reload from last checkpoint, continue training

---

## Projects

| Project | Description | Key concepts |
|---|---|---|
| Ring all-reduce from scratch | N-process gradient averaging via ring | Collective ops, communication |
| Data parallel training from scratch | Manual DDP without PyTorch's DDP | Data parallelism, `torch.distributed` |
| Pipeline parallel MLP | 2-stage pipeline with micro-batching | Pipeline parallelism, bubble overhead |
| Gradient sparsification | Top-k compression with error feedback | Gradient compression, convergence |
| Minimal parameter server | Sync + async PS with N workers | Parameter server architecture |
| Fault-tolerant training | Checkpointing + worker failure recovery | Fault tolerance, elastic training |

---

## Resources

**Papers**
- *Accurate, Large Minibatch SGD: Training ImageNet in 1 Hour* — Goyal et al., Facebook (2017)
- *Horovod: fast and easy distributed deep learning in TensorFlow* — Sergeev & Del Balso (2018)
- *ZeRO: Memory Optimizations Toward Training Trillion Parameter Models* — Rajbhandari et al. (2020)
- *GPipe: Efficient Training of Giant Neural Networks using Pipeline Parallelism* — Huang et al. (2019)
- *Deep Gradient Compression* — Lin et al. (2018)

**Documentation**
- PyTorch Distributed docs — pytorch.org/tutorials/distributed
- NCCL documentation — developer.nvidia.com/nccl

**Books**
- *Designing Distributed Systems* — Burns (patterns for distributed systems, useful context)

---

## Progress

- [ ] Distributed systems fundamentals for ML
- [ ] Data parallelism
- [ ] Model parallelism
- [ ] Gradient compression
- [ ] Parameter servers
- [ ] Fault tolerance and checkpointing
- [ ] Project: Ring all-reduce from scratch
- [ ] Project: Data parallel training from scratch
- [ ] Project: Pipeline parallel MLP
- [ ] Project: Gradient sparsification
- [ ] Project: Minimal parameter server
- [ ] Project: Fault-tolerant training
