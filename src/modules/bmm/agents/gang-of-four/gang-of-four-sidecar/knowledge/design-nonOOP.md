### Common non-OOP patterns


| Category                  | Pattern Name                                   | Primary Paradigm / Origin                | Short Description / Typical Use                                                                                  | Typical Context of Usage                                                                                         |
|---------------------------|------------------------------------------------|------------------------------------------|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| Functional Programming    | **MapReduce**                                  | Functional / Distributed (Google)        | Decompose massive data processing into independent map & reduce phases                                         | Big data analytics pipelines, log aggregation, distributed batch jobs on Hadoop/Spark clusters                  |
| Functional Programming    | **Monad** (Maybe, Either, IO, State, Reader…)  | Haskell / Category Theory                | Encapsulate computations with context (error handling, logging, async, dependency injection)                   | Functional codebases handling nullable values, chained async operations, or composable error propagation         |
| Functional Programming    | **Functor / Applicative**                      | Functional                               | Generalised mapping and chaining over containers                                                                | Transforming collections, optional values, or async results without unwrapping them manually                     |
| Functional Programming    | **Fold / Reduce / Catamorphism**               | Functional                               | Collapse a data structure into a single value                                                                   | Summing lists, building accumulators, traversing tree structures to produce aggregated results                   |
| Functional Programming    | **Partial Application & Currying**             | Lambda calculus                          | Transform multi-arg functions into chains of single-arg functions                                               | Creating reusable function factories, configuring callbacks, building DSLs with pre-filled parameters            |
| Functional Programming    | **Higher-Order Functions**                     | Functional                               | Functions that take/return other functions (map, filter, compose, etc.)                                        | Data transformation pipelines, event handlers, middleware chains, declarative collection processing             |
| Concurrency               | **Actor Model**                                | Erlang, Akka, CAF                        | Isolated entities with private state communicating only via messages                                           | Telecom systems, real-time chat servers, game backends, IoT device coordination                                  |
| Concurrency               | **CSP** (Communicating Sequential Processes)  | Go channels, Occam, Hoare                | Synchronous message passing over typed channels                                                                 | Go microservices, concurrent task coordination, producer-consumer workflows with explicit synchronization        |
| Concurrency               | **Software Transactional Memory (STM)**        | Haskell, Clojure                         | Lock-free composable atomic operations with automatic retry on conflict                                        | Concurrent data structures, banking/financial transactions, multi-threaded state updates without explicit locks  |
| Concurrency               | **Reactor Pattern**                            | C/libevent, Java NIO, Node.js            | Single-threaded event demultiplexing and dispatching                                                            | High-throughput web servers, real-time applications, I/O-bound services handling thousands of connections        |
| Concurrency               | **Proactor Pattern**                           | Windows IOCP, Boost.Asio                 | Asynchronous I/O with completion callbacks                                                                      | Windows-based high-performance servers, async file I/O, network services requiring true async completion         |
| Architecture / DDD        | **CQRS** (Command Query Responsibility Segregation) | Domain-Driven Design                | Separate read and write models for scalability and clarity                                                      | E-commerce platforms, reporting dashboards, systems with vastly different read/write performance requirements    |
| Architecture / DDD        | **Event Sourcing**                             | DDD / Banking                            | Persist state as an immutable sequence of events instead of current state                                       | Financial ledgers, audit-heavy systems, collaborative editing, any domain requiring complete history replay      |
| Architecture              | **Hexagonal** (Ports & Adapters)               | Alistair Cockburn                        | Isolate core business logic from external concerns (UI, DB, frameworks)                                        | Enterprise applications needing testability, systems that swap databases or UIs, long-lived maintainable codebases |
| Architecture              | **Onion Architecture**                         | Jeffrey Palermo                          | Layered dependency-inverted structure around the domain core                                                    | .NET enterprise apps, domain-rich applications where business rules must remain framework-agnostic               |
| Architecture              | **Clean Architecture**                         | Robert C. Martin                         | Explicit boundaries and dependency rule (nothing outside depends on inside)                                     | Large-scale applications, teams enforcing strict separation of concerns, projects prioritizing long-term maintainability |
| Architecture              | **Pipeline** (Pipes and Filters)               | UNIX, Enterprise Integration Patterns    | Chain of processing steps; great for ETL, compilers, image processing                                           | Data ingestion workflows, CI/CD pipelines, media transcoding, compiler front-ends, log processing chains         |
| Distributed Systems       | **CRDTs** (Conflict-free Replicated Data Types)| Distributed databases (Riak, Redis)      | Data types that converge without coordination in eventually consistent systems                                  | Collaborative editors, offline-first mobile apps, distributed caches, multi-region database replication          |
| Distributed Systems       | **Merkle Tree**                                | Git, Cassandra, Blockchain               | Cryptographic tree for efficient and secure verification of large data sets                                     | Version control systems, blockchain transaction verification, distributed storage integrity checks               |
| Resilience                | **Circuit Breaker**                            | Michael Nygard "Release It!"             | Fail fast and prevent cascading failures                                                                         | Microservice-to-microservice calls, third-party API integrations, any remote dependency prone to outages         |
| Resilience                | **Bulkhead**                                   | Nygard / Ship stability metaphor         | Isolate resources (threads, connections) to contain failures                                                    | Multi-tenant SaaS platforms, services with mixed criticality workloads, preventing noisy-neighbor problems       |
| Resilience                | **Retry / Timeout / Backoff**                  | Cloud-native libraries                   | Transient fault handling patterns                                                                                | Cloud API calls, database connections, message queue consumers, any network operation subject to transient errors |
| Cloud / Service Mesh      | **Sidecar**                                    | Istio, Linkerd, Envoy                    | Companion container/process for cross-cutting concerns (logging, TLS, tracing)                                  | Kubernetes deployments, service mesh architectures, adding observability without modifying application code       |
| Cloud / Migration         | **Strangler Fig**                              | Martin Fowler                            | Gradually replace a legacy system by intercepting calls and routing to new implementation                     | Monolith-to-microservices migrations, legacy modernization projects, incremental rewrites of aging systems       |
| Web / API                 | **REST Architectural Constraints**            | Roy Fielding                             | Stateless, cacheable, uniform interface, resource-based APIs                                                     | Public APIs, mobile app backends, any HTTP-based service requiring broad client compatibility                    |
| Web / API                 | **HATEOAS**                                    | Part of REST                             | Hypermedia-driven APIs where clients discover actions dynamically                                               | Self-documenting APIs, workflow-driven interfaces, APIs where available actions depend on resource state         |
| Reactive / Streaming      | **Reactive Streams / Back-pressure**           | RxJava, Project Reactor, Akka Streams    | Non-blocking, asynchronous stream processing with flow control                                                  | Real-time data feeds, IoT sensor ingestion, streaming analytics, systems where producers can overwhelm consumers |
| Testing                   | **Property-Based Testing**                     | QuickCheck (Haskell), Hypothesis (Python)| Automatically generate thousands of test cases to verify invariants                                             | Validating parsers, serialization round-trips, algorithm correctness, finding edge cases in complex logic        |
| Testing / Contracts       | **Consumer-Driven Contracts**                  | Pact, Spring Cloud Contract              | Consumers define expected API behaviour; providers verify against it                                            | Microservice ecosystems, API versioning, ensuring backward compatibility across independently deployed services  |

