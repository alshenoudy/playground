# Design Patterns

Design patterns are reusable solutions to recurring software design problems. This track covers the most important patterns — not as abstract theory but through implementation in both Python and Go, with focus on where they appear in real ML and systems code.

---

## Goal

By the end of this track you will be able to:
- Recognize and apply the right pattern for a given design problem
- Implement patterns idiomatically in both Python and Go (they differ significantly)
- Understand where patterns appear in popular frameworks (PyTorch, FastAPI, Kubernetes operators)
- Design software that is extensible, testable, and easy to reason about

---

## Prerequisites

- Python proficiency (you have this)
- Go fundamentals (complete the Go track first — patterns in Go use interfaces heavily)

---

## Learning Path

### 1. Creational Patterns
These patterns control how objects/structs are created.

- [ ] **Factory Method** — define an interface for creating objects; let subclasses decide which class to instantiate
  - Python: abstract base class + concrete factories
  - Go: function returning an interface
  - *Appears in:* PyTorch optimizer factory, ML model registries
- [ ] **Builder** — construct complex objects step by step
  - Python: method chaining with a builder class
  - Go: functional options pattern (idiomatic Go alternative)
  - *Appears in:* building training configs, request builders in HTTP clients
- [ ] **Singleton** — ensure a single instance (and when NOT to use it)
  - Python: module-level instance or `__new__`
  - Go: `sync.Once`
  - *Appears in:* database connections, global config, loggers
- [ ] **Project:** Model registry — implement a registry that maps string names to model classes, supports `register` and `build` operations, and is used to instantiate models from a config file. Implement in Python and Go.

### 2. Structural Patterns
These patterns deal with how objects/structs are composed.

- [ ] **Adapter** — convert one interface into another
  - *Appears in:* wrapping third-party model APIs to a common interface
- [ ] **Decorator** — add behavior to an object without modifying it
  - Python: `@functools.wraps`, class-based decorators
  - Go: wrapping a struct that implements an interface
  - *Appears in:* middleware in HTTP servers, PyTorch hooks, caching layers
- [ ] **Proxy** — control access to an object (lazy init, caching, logging)
  - *Appears in:* lazy model loading, feature store caching
- [ ] **Composite** — treat individual objects and groups uniformly (tree structures)
  - *Appears in:* PyTorch `nn.Sequential`, file system abstractions
- [ ] **Project:** Middleware pipeline — implement a chain of HTTP middleware (logging, auth, rate limiting) using the Decorator pattern in Go. Replicate the same concept in Python using function decorators.

### 3. Behavioral Patterns
These patterns define how objects communicate and distribute responsibility.

- [ ] **Strategy** — define a family of algorithms, make them interchangeable
  - *Appears in:* ML optimizers, loss functions, samplers
- [ ] **Observer** — notify dependents when state changes (event system)
  - Python: callbacks, event emitters
  - Go: channels as a natural observer mechanism
  - *Appears in:* PyTorch training callbacks, Prefect event hooks
- [ ] **Command** — encapsulate a request as an object (supports undo, queuing)
  - *Appears in:* task queues, undo/redo systems, CLI commands
- [ ] **Template Method** — define the skeleton of an algorithm; subclasses fill in steps
  - *Appears in:* PyTorch `LightningModule`, sklearn estimator base classes
- [ ] **Iterator** — sequential access to elements without exposing internals
  - Python: `__iter__` / `__next__`, generators
  - Go: range loops, custom iterators with channels
  - *Appears in:* PyTorch DataLoader, database cursors
- [ ] **Project:** Plugin-based optimizer — implement a training loop where the optimizer, loss function, and learning rate schedule are all swappable strategies loaded from config. Implement in Python.

### 4. Patterns in ML Systems
Apply patterns in the context of real ML engineering.

- [ ] **Repository pattern** — abstract data access behind an interface (decouple business logic from storage)
- [ ] **Pipeline pattern** — chain transformations where each step is independent and composable
- [ ] **Circuit breaker** — prevent cascading failures in service calls
- [ ] **Sidecar pattern** — offload cross-cutting concerns (logging, metrics) to a separate process
- [ ] **Project:** Refactor a data pipeline — take a monolithic preprocessing script and refactor it using the Pipeline and Repository patterns. Every transformation is a composable step; data access goes through a repository interface.

---

## Projects

| Project | Description | Key concepts |
|---|---|---|
| Model registry | String → model class mapping with config-driven instantiation | Factory, Registry |
| Middleware pipeline | Chainable HTTP middleware in Go + Python | Decorator, Chain of Responsibility |
| Plugin-based optimizer | Strategy pattern for ML training components | Strategy, Dependency Injection |
| Refactored data pipeline | Pipeline + Repository pattern applied to preprocessing | Pipeline, Repository |

---

## Resources

**Books**
- *Design Patterns* — Gang of Four (the original reference, language-agnostic)
- *Head First Design Patterns* — Freeman & Robson (approachable introduction)
- *A Philosophy of Software Design* — John Ousterhout (goes beyond patterns to design principles)

**Go-specific**
- *100 Go Mistakes* — Harsanyi (idiomatic patterns and anti-patterns)
- go.dev/blog — search for interface and composition posts

---

## Progress

- [ ] Creational patterns
- [ ] Structural patterns
- [ ] Behavioral patterns
- [ ] Patterns in ML systems
- [ ] Project: Model registry
- [ ] Project: Middleware pipeline
- [ ] Project: Plugin-based optimizer
- [ ] Project: Refactored data pipeline
