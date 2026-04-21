# Calculus & Optimization

Calculus and optimization are the engine of machine learning. This track focuses on the mathematics that drives training: derivatives, gradients, backpropagation, and optimization algorithms — all implemented from scratch in Python.

---

## Goal

By the end of this track you will be able to:
- Implement automatic differentiation from scratch
- Understand and implement gradient-based optimizers at the level needed to read optimizer papers
- Solve constrained and unconstrained optimization problems
- Understand the geometry of loss landscapes and why certain optimizers work better than others

---

## Prerequisites

- Linear algebra fundamentals (complete that track first)
- Single-variable calculus (derivatives, chain rule)
- NumPy proficiency

---

## Learning Path

### 1. Multivariate Calculus
- [ ] Partial derivatives and the gradient vector
- [ ] Directional derivatives and the Jacobian matrix
- [ ] The Hessian: second-order information, curvature
- [ ] Chain rule in multiple dimensions
- [ ] **Implementation:** Numerical gradient checker — verify analytical gradients using finite differences

### 2. Automatic Differentiation
- [ ] Forward mode vs. reverse mode autodiff
- [ ] Computation graphs: nodes, edges, forward pass, backward pass
- [ ] Reverse mode as generalized backpropagation
- [ ] **Project:** Build a scalar-valued autodiff engine (like micrograd) supporting +, *, tanh, relu — train a small MLP on a toy dataset

### 3. Gradient Descent and Variants
- [ ] Vanilla gradient descent — convergence conditions, learning rate sensitivity
- [ ] Stochastic and mini-batch gradient descent
- [ ] Momentum: heavy ball method, Nesterov acceleration
- [ ] Adaptive methods: AdaGrad, RMSProp, Adam — derive update rules from scratch
- [ ] **Project:** Optimizer comparison — implement SGD, Momentum, Adam from scratch, benchmark convergence on a quadratic bowl and a non-convex function, plot loss curves

### 4. Convex Optimization
- [ ] Convex sets and convex functions — definitions and why they matter
- [ ] Gradient descent convergence rates for convex and strongly convex functions
- [ ] Lagrange multipliers and constrained optimization
- [ ] KKT conditions
- [ ] **Implementation:** Solve a constrained quadratic program using projected gradient descent

### 5. Second-Order Methods
- [ ] Newton's method — using curvature to accelerate convergence
- [ ] Quasi-Newton methods: L-BFGS (conceptual understanding)
- [ ] Natural gradient and Fisher information matrix (bridge to deep learning)
- [ ] **Implementation:** Newton's method on a 2D non-convex function, compare convergence to gradient descent

### 6. Optimization in Deep Learning
- [ ] Loss landscape geometry: saddle points, flat minima, sharp minima
- [ ] Learning rate schedules: step decay, cosine annealing, warmup
- [ ] Gradient clipping, weight decay as L2 regularization
- [ ] **Project:** Train a small CNN on CIFAR-10 using your own training loop with custom LR schedule and gradient clipping — no PyTorch Lightning or high-level wrappers

---

## Projects

| Project | Description | Key concepts |
|---|---|---|
| Numerical gradient checker | Verify ∂f/∂x via finite differences | Partial derivatives, Jacobian |
| Autodiff engine (micrograd-style) | Scalar autodiff with backprop, train a toy MLP | Computation graphs, reverse mode |
| Optimizer zoo | SGD, Momentum, Adam from scratch with convergence plots | Optimizer math, loss landscapes |
| Constrained optimizer | Projected gradient descent on a QP | Lagrangians, KKT, convexity |
| Newton's method explorer | 2D optimization with curvature visualization | Hessian, second-order methods |
| CNN training loop from scratch | Full training loop with custom optimizer and schedule | End-to-end DL training engineering |

---

## Resources

**Books**
- *Mathematics for Machine Learning* — Deisenroth et al. (chapters 5–7, free online)
- *Convex Optimization* — Boyd & Vandenberghe (free PDF, the definitive reference)
- *Deep Learning* — Goodfellow et al. (chapters 4 and 8 for optimization)

**Courses**
- Stanford CS229 lecture notes on optimization
- Andrej Karpathy's *micrograd* — watch before building your own autodiff engine

**Papers**
- *Adam: A Method for Stochastic Optimization* — Kingma & Ba (2015)
- *On the importance of initialization and momentum in deep learning* — Sutskever et al. (2013)

---

## Progress

- [ ] Multivariate calculus
- [ ] Automatic differentiation
- [ ] Gradient descent and variants
- [ ] Convex optimization
- [ ] Second-order methods
- [ ] Optimization in deep learning
- [ ] Project: Numerical gradient checker
- [ ] Project: Autodiff engine
- [ ] Project: Optimizer zoo
- [ ] Project: Constrained optimizer
- [ ] Project: Newton's method explorer
- [ ] Project: CNN training loop from scratch