### Most commonly used today (2025)

**CQRS + Event Sourcing**  
This combination dominates in domains requiring auditability and complex read/write scaling. CQRS separates command (write) and query (read) responsibilities into distinct models, allowing each to be optimized independently. Event Sourcing complements this by storing every state change as an immutable event, enabling full history replay, temporal queries, and straightforward debugging. Common in fintech, e-commerce order systems, and collaborative platforms.

**Hexagonal / Clean Architecture**  
These architectural styles have become the gold standard for maintainable enterprise applications. By placing business logic at the center and pushing infrastructure concerns (databases, APIs, UIs) to the edges via ports and adapters, teams achieve high testability and the freedom to swap technologies without rewriting core logic. Widely adopted in Java/Spring and .NET ecosystems.

**Actor Model & CSP (Go, Akka, Orleans)**  
Concurrency patterns that avoid shared mutable state. The Actor Model (Erlang, Akka, Microsoft Orleans) uses isolated actors communicating via async messages—ideal for distributed systems, IoT, and real-time gaming. CSP (Go channels) provides synchronous, typed channel communication for structured concurrency. Both patterns simplify reasoning about concurrent code and reduce race conditions.

**Reactor / Proactor (Node.js, Tokio, Netty)**  
These I/O patterns power the highest-throughput servers. Reactor uses a single-threaded event loop to multiplex thousands of connections (Node.js, Nginx, Redis). Proactor handles true async I/O with completion callbacks (Windows IOCP, Rust's Tokio). Essential for real-time applications, API gateways, and any service handling massive concurrent connections.

**Circuit Breaker + Bulkhead + Retry stacks**  
The resilience trifecta for distributed systems. Circuit Breaker prevents cascading failures by failing fast when a dependency is unhealthy. Bulkhead isolates resources (thread pools, connection pools) so one failing component doesn't starve others. Retry with exponential backoff handles transient faults gracefully. Libraries like Resilience4j, Polly, and Hystrix make these patterns accessible.

**CRDTs (SoundCloud, Redis, LWW-Register, etc.)**  
Conflict-free Replicated Data Types enable eventually consistent systems without coordination overhead. They mathematically guarantee convergence regardless of update order—critical for offline-first mobile apps, collaborative editors (Figma, Notion), and multi-region databases. Redis CRDTs and Automerge are popular implementations.

**Sidecar & Service Mesh patterns**  
The sidecar pattern deploys a companion container alongside each service to handle cross-cutting concerns: mTLS, observability, rate limiting, and traffic management. Service meshes (Istio, Linkerd, Cilium) orchestrate these sidecars across a cluster. This approach decouples infrastructure concerns from application code, enabling polyglot microservices with consistent security and monitoring.

**Strangler Fig for legacy modernization**  
Named after the vine that gradually envelops a host tree, this pattern enables incremental migration from legacy systems. New functionality is built in a modern stack while an interception layer (API gateway, reverse proxy) routes traffic between old and new implementations. Over time, the legacy system is "strangled" until it can be decommissioned. The safest approach for large-scale rewrites.

**Property-Based Testing**  
Instead of writing individual test cases, developers define properties that must hold for all inputs, and the framework generates thousands of random test cases. Tools like Hypothesis (Python), QuickCheck (Haskell), and fast-check (JS) excel at finding edge cases humans miss. Particularly valuable for parsers, serializers, algorithms, and any code with complex input spaces.

**Consumer-Driven Contracts**  
In microservice ecosystems, consumers define the API behavior they expect, and providers verify they meet those contracts. Tools like Pact and Spring Cloud Contract automate this verification in CI/CD pipelines. This inverts the traditional provider-first approach, ensuring backward compatibility and enabling independent deployments without integration test environments.

**REST Architectural Constraints**  
Roy Fielding's original REST constraints (statelessness, cacheability, uniform interface, layered system) remain the foundation of most web APIs. When properly applied, REST enables scalable, evolvable APIs with excellent tooling support. The emphasis on resources, standard HTTP methods, and hypermedia makes APIs intuitive and self-descriptive.

**HATEOAS**  
Hypermedia as the Engine of Application State is REST's most powerful (and underused) constraint. APIs return links describing available actions, allowing clients to navigate workflows dynamically without hardcoded URLs. This enables API evolution without breaking clients and creates truly self-documenting interfaces. Gaining traction in enterprise APIs and workflow-heavy domains.

**Reactive Streams / Back-pressure**  
The standard for non-blocking stream processing with flow control. When producers generate data faster than consumers can process, back-pressure signals slow down the source rather than causing buffer overflows or dropped messages. Implementations include RxJava, Project Reactor, Akka Streams, and Kotlin Flow. Essential for real-time analytics, IoT ingestion, and any streaming pipeline.

---

### Most Useful Combinations and Pairings

**CQRS + Event Sourcing** — Auditable Scalable Systems  
CQRS separates read and write models for independent optimization; Event Sourcing persists all state changes as immutable events enabling full history replay. *Context*: Financial ledgers, e-commerce order systems, collaborative platforms, any domain requiring audit trails and temporal queries.

**Hexagonal + CQRS + Event Sourcing** — Enterprise Domain Architecture  
Hexagonal isolates business logic from infrastructure; CQRS optimizes read/write paths; Event Sourcing provides complete audit history. *Context*: Banking systems, insurance platforms, healthcare records—enterprise applications requiring testability, scalability, and regulatory compliance.

**Clean + Onion + Hexagonal Architecture** — Layered Domain Isolation  
All three share the core principle of dependency inversion with business logic at the center. Clean adds explicit boundaries; Onion emphasizes concentric layers; Hexagonal provides ports/adapters abstraction. *Context*: Long-lived enterprise applications, teams enforcing strict separation of concerns, systems that must survive technology changes.

**Circuit Breaker + Bulkhead + Retry/Timeout** — Resilience Stack  
Circuit Breaker prevents cascading failures by failing fast; Bulkhead isolates resources to contain failures; Retry with exponential backoff handles transient faults. *Context*: Microservice architectures, cloud-native applications, any distributed system with remote dependencies (Resilience4j, Polly, Hystrix).

**Sidecar + Circuit Breaker + Bulkhead** — Service Mesh Resilience  
Sidecar proxies handle cross-cutting concerns; Circuit Breaker and Bulkhead patterns are implemented in the mesh layer (Envoy/Istio) rather than application code. *Context*: Kubernetes deployments, polyglot microservices, zero-trust architectures requiring consistent resilience without code changes.

**Actor Model + Reactive Streams + Back-pressure** — Scalable Stream Processing  
Actors provide isolated concurrent processing units; Reactive Streams define the protocol for async data flow; Back-pressure prevents system overload. *Context*: Real-time analytics (Akka Streams), IoT sensor ingestion, high-throughput event processing, streaming ETL pipelines.

**Actor Model + CQRS + Event Sourcing** — Distributed Domain Systems  
Actors encapsulate aggregate state and process commands; CQRS separates command/query responsibilities; Event Sourcing persists actor state as event streams. *Context*: Distributed gaming backends, real-time trading systems, collaborative applications (Akka, Microsoft Orleans, Lagom).

**CSP + Pipeline** — Structured Concurrent Processing  
CSP (Go channels) provides typed synchronous communication between goroutines; Pipeline pattern chains processing stages. *Context*: Go microservices, concurrent ETL workflows, fan-out/fan-in processing, producer-consumer systems with explicit synchronization.

**Reactor + Pipeline** — High-Throughput I/O Processing  
Reactor pattern handles thousands of connections via single-threaded event demultiplexing; Pipeline chains processing stages for each request. *Context*: Node.js applications, Nginx, Redis, API gateways, real-time web servers handling massive concurrent connections.

**MapReduce + Pipeline + Fold** — Distributed Data Processing  
MapReduce decomposes processing into parallel map and reduce phases; Pipeline chains transformations; Fold aggregates results. *Context*: Big data analytics (Hadoop, Spark), log aggregation, batch processing jobs, distributed ETL workflows.

**Monad + Functor + Higher-Order Functions** — Functional Composition  
Functors enable mapping over containers; Monads chain computations with context (error handling, async, state); Higher-Order Functions compose transformations. *Context*: Functional codebases (Haskell, Scala, F#), error propagation chains, async operation composition, DSL construction.

**Partial Application + Currying + Higher-Order Functions** — Function Factory Patterns  
Currying transforms multi-arg functions into chains; Partial Application pre-fills arguments; Higher-Order Functions compose the results. *Context*: Configuration injection, callback factories, middleware construction, building DSLs with pre-configured behavior.

**CRDTs + Event Sourcing** — Eventually Consistent Distributed State  
CRDTs guarantee convergence without coordination; Event Sourcing provides the event stream that updates CRDT state across replicas. *Context*: Collaborative editors (Figma, Notion), offline-first mobile apps, multi-region databases, peer-to-peer applications.

**CRDTs + Merkle Tree** — Verified Distributed Data  
CRDTs ensure conflict-free convergence; Merkle Trees provide cryptographic verification of data integrity and efficient sync detection. *Context*: Distributed version control (Git), blockchain systems, peer-to-peer file sharing, distributed databases requiring integrity verification.

**Strangler Fig + Sidecar** — Incremental Legacy Migration  
Strangler Fig routes traffic between legacy and new systems; Sidecar proxies handle the routing logic without modifying either system. *Context*: Monolith-to-microservices migrations, legacy modernization with API gateway interception, gradual rewrites of aging systems.

**REST + HATEOAS + Consumer-Driven Contracts** — Evolvable API Ecosystem  
REST provides resource-based uniform interface; HATEOAS enables dynamic discovery of available actions; Consumer-Driven Contracts ensure backward compatibility. *Context*: Public APIs, microservice ecosystems with independent deployments, APIs requiring evolution without breaking clients.

**Property-Based Testing + Consumer-Driven Contracts** — Comprehensive API Verification  
Property-Based Testing generates thousands of test cases to verify invariants; Consumer-Driven Contracts ensure provider meets consumer expectations. *Context*: Microservice API testing, serialization round-trip verification, ensuring backward compatibility across service boundaries.

**STM + Actor Model** — Hybrid Concurrency  
STM provides composable atomic transactions for shared state; Actors provide isolated message-passing concurrency. STM handles local shared state while Actors handle distributed coordination. *Context*: Haskell/Clojure applications mixing local and distributed concurrency, systems requiring both transactional and message-based patterns.

**Reactor + Proactor** — Hybrid Async I/O  
Reactor handles synchronous event demultiplexing; Proactor handles true async I/O with completion callbacks. Combined for systems mixing sync and async I/O patterns. *Context*: Cross-platform servers (Windows IOCP + epoll), applications requiring both polling and completion-based I/O.

**Hexagonal + CQRS + Event Sourcing + Actor Model** — Full DDD Stack  
Hexagonal provides architectural boundaries; CQRS separates concerns; Event Sourcing captures history; Actors encapsulate aggregates. *Context*: Large-scale distributed systems (Akka, Lagom, Axon), enterprise platforms requiring all four capabilities.

**Circuit Breaker + Bulkhead + Retry + Timeout** — Complete Resilience Pattern  
The four patterns work together: Timeout prevents indefinite waits; Retry handles transient failures; Circuit Breaker prevents retry storms; Bulkhead isolates failures. *Context*: Production microservices, cloud-native applications, any system calling external dependencies.

**Sidecar + Circuit Breaker + Bulkhead + mTLS** — Service Mesh Security Stack  
Sidecar proxies implement all cross-cutting concerns: Circuit Breaker and Bulkhead for resilience; mTLS for zero-trust security. *Context*: Istio/Linkerd deployments, enterprise Kubernetes clusters, regulated industries requiring consistent security and resilience.

**MapReduce + Pipeline + Higher-Order Functions + Fold** — Functional Data Pipeline  
MapReduce distributes processing; Pipeline chains stages; Higher-Order Functions define transformations; Fold aggregates results. *Context*: Spark/Flink applications, functional ETL pipelines, streaming analytics with complex aggregations.

**Monad + Functor + Applicative + Higher-Order Functions** — Full Functional Composition  
Functor maps single functions; Applicative applies functions in context; Monad chains dependent computations; Higher-Order Functions compose everything. *Context*: Haskell/Scala applications, effect systems, parser combinators, validation pipelines.

**Actor Model + CSP + Reactive Streams** — Multi-Paradigm Concurrency  
Actors for isolated stateful entities; CSP for synchronous coordination; Reactive Streams for async data flow with back-pressure. *Context*: Complex concurrent systems mixing paradigms, applications requiring both message-passing and stream processing.

**CQRS + Event Sourcing + CRDTs + Merkle Tree** — Distributed Audit System  
CQRS separates concerns; Event Sourcing captures all changes; CRDTs enable multi-region convergence; Merkle Trees verify integrity. *Context*: Distributed ledgers, multi-region financial systems, collaborative platforms requiring verifiable history.

**REST + HATEOAS + Consumer-Driven Contracts + Property-Based Testing** — Robust API Development  
REST provides the architectural style; HATEOAS enables discoverability; Consumer-Driven Contracts ensure compatibility; Property-Based Testing verifies edge cases. *Context*: Enterprise API platforms, public API development, microservice ecosystems with strict quality requirements.

**Clean Architecture + CQRS + Event Sourcing + Reactive Streams** — Modern Enterprise Stack  
Clean Architecture enforces boundaries; CQRS optimizes read/write; Event Sourcing provides audit trail; Reactive Streams handle async data flow. *Context*: Event-driven enterprise applications, real-time analytics platforms, systems requiring both structure and reactivity.

**Strangler Fig + Sidecar + Circuit Breaker + Consumer-Driven Contracts** — Safe Legacy Migration  
Strangler Fig enables incremental migration; Sidecar handles routing; Circuit Breaker protects against legacy failures; Consumer-Driven Contracts ensure compatibility. *Context*: Large-scale legacy modernization, risk-averse enterprise migrations, gradual monolith decomposition.