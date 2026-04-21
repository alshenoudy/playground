# ML Inference

Moving a trained model from a Jupyter notebook to a production system that serves real traffic is a distinct engineering discipline. This track covers everything from ONNX export to batching strategies to latency profiling — the full lifecycle of making ML inference fast and reliable.

---

## Goal

By the end of this track you will be able to:
- Export and serve models using standard formats (ONNX, TorchScript)
- Design and implement batching strategies that maximize throughput under latency constraints
- Profile and identify inference bottlenecks at the system level
- Build a production inference server with proper observability

---

## Prerequisites

- Solid PyTorch experience (you have this)
- Basic Docker and HTTP knowledge
- Familiarity with profiling concepts

---

## Learning Path

### 1. Model Export Formats
- [ ] TorchScript: `torch.jit.trace` vs. `torch.jit.script` — when to use each
- [ ] ONNX: export pipeline, opset versions, common export pitfalls
- [ ] ONNX Runtime: running inference, execution providers (CPU, CUDA)
- [ ] Model quantization: INT8 post-training quantization, dynamic vs. static
- [ ] **Implementation:** Export a trained medical imaging model to ONNX, run it with ONNX Runtime, verify output parity with PyTorch

### 2. Serving Fundamentals
- [ ] Synchronous vs. asynchronous serving
- [ ] The anatomy of an inference server: request parsing, preprocessing, model forward pass, postprocessing, response serialization
- [ ] Latency vs. throughput tradeoff
- [ ] Percentile latency (p50, p95, p99) — why averages lie
- [ ] **Project:** Build a minimal inference server in Python (FastAPI) that serves an ONNX model — include request validation, error handling, and basic logging

### 3. Batching Strategies
- [ ] Static batching: fixed batch size, padding, masking
- [ ] Dynamic batching: accumulate requests over a time window, send when full or timeout expires
- [ ] Continuous batching (for LLMs) — conceptual understanding
- [ ] GPU utilization analysis: how batching affects GPU memory and compute efficiency
- [ ] **Project:** Implement dynamic batching from scratch — build a batching layer that queues incoming inference requests, groups them, runs a batched forward pass, and dispatches results back to individual callers. Benchmark throughput vs. latency tradeoffs.

### 4. Latency Profiling and Optimization
- [ ] Where time goes: network, preprocessing, model forward, postprocessing
- [ ] PyTorch profiler: `torch.profiler`, CUDA events, kernel-level timing
- [ ] ONNX Runtime profiling
- [ ] Operator fusion, kernel selection
- [ ] Mixed precision inference (FP16, BF16)
- [ ] **Project:** Latency audit — take a real model, profile every stage of inference, produce a breakdown report, then apply at least two optimizations and measure the improvement

### 5. Observability and Reliability
- [ ] Metrics to track: request rate, latency percentiles, error rate, GPU utilization, queue depth
- [ ] Prometheus + Grafana: instrument your server, build a dashboard
- [ ] Health checks and readiness probes
- [ ] Graceful degradation: timeouts, circuit breakers, fallbacks
- [ ] **Project:** Add full observability to your inference server — Prometheus metrics, structured logging, health endpoint, and a Grafana dashboard

### 6. Inference at Scale
- [ ] Horizontal scaling: stateless servers, load balancing
- [ ] Model replicas vs. model parallelism for large models
- [ ] Triton Inference Server: model repository, ensemble pipelines, backends
- [ ] **Project:** Deploy your inference server with Triton — configure a model repository, run multiple model instances, benchmark concurrent throughput

---

## Projects

| Project | Description | Key concepts |
|---|---|---|
| ONNX export pipeline | Export + verify model with ONNX Runtime | Export, opsets, parity testing |
| Minimal inference server | FastAPI server serving an ONNX model | Serving fundamentals, API design |
| Dynamic batching engine | Queued batching layer with latency/throughput tradeoff | Batching, concurrency, benchmarking |
| Latency audit | Profile + optimize every stage of inference | Profiling, fusion, mixed precision |
| Observable inference server | Prometheus metrics + Grafana dashboard | Observability, instrumentation |
| Triton deployment | Multi-instance model serving with Triton | Production serving, scaling |

---

## Resources

**Documentation**
- ONNX Runtime docs — onnxruntime.ai
- PyTorch profiler tutorial — pytorch.org
- NVIDIA Triton Inference Server docs

**Papers**
- *Clipper: A Low-Latency Online Prediction Serving System* — Crankshaw et al. (2017)
- *Orca: A Distributed Serving System for Transformer-Based Language Generation* (2022) — continuous batching

**Books / Guides**
- *Designing Machine Learning Systems* — Chip Huyen (chapters on serving and monitoring)

---

## Progress

- [ ] Model export formats
- [ ] Serving fundamentals
- [ ] Batching strategies
- [ ] Latency profiling and optimization
- [ ] Observability and reliability
- [ ] Inference at scale
- [ ] Project: ONNX export pipeline
- [ ] Project: Minimal inference server
- [ ] Project: Dynamic batching engine
- [ ] Project: Latency audit
- [ ] Project: Observable inference server
- [ ] Project: Triton deployment

---

## 7. DICOM-Aware Serving (Clinical Context)

Production clinical ML does not receive JPEG inputs — it receives DICOM. Serving in a hospital environment requires understanding the clinical data format and integration protocols.

- [ ] **DICOM basics for serving:** reading a DICOM series at inference time, extracting pixel data and metadata, handling transfer syntaxes (JPEG2000, uncompressed, etc.)
- [ ] **Preprocessing at inference:** replicate the exact preprocessing applied at training time — spacing, orientation, normalisation — this is where training/serving skew occurs
- [ ] **DICOMweb:** the RESTful API for DICOM — WADO-RS (retrieve), STOW-RS (store), QIDO-RS (query). How clinical systems retrieve and push studies.
- [ ] **DICOM-SEG and DICOM-RT:** standard formats for returning segmentation results back into the clinical workflow — not a PNG, but a DICOM object
- [ ] **OHIF Viewer:** open-source DICOM viewer; how to push segmentation results to it and visualise them
- [ ] **Project:** DICOM-to-DICOM segmentation service — build an inference server that: receives a DICOM series via DICOMweb WADO-RS, preprocesses correctly, runs segmentation, and returns a DICOM-SEG object via STOW-RS. Test end-to-end with OHIF as the viewer.

**Key libraries:** `pydicom`, `pynetdicom`, `highdicom` (DICOM-SEG creation), `orthanc` (open-source DICOM server for local testing)

---

## Progress (updated)

- [ ] Model export formats
- [ ] Serving fundamentals
- [ ] Batching strategies
- [ ] Latency profiling and optimization
- [ ] Observability and reliability
- [ ] Inference at scale
- [ ] DICOM-aware serving
- [ ] Project: ONNX export pipeline
- [ ] Project: Minimal inference server
- [ ] Project: Dynamic batching engine
- [ ] Project: Latency audit
- [ ] Project: Observable inference server
- [ ] Project: Triton deployment
- [ ] Project: DICOM-to-DICOM segmentation service
