# Paper Reproduction

Reproducing a published result is one of the most effective ways to deeply understand a method. It forces you to engage with every detail — the ones the paper explains and, critically, the ones it doesn't. This document describes a systematic workflow for faithful paper reproduction.

---

## Goal

- Develop a disciplined, repeatable process for reproducing published results
- Build the habit of reading papers at implementation depth, not just conceptual depth
- Identify where papers are underspecified and develop strategies for filling in the gaps
- Build a personal library of clean, well-understood implementations

---

## Why Reproduce Papers

- **Deep understanding:** You cannot claim to understand a method until you can implement it from scratch
- **Baseline quality:** Your experiments are only as strong as your baseline — if you reproduce nnU-Net, you know your baseline is correct
- **Research intuition:** Repeated reproduction builds intuition for what implementation details actually matter
- **Finding gaps:** Reproduction surfaces what a paper omits — this is often where research opportunities hide

---

## The Reproduction Workflow

Follow these steps in order for every paper you reproduce. Do not skip steps.

---

### Step 1 — Read at three depths

**First pass (20 min):** Abstract, introduction, conclusion, figures and tables only. Answer:
- What problem does this paper solve?
- What is the claimed contribution?
- What are the main results?

**Second pass (1–2 hours):** Full paper, skip maths proofs. Answer:
- What is the method, at a high level?
- What dataset(s) and evaluation protocol?
- What baselines are used?
- What implementation details are given?

**Third pass (full depth):** Every equation, every figure, supplementary material. Answer:
- Can you derive the key equations yourself?
- What is underspecified? (List every missing detail explicitly)
- What would you need to implement this?

---

### Step 2 — Find the implementation landscape

Before writing a line of code:
- [ ] Does an official implementation exist? If so, read it — don't run it yet
- [ ] Are there community reproductions? Check Papers With Code, GitHub
- [ ] Are there related implementations (same architecture, different paper) you can learn from?
- [ ] List every dependency: datasets, pretrained weights, specific library versions mentioned

---

### Step 3 — List what is underspecified

Write down every implementation detail the paper does not fully specify. Common gaps:
- Weight initialisation strategy
- Exact augmentation parameters (rotation range, flip probability, etc.)
- Learning rate schedule details (warmup steps, decay factor)
- Loss function weighting when multiple losses are combined
- Patch sampling strategy for 3D volumes
- Batch normalisation vs. instance normalisation choice
- Inference procedure (sliding window overlap, test-time augmentation)

For each gap, write your best guess based on related work, then note what you will test if results don't match.

---

### Step 4 — Implement incrementally

Do not implement everything at once. Build and verify layer by layer:

1. Data loading: verify shapes, intensities, label distributions match what the paper describes
2. Architecture: verify parameter count matches (if reported), verify output shapes
3. Forward pass: verify loss values are in a sensible range on a single batch
4. Training loop: overfit on a single batch first — if the model can't overfit one batch, something is wrong
5. Full training: run with the paper's hyperparameters first, before tuning anything

Commit after each verified step.

---

### Step 5 — Compare results

- Run on the same dataset and split as the paper
- Report the gap between your result and the paper's result
- Acceptable gap: within ~1% Dice for segmentation tasks, given dataset and split ambiguity
- If the gap is large (>3%), systematically investigate: data preprocessing, augmentation, LR schedule, loss weights
- Document every change you make to close the gap

---

### Step 6 — Document findings

Write a reproduction report (add it to `notes/papers/<task>/`) covering:
- What the paper claims
- What you implemented
- What was underspecified and how you resolved it
- Your results vs. reported results
- What you would do differently

---

## Red Flags in Papers (Read Critically)

| Red flag | What it might mean |
|---|---|
| No standard deviation reported | Possibly single run — results may not be robust |
| Evaluation on proprietary dataset only | Cannot verify independently |
| Baselines without citations or reimplementations | May be unfair comparisons |
| Missing ablation of the most important component | May not hold up to scrutiny |
| "We tune all baselines" without details | Tuning effort may not be equal |
| Results close to human performance on hard tasks | Verify the evaluation protocol carefully |

---

## Suggested Papers to Reproduce

Start with well-known methods with available official code — use the code as ground truth for your implementation.

| Paper | Task | Difficulty | Official code? |
|---|---|---|---|
| U-Net | Segmentation | Low | Yes |
| nnU-Net | Segmentation | High | Yes — reproduce the logic, not just run it |
| VoxelMorph | Registration | Medium | Yes |
| SimCLR | Representation | Medium | Yes |
| CycleGAN | Synthesis | Medium | Yes |
| DDPM | Synthesis | High | Yes |

---

## Progress

- [ ] Read workflow understood and applied to first paper
- [ ] First reproduction complete (U-Net or equivalent)
- [ ] Second reproduction complete (a paper in your specific research area)
- [ ] Reproduction reports written and filed in `notes/papers/`
