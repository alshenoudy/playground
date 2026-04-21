# Go

Learning Go from first principles, progressing from language fundamentals to building production-grade systems: concurrent pipelines, HTTP/gRPC servers, and CLI tools. Go is chosen for its simplicity, excellent concurrency model, and suitability for systems and infrastructure work.

---

## Goal

By the end of this track you will be able to:
- Write idiomatic, production-quality Go code
- Build concurrent systems using goroutines and channels correctly
- Design and implement HTTP APIs and gRPC services
- Understand Go's memory model, scheduler, and runtime well enough to reason about performance
- Use Go for systems-level tooling that complements your Python ML work

---

## Prerequisites

- Strong Python background (you have this — expect to constantly compare mental models)
- Basic understanding of how HTTP works
- Familiarity with the command line

---

## Learning Path

### 1. Language Fundamentals
- [ ] Types, variables, zero values, short declarations
- [ ] Functions: multiple return values, named returns, variadic functions
- [ ] Arrays, slices, maps — internals and gotchas
- [ ] Structs and methods — Go's approach to OOP without classes
- [ ] Interfaces: implicit satisfaction, the empty interface, type assertions
- [ ] Pointers: when to use them, stack vs. heap allocation intuition
- [ ] Error handling: the `error` interface, wrapping with `fmt.Errorf`, `errors.As`/`errors.Is`
- [ ] Packages and modules: `go.mod`, visibility rules, organizing code
- [ ] **Project:** Build a CLI tool — a command-line file statistics tool that counts lines, words, and bytes across multiple files (like `wc` but written in Go with flags)

### 2. Concurrency
- [ ] Goroutines: lightweight threads, scheduling model (M:N scheduler)
- [ ] Channels: buffered vs. unbuffered, directional channels, closing
- [ ] `select` statement: multiplexing channels, timeouts, cancellation
- [ ] `sync` package: `Mutex`, `RWMutex`, `WaitGroup`, `Once`
- [ ] Common concurrency patterns: fan-out/fan-in, worker pools, pipelines
- [ ] Data races: `go race` detector, how to reason about shared state
- [ ] Context package: cancellation, deadlines, passing values across goroutines
- [ ] **Project:** Concurrent file processor — process a directory of files in parallel with a bounded worker pool, aggregate results, support cancellation via context

### 3. HTTP Servers and APIs
- [ ] `net/http` standard library — handlers, `ServeMux`, middleware
- [ ] Request/response lifecycle, reading bodies, setting headers
- [ ] JSON encoding/decoding with `encoding/json`
- [ ] Middleware patterns: logging, auth, request IDs
- [ ] Testing HTTP handlers with `httptest`
- [ ] **Project:** Build a REST API server — a simple key-value store HTTP API with GET, PUT, DELETE endpoints. Support concurrent access with proper locking. Include handler tests.

### 4. Go Internals and Performance
- [ ] Go memory model: happens-before, why it matters for concurrency
- [ ] Garbage collector: how it works, tuning with `GOGC`
- [ ] Escape analysis: when variables go to the heap
- [ ] Profiling with `pprof`: CPU, memory, goroutine profiles
- [ ] Benchmarking with `testing.B`
- [ ] **Project:** Profile and optimize a Go program — take a deliberately slow implementation of a word frequency counter, profile it, identify bottlenecks, and optimize using what you learn

### 5. gRPC and Protocol Buffers
- [ ] Protocol Buffers: defining `.proto` files, code generation
- [ ] gRPC service types: unary, server streaming, client streaming, bidirectional
- [ ] Interceptors (middleware for gRPC)
- [ ] Error handling in gRPC: status codes, error details
- [ ] **Project:** gRPC inference service — define a proto for a simple ML model inference service (send a feature vector, get back a prediction). Implement server in Go, client in both Go and Python.

### 6. Real-World Patterns
- [ ] Dependency injection without frameworks
- [ ] Configuration management: env vars, config files, `viper`
- [ ] Structured logging with `slog` (Go 1.21+)
- [ ] Graceful shutdown: trapping signals, draining connections
- [ ] Writing testable Go: interfaces, table-driven tests, mocks
- [ ] **Project:** Production-ready service template — refactor your REST API server to include structured logging, graceful shutdown, config management, and a full test suite

---

## Projects

| Project | Description | Key concepts |
|---|---|---|
| `wc` clone | CLI file statistics tool with flags | Fundamentals, CLI, `os`, `bufio` |
| Concurrent file processor | Parallel directory processing with worker pool | Goroutines, channels, context |
| Key-value store API | REST API with concurrent access | `net/http`, JSON, sync |
| Performance profiler exercise | Profile + optimize a slow Go program | `pprof`, benchmarks, escape analysis |
| gRPC inference service | Proto-defined ML inference endpoint | gRPC, protobuf, cross-language client |
| Production-ready service | Full-featured, testable, observable HTTP service | Production patterns, testing |

---

## Resources

**Books**
- *The Go Programming Language* — Donovan & Kernighan (the definitive reference)
- *Concurrency in Go* — Katherine Cox-Buday (deep dive into Go concurrency)
- *100 Go Mistakes and How to Avoid Them* — Teiva Harsanyi (read after basics)

**Official**
- go.dev/tour — official interactive tour, good for day one
- go.dev/doc/effective_go — idiomatic Go patterns, read early and revisit often
- go.dev/blog — high-quality posts on internals, concurrency, performance

**Videos**
- Rob Pike's *Concurrency is not Parallelism* (talk) — mental model for goroutines
- GopherCon talks on YouTube — practical, real-world Go patterns

---

## Progress

- [ ] Language fundamentals
- [ ] Concurrency
- [ ] HTTP servers and APIs
- [ ] Go internals and performance
- [ ] gRPC and Protocol Buffers
- [ ] Real-world patterns
- [ ] Project: `wc` clone CLI
- [ ] Project: Concurrent file processor
- [ ] Project: Key-value store API
- [ ] Project: Performance profiler exercise
- [ ] Project: gRPC inference service
- [ ] Project: Production-ready service template
