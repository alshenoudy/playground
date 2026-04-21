# Probability & Statistics

Probability is the language of uncertainty — and uncertainty is everywhere in ML. This track builds rigorous probabilistic intuition through implementation: from basic distributions to Bayesian inference to sampling algorithms used in modern ML.

---

## Goal

By the end of this track you will be able to:
- Implement and reason about probability distributions from first principles
- Build Bayesian inference pipelines from scratch
- Implement MCMC samplers and understand when and why they work
- Read probabilistic ML papers (VAEs, diffusion models, Bayesian deep learning) with confidence

---

## Prerequisites

- Calculus: integration, partial derivatives (complete that track first)
- Basic probability (random variables, expectation, variance — at undergrad level)
- NumPy and matplotlib proficiency

---

## Learning Path

### 1. Probability Foundations
- [ ] Sample spaces, events, probability axioms
- [ ] Conditional probability and Bayes' theorem
- [ ] Random variables: discrete and continuous
- [ ] Expectation, variance, covariance, correlation
- [ ] **Implementation:** Build a probability toolkit — compute expectations, variances, and marginals by hand using numerical integration and Monte Carlo estimation, compare results

### 2. Distributions
- [ ] Key discrete distributions: Bernoulli, Binomial, Poisson, Categorical
- [ ] Key continuous distributions: Gaussian, Exponential, Beta, Dirichlet, Gamma
- [ ] Multivariate Gaussian: covariance structure, marginals, conditionals
- [ ] Exponential family: unifying framework for common distributions
- [ ] **Implementation:** Implement each distribution from scratch — PDF/PMF, CDF, sampling (without scipy), log-likelihood

### 3. Information Theory
- [ ] Entropy, cross-entropy, KL divergence
- [ ] Mutual information
- [ ] Why KL divergence is not symmetric; when to use which direction
- [ ] **Implementation:** Implement KL divergence between two Gaussians analytically and numerically, verify they match. Visualize KL as a function of distribution parameters.

### 4. Bayesian Inference
- [ ] Prior, likelihood, posterior — the full pipeline
- [ ] Conjugate priors: Beta-Binomial, Gaussian-Gaussian
- [ ] Maximum likelihood estimation (MLE) vs. maximum a posteriori (MAP)
- [ ] Posterior predictive distribution
- [ ] **Project:** Bayesian coin flip — start with a Beta prior, update with Bernoulli observations, visualize posterior evolution with increasing data. Implement from scratch, no PyMC.

### 5. Approximate Inference
- [ ] Why exact inference is intractable in general
- [ ] Variational inference: ELBO, mean-field approximation
- [ ] Expectation Maximization (EM algorithm)
- [ ] **Project:** Implement EM for Gaussian Mixture Models from scratch — fit GMMs to 2D synthetic data, visualize cluster evolution across iterations

### 6. Sampling Methods (MCMC)
- [ ] Monte Carlo estimation and importance sampling
- [ ] Markov chains: stationarity, mixing, detailed balance
- [ ] Metropolis-Hastings algorithm
- [ ] Gibbs sampling
- [ ] Hamiltonian Monte Carlo (HMC) — conceptual understanding
- [ ] **Project:** MCMC sampler from scratch — implement Metropolis-Hastings to sample from a 2D posterior. Visualize trace plots, autocorrelation, and convergence diagnostics.

### 7. Probabilistic ML Connections
- [ ] Gaussian Processes: intuition and kernel functions
- [ ] Variational Autoencoders: ELBO derivation, reparameterization trick
- [ ] Normalizing flows (conceptual)
- [ ] **Project:** Implement a VAE from scratch in PyTorch (no high-level libraries) — train on MNIST, visualize latent space, sample from prior

---

## Projects

