# The Twelve-Factor App

| **#** | **Factor**              | **Principle**                                                    | **Typical Implementation**                                                                                      |
|-------|-------------------------|------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| I     | **Codebase**            | One codebase tracked in revision control, many deploys           | Git/GitHub repository; same code for dev, staging, production; shared code extracted to libraries              |
| II    | **Dependencies**        | Explicitly declare and isolate dependencies                      | package.json, requirements.txt, Gemfile; virtual environments, containers; no reliance on system packages      |
| III   | **Config**              | Store config in the environment                                  | Environment variables; .env files (not committed); secrets managers (Vault, AWS Secrets Manager)               |
| IV    | **Backing Services**    | Treat backing services as attached resources                     | Database URLs in config; swap local/cloud services without code changes; connection strings for all services   |
| V     | **Build, Release, Run** | Strictly separate build and run stages                           | CI/CD pipelines; Docker images; immutable releases with unique IDs; rollback capability                        |
| VI    | **Processes**           | Execute the app as one or more stateless processes               | No sticky sessions; session state in Redis/Memcached; share-nothing architecture; horizontal scaling           |
| VII   | **Port Binding**        | Export services via port binding                                 | Self-contained web servers (Express, Uvicorn, Puma); no external container required; apps as backing services  |
| VIII  | **Concurrency**         | Scale out via the process model                                  | Multiple process types (web, worker, scheduler); process managers (systemd, Kubernetes); horizontal scaling    |
| IX    | **Disposability**       | Maximize robustness with fast startup and graceful shutdown      | Quick startup times; SIGTERM handling; idempotent jobs; crash-only design; queue-based job recovery            |
| X     | **Dev/Prod Parity**     | Keep development, staging, and production as similar as possible | Docker Compose; same backing services everywhere; continuous deployment; developers deploy their own code      |
| XI    | **Logs**                | Treat logs as event streams                                      | Write to stdout; log aggregation (Fluentd, Logstash); centralized analysis (Splunk, ELK, Datadog)              |
| XII   | **Admin Processes**     | Run admin/management tasks as one-off processes                  | Same environment as app; migrations, REPL consoles, one-off scripts; shipped with application code             |

### Quick Context Summary
- **Foundation**: Codebase, Dependencies, Config
- **Deployment**: Build/Release/Run, Backing Services, Port Binding
- **Operations**: Processes, Concurrency, Disposability
- **Observability & Maintenance**: Dev/Prod Parity, Logs, Admin Processes

---

### Foundation Factors

**I. Codebase**  
Every twelve-factor app has exactly one codebase tracked in version control (Git, Mercurial), with many deploys stemming from it. Production, staging, and every developer's local environment are all deploys of the same codebase—just different versions. If you have multiple codebases, you have a distributed system, not a single app. If multiple apps share code, extract it into a library managed through your dependency system. This one-to-one mapping between codebase and app is fundamental to everything else in the methodology.

**II. Dependencies**  
A twelve-factor app never relies on implicit system-wide packages. All dependencies are explicitly declared in a manifest (package.json, requirements.txt, Gemfile, go.mod) and isolated during execution (node_modules, virtualenv, bundler). This means a new developer can clone the repo and run a single command to have everything needed. No "works on my machine" problems. Even system tools like ImageMagick or curl should be vendored if required. The combination of declaration and isolation ensures reproducible builds across all environments.

**III. Config**  
Configuration that varies between deploys—database URLs, API keys, feature flags—must be stored in environment variables, not in code. The litmus test: could you open-source your codebase right now without exposing credentials? Environment variables are language-agnostic, won't accidentally get committed, and can be changed per-deploy without code changes. Avoid grouping config into "environments" (development, staging, production); instead, treat each variable as an independent, orthogonal control. Modern tools like dotenv, Vault, and cloud secrets managers make this practical.

---

### Deployment Factors

**IV. Backing Services**  
Databases, message queues, caches, SMTP servers, and third-party APIs are all "attached resources" accessed via URLs or credentials stored in config. The app makes no distinction between local MySQL and Amazon RDS—both are just resources that can be attached or detached at will. This loose coupling means you can swap a misbehaving database for a fresh one restored from backup without any code changes. Every backing service is a resource; two databases means two resources. This abstraction enables portability and operational flexibility.

**V. Build, Release, Run**  
Strictly separate three stages: Build (compile code, fetch dependencies, create artifacts), Release (combine build with config to create an immutable, versioned release), and Run (execute processes from a release). You cannot modify code at runtime—changes require a new build. Every release has a unique ID (timestamp or version number) and releases are append-only; you never mutate an existing release. This separation enables reliable rollbacks, audit trails, and prevents "it worked in dev" surprises. CI/CD pipelines (GitHub Actions, GitLab CI, Jenkins) formalize this separation.

