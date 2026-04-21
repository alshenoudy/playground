# Distributed Systems

Distributed systems are at the foundation of every large-scale infrastructure — including ML platforms. This track covers the core theory and builds up to real implementations: consensus algorithms, replication, message queues, and the tradeoffs that make distributed systems genuinely hard.

---

## Goal

By the end of this track you will be able to:
- Reason clearly about consistency, availability, and partition tolerance
- Understand how consensus algorithms like Raft work and implement a simplified version
- Design systems that handle partial failures gracefully
- Build message-queue-based architectures for decoupled, scalable systems
- Read systems papers (Dynamo, Spanner, Kafka) and understand the design decisions

---

## Prerequisites

- Go fundamentals (this track is implemented in Go)
- Networking basics: TCP, HTTP, what a socket is
- Basic concurrency (covered in the Go track)

---

## Learning Path

### 1. Foundations and Failure Models
- [ ] Why distributed systems are hard: partial failures, network unreliability, no global clock
- [ ] Failure models: crash-stop, crash-recovery, Byzantine
- [ ] The two generals problem and why it's unsolvable
- [ ] CAP theorem: consistency, availability, partition tolerance — understanding the actual tradeoff
- [ ] PACELC: a more nuanced model of distributed tradeoffs
- [ ] **Implementation:** Build a network simulator in Go — simulate message loss, delay, and reordering. Use it as the foundation for testing all subsequent distributed systems implementations.

### 2. Time and Ordering
- [ ] Physical clocks: why wall clocks can't be trusted
- [ ] Logical clocks: Lamport timestamps
- [ ] Vector clocks: tracking causality across processes
- [ ] **Implementation:** Implement Lamport timestamps and vector clocks — run a simulated multi-process system, log events, verify causal ordering

### 3. Replication
- [ ] Why replication: fault tolerance, read scaling
- [ ] Single-leader, multi-leader, leaderless replication
- [ ] Replication lag and read-your-writes consistency
- [ ] Conflict resolution: last-write-wins, version vectors, CRDTs
- [ ] **Project:** Build a replicated key-value store — single-leader replication with two replicas. Leader accepts writes and replicates to followers. Implement read-from-follower with configurable consistency levels (eventual vs. strong).

### 4. Consensus
- [ ] The consensus problem: why it's hard (FLP impossibility)
- [ ] Paxos: single-decree Paxos, why it's hard to implement correctly
- [ ] Raft: leader election, log replication, safety properties — the understandable consensus algorithm
- [ ] **Project:** Implement simplified Raft in Go — leader election and log replication (no log compaction required). Run a 3-node cluster, simulate leader failure, verify a new leader is elected and the log remains consistent.

### 5. Message Queues and Event-Driven Architecture
- [ ] Why message queues: decoupling producers and consumers, buffering, fan-out
- [ ] Delivery semantics: at-most-once, at-least-once, exactly-once
- [ ] Kafka architecture: topics, partitions, consumer groups, offsets, retention
- [ ] Event sourcing and CQRS as architectural patterns
- [ ] **Project:** Build a minimal Kafka-like message queue in Go — a broker that supports topics with multiple partitions, persistent append-only logs, consumer group offsets, and at-least-once delivery semantics

### 6. Distributed Transactions
- [ ] ACID vs. BASE: transactional guarantees in distributed context
- [ ] Two-phase commit (2PC): how it works and why it's fragile
- [ ] Saga pattern: compensating transactions for long-running workflows
- [ ] **Implementation:** Implement 2PC across two services in Go — a coordinator and two participant services. Demonstrate commit and abort paths. Demonstrate the blocking failure mode.

---

## Projects

| Project | Description | Key concepts |
|---|---|---|
| Network simulator | Go-based message layer with loss/delay/reorder | Failure models, testing infrastructure |
| Logical + vector clocks | Causal ordering across simulated processes | Time, causality |
| Replicated key-value store | Single-leader KV store with configurable consistency | Replication, consistency levels |
| Simplified Raft | Leader election + log replication in Go | Consensus, fault tolerance |
| Minimal message queue | Kafka-like broker with partitions and consumer groups | Messaging, event-driven arch |
| 2PC implementation | Two-phase commit across two services | Distributed transactions |

---

## Resources

**Books**
- *Designing Data-Intensive Applications* — Martin Kleppmann (read this cover to cover — essential)
- *Distributed Systems* — Tanenbaum & Van Steen (theoretical foundations)

**Papers**
- *The Raft Consensus Algorithm* — Ongaro & Ousterhout (2014) — read alongside your implementation
- *Dynamo: Amazon's Highly Available Key-value Store* — DeCandia et al. (2007)
- *Kafka: a Distributed Messaging System for Log Processing* — Kreps et al. (2011)
- *Spanner: Google's Globally Distributed Database* — Corbett et al. (2012)
- *In Search of an Understandable Consensus Algorithm* — Ongaro (Raft PhD dissertation)

**Courses**
- MIT 6.824 Distributed Systems (labs are in Go — highly recommended to follow along)

---

## Progress

- [ ] Foundations and failure models
- [ ] Time and ordering
- [ ] Replication
- [ ] Consensus
- [ ] Message queues and event-driven architecture
- [ ] Distributed transactions
- [ ] Project: Network simulator
- [ ] Project: Logical + vector clocks
- [ ] Project: Replicated key-value store
- [ ] Project: Simplified Raft
- [ ] Project: Minimal message queue
- [ ] Project: 2PC implementation