| Project | Description | Key concepts |
|---|---|---|
| Probability toolkit | Monte Carlo vs. numerical integration for expectations | Estimation, integration |
| Distribution library | Implement 8+ distributions from scratch | PDFs, sampling, log-likelihood |
| KL divergence explorer | Analytical + numerical KL, visualize asymmetry | Information theory |
| Bayesian coin flip | Beta-Binomial conjugate inference | Bayes' theorem, conjugacy |
| EM for GMMs | Gaussian Mixture Model fitting from scratch | EM algorithm, latent variables |
| Metropolis-Hastings sampler | MCMC sampling with convergence diagnostics | Markov chains, mixing |
| VAE from scratch | Variational autoencoder on MNIST | ELBO, reparameterization trick |

---

## Resources

**Books**
- *Pattern Recognition and Machine Learning* — Bishop (the probabilistic ML bible)
- *Probabilistic Theory of Pattern Recognition* — Devroye et al.
- *Information Theory, Inference, and Learning Algorithms* — MacKay (free online)
- *Bayesian Data Analysis* — Gelman et al. (for deep Bayesian intuition)

**Courses**
- Coursera *Probabilistic Graphical Models* — Daphne Koller (Stanford)
- Cambridge *Information Theory, Pattern Recognition and Neural Networks* — MacKay lectures (YouTube)

**Papers**
- *Auto-Encoding Variational Bayes* — Kingma & Welling (2013) — foundational VAE paper
- *A Tutorial on Energy-Based Learning* — LeCun et al.

---

## Progress

- [ ] Probability foundations
- [ ] Distributions
- [ ] Information theory
- [ ] Bayesian inference
- [ ] Approximate inference
- [ ] Sampling methods (MCMC)
- [ ] Probabilistic ML connections
- [ ] Project: Probability toolkit
- [ ] Project: Distribution library
- [ ] Project: KL divergence explorer
- [ ] Project: Bayesian coin flip
- [ ] Project: EM for GMMs
- [ ] Project: Metropolis-Hastings sampler
- [ ] Project: VAE from scratch

---

## 8. Uncertainty Quantification

Directly relevant to clinical ML — overconfident predictions can cause harm.

- [ ] Aleatoric vs. epistemic uncertainty: data noise vs. model ignorance
- [ ] **MC Dropout:** enable dropout at inference, run N forward passes, compute predictive mean and variance
- [ ] **Deep Ensembles:** train N independent models with different random seeds, aggregate — empirically stronger than MC Dropout
- [ ] **Calibration:** expected calibration error (ECE), reliability diagrams — is confidence meaningful?
- [ ] Temperature scaling: post-hoc calibration without retraining
- [ ] **Conformal Prediction:** distribution-free, statistically guaranteed prediction sets
  - Inductive conformal prediction: calibration set → non-conformity scores → adaptive prediction sets
  - Coverage guarantee: P(Y ∈ Ĉ(X)) ≥ 1 − α, regardless of model or data distribution
  - Risk-controlling prediction sets (RCPS): extend to structured outputs like segmentation masks
- [ ] **Project:** Uncertainty benchmark — implement MC Dropout and deep ensembles on a classifier; compute ECE and reliability diagrams; apply conformal prediction; visualise where uncertainty correlates with error

**Key papers:**
- *Simple and Scalable Predictive Uncertainty Estimation using Deep Ensembles* — Lakshminarayanan et al., NeurIPS 2017
- *A Gentle Introduction to Conformal Prediction* — Angelopoulos & Bates (2022, tutorial)
- *Risk-Controlling Prediction Sets* — Bates et al., JACM 2023
- *On Calibration of Modern Neural Networks* — Guo et al., ICML 2017

---

## Progress

- [ ] Probability foundations
- [ ] Distributions
- [ ] Information theory
- [ ] Bayesian inference
- [ ] Approximate inference
- [ ] Sampling methods (MCMC)
- [ ] Probabilistic ML connections
- [ ] Uncertainty quantification
- [ ] Project: Probability toolkit
- [ ] Project: Distribution library
- [ ] Project: KL divergence explorer
- [ ] Project: Bayesian coin flip
- [ ] Project: EM for GMMs
- [ ] Project: Metropolis-Hastings sampler
- [ ] Project: VAE from scratch
- [ ] Project: Uncertainty benchmark (MC Dropout + ensembles + conformal prediction)