**VI. Port Binding**  
The app is completely self-contained and exports HTTP (or other protocols) by binding to a port. No external web server container (Apache, Tomcat) is required—the app includes its own server library (Express, Uvicorn, Puma, Jetty). In development, you visit localhost:3000; in production, a routing layer maps public hostnames to your port-bound processes. This self-containment means one app can become a backing service for another, accessed via URL. The pattern applies to any protocol—HTTP, WebSocket, Redis protocol, gRPC—not just web traffic.

---

### Operations Factors

**VII. Processes**  
Twelve-factor processes are stateless and share-nothing. Any data that must persist goes to a backing service (database, cache). Memory and filesystem are ephemeral—a restart wipes them. Never use sticky sessions; store session state in Redis or Memcached with TTL. This statelessness enables horizontal scaling: spin up more processes without coordination. Each process is identical and interchangeable. The filesystem can be used for brief, single-transaction caching (download, process, store result), but never assume it persists across requests.

**VIII. Concurrency**  
Scale out via the process model, not by making one process bigger. Different workloads get different process types: web processes handle HTTP requests, worker processes handle background jobs, scheduler processes trigger periodic tasks. Each process type can scale independently based on load. The Unix process model is the inspiration—small, focused processes managed by the OS or a process manager (systemd, Kubernetes, Foreman). Individual processes can still use threads or async I/O internally, but the primary scaling mechanism is adding more processes across machines.

**IX. Disposability**  
Processes can be started or stopped at a moment's notice. Fast startup (seconds, not minutes) enables rapid scaling and deployment. Graceful shutdown means handling SIGTERM properly: stop accepting new requests, finish current work, then exit. Worker processes return jobs to the queue on shutdown. Design for crash-only operation—if a process dies unexpectedly, the system recovers automatically. Idempotent operations and transactional job processing ensure no work is lost. This disposability is essential for elastic cloud environments where instances come and go constantly.

---

### Observability & Maintenance Factors

**X. Dev/Prod Parity**  
Minimize the gaps between development and production: time gap (deploy hours after writing, not weeks), personnel gap (developers deploy their own code), and tools gap (same backing services everywhere). Don't use SQLite locally and PostgreSQL in production—subtle incompatibilities will bite you. Docker and Docker Compose make running production-like environments locally trivial. The goal is continuous deployment with confidence: if it works in dev, it works in production. This parity reduces friction and enables rapid iteration.

**XI. Logs**  
Treat logs as event streams, not files. The app writes to stdout, unbuffered, and doesn't concern itself with routing or storage. The execution environment captures these streams and routes them to appropriate destinations—files for development, log aggregators (Fluentd, Logstash, Filebeat) for production, analysis systems (Splunk, ELK, Datadog) for insights. This separation means the app stays simple while operations teams can implement sophisticated log management without code changes. Structured logging (JSON) makes parsing and querying easier.

**XII. Admin Processes**  
Database migrations, console sessions, and one-off scripts run as one-off processes in the same environment as the app. They use the same codebase, config, and dependency isolation as regular processes. Admin code ships with application code to avoid version mismatches. Run migrations with `bundle exec rake db:migrate`, not by SSHing into a server and running commands manually. REPL shells (rails console, python manage.py shell) are invaluable for debugging. These processes are first-class citizens, not afterthoughts.

---

### Modern Extensions (Beyond the Original 12)

The original twelve factors were published in 2011. Modern practice has identified additional considerations:

**API First**  
Design APIs before implementation using OpenAPI/Swagger specifications, enabling contract-first development where frontend and backend teams work in parallel against agreed interfaces. API versioning strategies (URL path, headers, content negotiation) ensure backward compatibility as services evolve. Mock servers generated from specs let consumers develop before implementations exist. API gateways centralize cross-cutting concerns like rate limiting, authentication, and request transformation. This approach prevents the "API as afterthought" anti-pattern where internal data models leak into public interfaces. *Context*: Microservice architectures, public API platforms, mobile app backends, partner integrations, any system where multiple teams consume the same services.

