# Linear Algebra

Deep understanding of linear algebra through Python implementation. The goal is not to memorize formulas but to build intuition by coding every concept from scratch — using NumPy only after you've implemented the idea yourself.

---

## Goal

By the end of this track you will be able to:
- Implement core matrix operations, decompositions, and solvers from scratch
- Understand why and how decompositions like SVD and eigendecomposition work geometrically
- Apply these tools to real ML problems: PCA, low-rank approximation, least squares, and more
- Read and understand linear algebra in ML papers without reaching for a textbook

---

## Prerequisites

- Python proficiency (you have this)
- Comfort with basic matrix/vector notation
- NumPy familiarity (for verification — not as a crutch)

---

## Learning Path

Work through topics in order. Each topic ends in a project or implementation milestone.

### 1. Foundations
- [ ] Vectors: addition, scaling, dot product, norms, angles
- [ ] Matrices: multiplication, transpose, rank, identity, inverse
- [ ] Systems of linear equations: row reduction, Gaussian elimination
- [ ] **Implementation:** Gaussian elimination solver from scratch

### 2. Vector Spaces
- [ ] Span, linear independence, basis, dimension
- [ ] Column space, null space, row space
- [ ] Change of basis
- [ ] **Implementation:** Build a basis finder — given a set of vectors, extract a linearly independent basis

### 3. Matrix Decompositions
- [ ] LU decomposition — what it is, why it matters for solving systems
- [ ] QR decomposition — orthogonalization via Gram-Schmidt
- [ ] Eigenvalues and eigenvectors — geometric interpretation, power iteration
- [ ] **Implementation:** QR algorithm for eigenvalue computation from scratch

### 4. The Singular Value Decomposition (SVD)
- [ ] Derivation of SVD from eigendecomposition of AᵀA
- [ ] Geometric interpretation: rotation, scaling, rotation
- [ ] Truncated SVD and low-rank approximation
- [ ] **Project:** SVD-based image compression — compress grayscale images at varying rank-k approximations, plot reconstruction error vs. rank

### 5. Applications to ML
- [ ] PCA as eigendecomposition of the covariance matrix
- [ ] PCA via SVD — why this is numerically preferred
- [ ] Least squares: normal equations and pseudoinverse
- [ ] **Project:** PCA from scratch — implement PCA using your own SVD, apply to a dataset (e.g., MNIST or medical image embeddings), visualize explained variance and projections

### 6. Advanced Topics
- [ ] Matrix calculus: gradients of matrix expressions (essential for ML)
- [ ] Positive definite matrices and their role in optimization
- [ ] Kronecker products and vectorization (appear in deep learning theory)
- [ ] **Implementation:** Verify matrix gradient formulas by finite differences

---

## Projects

| Project | Description | Key concepts |
|---|---|---|
| Gaussian elimination solver | Solve Ax=b without `np.linalg.solve` | Row reduction, pivoting |
| QR decomposition from scratch | Gram-Schmidt orthogonalization | Orthonormal bases, projections |
| Eigenvalue solver (power iteration + QR shift) | Find eigenvalues iteratively | Convergence, numerical stability |
| SVD-based image compression | Compress images at rank k, visualize quality vs. rank | SVD, low-rank approximation |
| PCA from scratch | Full PCA pipeline using your own SVD | Covariance, eigendecomposition, projection |
| Matrix calculus verifier | Implement and verify d/dX [tr(AX)] and similar | Matrix derivatives, finite differences |

---

## Resources

**Books**
- *Linear Algebra Done Right* — Sheldon Axler (theory, proof-based)
- *Introduction to Linear Algebra* — Gilbert Strang (applied, intuitive)
- *Mathematics for Machine Learning* — Deisenroth, Faisal, Ong (free online, ML-focused — start here)

**Courses**
- Gilbert Strang MIT 18.06 (OCW) — best lecture series on applied linear algebra
- 3Blue1Brown *Essence of Linear Algebra* — geometric intuition before coding

**Reference**
- *The Matrix Cookbook* — dense reference for matrix identities and derivatives

---

## Progress

- [ ] Foundations
- [ ] Vector spaces
- [ ] Matrix decompositions
- [ ] SVD
- [ ] Applications to ML
- [ ] Advanced topics
- [ ] Project: Gaussian elimination solver
- [ ] Project: QR decomposition
- [ ] Project: Eigenvalue solver
- [ ] Project: SVD image compression
- [ ] Project: PCA from scratch
- [ ] Project: Matrix calculus verifier
