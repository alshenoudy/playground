# Python

Not how to write Python — you know that. This is about understanding how Python actually works: the runtime, the memory model, the performance characteristics, and the language features that most people use without understanding.

The goal is to be able to read CPython source, reason about memory and performance, and write code that other engineers respect.

---

## Goal

- Understand Python's execution model well enough to reason about performance and behaviour without guessing
- Use advanced language features correctly — not because you saw them in a Stack Overflow answer
- Write clean, idiomatic Python that's easy to test and maintain
- Know when Python is the wrong tool and why

---

## Prerequisites

- Python proficiency (you have this)
- Basic C knowledge helps for the CPython sections but isn't required

---

## Learning Path

### 1. The Python Data Model
- [ ] `__dunder__` methods: the protocol behind `len()`, `in`, `[]`, iteration, comparison
- [ ] `__repr__` vs `__str__`: when each is called, why both matter
- [ ] `__slots__`: what it does to memory layout and attribute access speed
- [ ] `__call__`: making objects callable; where this pattern appears in ML (e.g. PyTorch `nn.Module`)
- [ ] Descriptor protocol: how `@property`, `@staticmethod`, `@classmethod` actually work
- [ ] `__getattr__` vs `__getattribute__`: the difference and when each fires
- [ ] **Implementation:** Build a `Vector` class that supports `+`, `*`, `abs()`, iteration, and `repr` — using only dunder methods, no helper functions

### 2. Functions and Closures
- [ ] First-class functions: functions as arguments, return values, stored in data structures
- [ ] Closures: what gets captured, when it's a reference vs a value, the late-binding gotcha
- [ ] Decorators: how they work mechanically; decorators with arguments; `functools.wraps`
- [ ] `functools`: `partial`, `lru_cache`, `cache`, `reduce` — know each by use case
- [ ] Generators: `yield`, `yield from`, generator expressions vs list comprehensions — memory implications
- [ ] `itertools`: `chain`, `islice`, `groupby`, `product` — composing iterators
- [ ] **Implementation:** Write a decorator that retries a function on exception with exponential backoff — with and without arguments version

### 3. The Object Model and Metaprogramming
- [ ] Classes are objects: `type()` is a class, classes have metaclasses
- [ ] `type()` as a class factory: creating classes dynamically
- [ ] `__init_subclass__`: hook into subclassing without a metaclass
- [ ] `__new__` vs `__init__`: object creation vs initialisation
- [ ] Abstract base classes: `abc.ABC`, `@abstractmethod`, why they matter for designing interfaces
- [ ] `dataclasses`: what they generate, `__post_init__`, `field()` — when to use over plain classes
- [ ] **Implementation:** Build a simple model registry using `__init_subclass__` — any class that subclasses `BaseModel` automatically registers itself by name

### 4. Memory and the Runtime
- [ ] Reference counting: how Python tracks object lifetimes
- [ ] The cyclic garbage collector: why reference counting alone isn't enough
- [ ] Memory layout: small integer cache, string interning, `id()` and object identity
- [ ] `weakref`: breaking reference cycles; where this matters in caching
- [ ] `sys.getsizeof`: measuring object memory; why a Python `int` is 28 bytes
- [ ] The GIL: what it protects, what it prevents, why `multiprocessing` exists, when `threading` is still useful (I/O-bound work)
- [ ] **Implementation:** Measure the memory footprint of 1M integers stored as a Python list vs a NumPy array vs a generator. Document findings.

### 5. Concurrency and Async
- [ ] `threading`: use cases (I/O-bound), limitations (GIL), `Lock`, `Event`, `Queue`
- [ ] `multiprocessing`: use cases (CPU-bound), `Pool`, `shared_memory`, serialisation cost
- [ ] `concurrent.futures`: `ThreadPoolExecutor`, `ProcessPoolExecutor` — the practical API
- [ ] `asyncio`: event loop, coroutines, `await`, `async for`, `async with` — when it beats threading
- [ ] Common mistake: using `asyncio` for CPU-bound work — why it doesn't help
- [ ] **Implementation:** Download 100 URLs three ways — sequential, `ThreadPoolExecutor`, `asyncio`. Compare wall time. Then try CPU-bound work (hashing) the same way and explain the difference.

### 6. Performance and Profiling
- [ ] `timeit`: microbenchmarking correctly — why you can't just time with `time.time()`
- [ ] `cProfile` and `pstats`: finding where time actually goes
- [ ] `line_profiler`: line-by-line profiling for hot functions
- [ ] `memory_profiler`: tracking memory usage over time
- [ ] Common Python performance pitfalls: attribute lookup in loops, list vs generator in tight loops, string concatenation, global vs local variable access
- [ ] When to reach for NumPy, Cython, or just rewrite in Go
- [ ] **Project:** Profile a slow data preprocessing script — find the top 3 bottlenecks with `cProfile`, fix them, measure the improvement. Document before/after.

### 7. Packaging and Project Structure
- [ ] `pyproject.toml`: the modern standard — `[build-system]`, `[project]`, `[tool]` sections
- [ ] `src/` layout vs flat layout — why `src/` prevents a class of import bugs
- [ ] Virtual environments: `venv`, why you need one per project, `pip-tools` for pinning
- [ ] Editable installs: `pip install -e .` and when you need it
- [ ] Type hints: `mypy` for static analysis, `typing` module essentials (`Optional`, `Union`, `TypeVar`, `Protocol`)
- [ ] `Protocol` vs `ABC`: structural vs nominal subtyping — prefer `Protocol` for duck typing
- [ ] **Implementation:** Take an existing script and turn it into a proper package — `src/` layout, `pyproject.toml`, type-annotated public API, `mypy` passing clean

---

## Projects

| Project | Key concepts |
|---|---|
| `Vector` class | Data model, dunder methods |
| Retry decorator | Closures, decorators with arguments, `functools.wraps` |
| Model registry via `__init_subclass__` | Metaprogramming, class hierarchy |
| Memory footprint comparison | Runtime, `sys.getsizeof`, NumPy internals |
| Concurrency benchmark (I/O vs CPU) | Threading, multiprocessing, asyncio |
| Profiling and optimisation exercise | `cProfile`, `line_profiler`, performance fixes |
| Script → proper package | `pyproject.toml`, `src/` layout, `mypy` |

---

## Resources

**Books**
- *Fluent Python* — Luciano Ramalho (the definitive advanced Python book — read cover to cover)
- *High Performance Python* — Gorelick & Ozsvald (profiling, optimization, concurrency)
- *Python Cookbook* — Beazley & Jones (patterns and idioms)

**Reference**
- CPython source on GitHub — reading the source for `list`, `dict`, `int` is more instructive than any blog post
- Python docs: Data Model chapter — the authoritative reference for dunder methods

---

## Progress

- [ ] The Python data model
- [ ] Functions and closures
- [ ] The object model and metaprogramming
- [ ] Memory and the runtime
- [ ] Concurrency and async
- [ ] Performance and profiling
- [ ] Packaging and project structure
- [ ] Project: `Vector` class
- [ ] Project: Retry decorator
- [ ] Project: Model registry
- [ ] Project: Memory footprint comparison
- [ ] Project: Concurrency benchmark
- [ ] Project: Profiling exercise
- [ ] Project: Script → package