**Telemetry**  
The three pillars of observability—logs, metrics, and traces—provide complete visibility into distributed systems. Metrics (Prometheus, StatsD, CloudWatch) capture aggregated numerical data: request rates, error percentages, latency percentiles, resource utilization. Distributed tracing (Jaeger, Zipkin, OpenTelemetry) follows requests across service boundaries, revealing where time is spent and where failures originate. Health checks (liveness, readiness probes) enable orchestrators to route traffic and restart unhealthy instances. Together with structured logs, these signals enable debugging production issues without reproducing them locally. Correlation IDs tie all three pillars together for a single request. *Context*: Kubernetes deployments, microservice debugging, SLA monitoring, capacity planning, incident response, performance optimization.

**Security**  
Security is a first-class concern woven throughout the development lifecycle, not bolted on at the end. Secrets management (HashiCorp Vault, AWS Secrets Manager, Azure Key Vault) centralizes credentials with rotation, auditing, and fine-grained access control—never commit secrets to code. Dependency scanning (Snyk, Dependabot, OWASP Dependency-Check) identifies vulnerable packages before they reach production. Container image scanning (Trivy, Clair, Anchore) catches vulnerabilities in base images and layers. Zero-trust networking assumes no implicit trust—every service-to-service call is authenticated and encrypted (mTLS via service mesh). Supply chain security (SBOM, signed images, SLSA compliance) verifies the integrity of everything you deploy. *Context*: Regulated industries (finance, healthcare), SOC 2 compliance, PCI-DSS requirements, enterprise applications, any system handling sensitive data.

**Authentication/Authorization**  
Externalize identity management rather than building it into each application. OAuth 2.0 and OpenID Connect (OIDC) provide standardized flows for authentication, with identity providers (Auth0, Okta, Keycloak, AWS Cognito) handling user management, MFA, and social login. JWT tokens carry claims between services, enabling stateless authentication. Authorization policies (OPA/Rego, Cedar, Casbin) centralize access control decisions, separating "who can do what" from application code. API gateways or service meshes can enforce policies at the edge. Role-based (RBAC) and attribute-based (ABAC) access control models scale from simple to complex permission requirements. Treat auth as a backing service—swap providers without changing application code. *Context*: Multi-tenant SaaS platforms, enterprise SSO integration, B2B applications, mobile apps, microservices requiring consistent authorization across services.

**Feature Flags / Progressive Delivery**  
Decouple deployment from release using feature flags (LaunchDarkly, Unleash, Flagsmith, Split). Deploy code to production but control who sees new features—enable for internal users first, then beta testers, then percentage rollouts, then everyone. Kill switches let you disable problematic features instantly without redeployment. A/B testing becomes trivial when features are flag-controlled. Trunk-based development becomes safer when incomplete features hide behind flags. Progressive delivery extends this with canary releases (route percentage of traffic to new version) and blue-green deployments. *Context*: Continuous deployment pipelines, risk-averse enterprises, product experimentation, gradual rollouts, instant rollback capability.

**Containerization & Orchestration**  
While the original twelve factors predate widespread container adoption, Docker and Kubernetes have become the standard implementation. Containers provide dependency isolation, consistent environments, and immutable artifacts. Kubernetes handles process management, scaling, health checks, and service discovery—implementing factors VI, VIII, and IX at the platform level. Helm charts and Kustomize manage configuration across environments. Service meshes (Istio, Linkerd) add observability, security, and traffic management without application changes. GitOps (ArgoCD, Flux) extends build/release/run with declarative, version-controlled infrastructure. *Context*: Cloud-native applications, multi-cloud deployments, platform engineering, any team running more than a handful of services.

**Resilience Patterns**  
Distributed systems fail in distributed ways. Circuit breakers (Resilience4j, Polly, Hystrix) prevent cascading failures by failing fast when dependencies are unhealthy. Retry with exponential backoff handles transient failures gracefully. Timeouts prevent indefinite waits. Bulkheads isolate failures so one misbehaving dependency doesn't exhaust all resources. Rate limiting protects services from traffic spikes. These patterns complement disposability—if processes can start and stop quickly, the system recovers faster from failures. Libraries and service meshes implement these patterns without cluttering application code. *Context*: Microservice architectures, cloud deployments, any system with external dependencies, high-availability requirements.

**Event-Driven Architecture**  
Extend backing services to include message brokers (Kafka, RabbitMQ, AWS SNS/SQS) for asynchronous communication. Event-driven patterns decouple producers from consumers, enabling independent scaling and deployment. Event sourcing captures all state changes as immutable events, providing audit trails and temporal queries. CQRS separates read and write models for independent optimization. Saga patterns coordinate distributed transactions without two-phase commit. These patterns complement stateless processes—events provide the communication mechanism between share-nothing services. *Context*: High-throughput systems, audit-heavy domains (finance, healthcare), eventual consistency requirements, complex business workflows, real-time data pipelines.
