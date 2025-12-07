# Gang of Four Design Patterns

| **Category**   | **Pattern**                | **Short Description**                                                                                     | **Typical Context of Usage**                                                                                   |
|----------------|----------------------------|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| **Creational** | **Abstract Factory**       | Creates families of related objects without specifying concrete classes                                   | UI toolkits, cross-platform apps, database drivers; designed upfront for product families                     |
| **Creational** | **Builder**                | Constructs complex objects step by step                                                                   | Fluent APIs, test data builders, configuration objects; when construction has many optional parameters        |
| **Creational** | **Factory Method**         | Defers instantiation to subclasses                                                                        | Frameworks, plugin systems; designed early when subclasses determine object types                              |
| **Creational** | **Prototype**              | Creates new objects by cloning existing ones                                                              | Game entities, document templates, performance-critical object creation                                        |
| **Creational** | **Singleton**              | Ensures a class has only one instance with global access                                                  | Logging, configuration, connection pools; often overused, consider DI alternatives                             |
| **Structural** | **Adapter**                | Converts one interface to another expected by clients                                                     | Legacy integration, third-party library wrapping; very common refactoring pattern                              |
| **Structural** | **Bridge**                 | Separates abstraction from implementation so both can vary independently                                  | Cross-platform graphics, device drivers; designed upfront when both dimensions need to evolve                  |
| **Structural** | **Composite**              | Treats individual objects and compositions uniformly (tree structures)                                    | File systems, UI component trees, org charts; natural fit for hierarchical data                                |
| **Structural** | **Decorator**              | Adds responsibilities dynamically without subclassing                                                     | I/O streams, middleware, logging wrappers; common refactoring to add behavior                                  |
| **Structural** | **Facade**                 | Provides a simplified interface to a complex subsystem                                                    | API gateways, library wrappers, legacy system fronts; very common for reducing complexity                      |
| **Structural** | **Flyweight**              | Shares fine-grained objects to reduce memory usage                                                        | Text editors (characters), game tiles, caching; performance optimization for many similar objects              |
| **Structural** | **Proxy**                  | Controls access to another object                                                                         | Lazy loading, access control, remote proxies, caching proxies; added when access control is needed             |
| **Behavioral** | **Chain of Responsibility**| Passes requests along a chain of handlers                                                                 | Middleware pipelines, event bubbling, approval workflows; when multiple handlers may process a request         |
| **Behavioral** | **Command**                | Encapsulates a request as an object                                                                       | Undo/redo, task queues, macro recording; common in UI and transaction systems                                  |
| **Behavioral** | **Interpreter**            | Defines a grammar and interpreter for a simple language                                                   | DSLs, rule engines, expression evaluation; rare, used when building custom languages                           |
| **Behavioral** | **Iterator**               | Sequential access to aggregate elements without exposing underlying representation                        | Collection traversal; part of standard libraries, designed early                                                |
| **Behavioral** | **Mediator**               | Centralizes complex communications between objects                                                        | Chat rooms, GUI coordination, air-traffic control; reduces coupling in many-to-many interactions               |
| **Behavioral** | **Memento**                | Captures and restores an object's internal state without breaking encapsulation                           | Undo frameworks, game saves, snapshot/rollback; added when rollback capability is needed                        |
| **Behavioral** | **Observer**               | One-to-many dependency; objects are notified of state changes                                             | Event systems, pub/sub, MVC, reactive UIs; extremely common in UI and event-driven code                         |
| **Behavioral** | **State**                  | Changes object behavior when internal state changes (appears to change class)                            | TCP connections, game character states, workflows; heavy state-dependent behavior                              |
| **Behavioral** | **Strategy**               | Defines a family of interchangeable algorithms                                                            | Payment methods, compression, sorting; pluggable behavior, very common refactoring pattern                     |
| **Behavioral** | **Template Method**        | Defines algorithm skeleton in base class; subclasses override steps                                      | Frameworks (Servlet, JUnit, Spring lifecycle); designed when you want to enforce algorithm structure            |
| **Behavioral** | **Visitor**                | Separates algorithm from object structure; adds operations without changing classes                      | AST traversal, report generation on complex hierarchies; stable structure, many new operations                 |

### Quick Context Summary
- **Most common in refactoring**: Adapter, Facade, Decorator, Strategy, Observer, Command
- **Designed upfront / frameworks**: Factory Method, Abstract Factory, Template Method, Singleton
- **Performance**: Flyweight, Prototype
- **Hierarchies & trees**: Composite, Visitor

### Most Common in Refactoring

**Adapter**  
The go-to pattern when integrating third-party libraries or legacy systems with incompatible interfaces. Rather than modifying existing code, you wrap it with an adapter that translates between interfaces. In practice, every codebase accumulates adapters around external dependencies—database drivers, payment gateways, cloud SDKs. The pattern is so common that many developers apply it instinctively without naming it. Modern dependency injection frameworks encourage adapter-style wrappers for testability.

**Facade**  
When a subsystem grows complex—dozens of classes with intricate interactions—Facade provides a simplified entry point. API gateways are essentially facades over microservice meshes. Library authors create facades to hide implementation complexity from consumers. During refactoring, extracting a facade is often the first step toward making a tangled codebase manageable. The pattern appears everywhere: ORMs facade over raw SQL, logging frameworks facade over multiple output targets, and cloud SDKs facade over REST APIs.

**Decorator**  
The pattern that makes Java's I/O streams work: `new BufferedReader(new InputStreamReader(new FileInputStream(...)))`. Decorators wrap objects to add behavior without modifying the original class. In modern codebases, middleware stacks (Express.js, ASP.NET Core) are decorator chains. Logging, caching, authentication, and compression are commonly added via decorators. The pattern shines when you need to combine behaviors in different configurations—each decorator is independent and composable.

**Strategy**  
One of the most frequently refactored-to patterns. When you find yourself with a switch statement or if-else chain selecting between algorithms, Strategy is the answer. Payment processing (PayPal, Stripe, credit card), file format handling (JSON, XML, CSV), and compression algorithms are classic examples. The pattern enables runtime algorithm selection and simplifies testing—each strategy can be tested in isolation. Modern functional programming often replaces Strategy with first-class functions, but the concept remains identical.

**Observer**  
The backbone of event-driven programming. Every UI framework uses Observer to connect user actions to handlers. Reactive programming (RxJS, Project Reactor) is Observer evolved. The pub/sub pattern in message queues is distributed Observer. MVC architectures use Observer to keep views synchronized with model state. The pattern is so fundamental that most languages provide built-in support (C# events, Java PropertyChangeListener, JavaScript EventEmitter). Overuse leads to debugging nightmares—event chains become hard to trace.

**Command**  
Encapsulating requests as objects unlocks powerful capabilities: undo/redo, macro recording, request queuing, and transaction logging. Every application with an undo feature uses Command. Task queues (Celery, Sidekiq) are command processors. The pattern separates "what to do" from "when to do it," enabling deferred execution, retry logic, and audit trails. Combined with Memento, Command enables sophisticated undo systems; combined with Composite, it enables macro commands.

### Designed Upfront / Frameworks

**Factory Method**  
The pattern that lets frameworks call your code. When a framework defines an algorithm but needs you to supply specific objects, it uses Factory Method. Spring's `@Bean` methods, Django's model managers, and JUnit's test case instantiation all follow this pattern. Unlike Abstract Factory (which creates families), Factory Method focuses on a single product type. The pattern appears early in design when you know subclasses will need to customize object creation.

**Abstract Factory**  
When your application must support multiple "themes" or "platforms" with families of related objects, Abstract Factory provides the structure. UI toolkits use it to create platform-specific widgets (buttons, scrollbars, dialogs) that work together. Database abstraction layers use it to create compatible connections, commands, and result sets. The pattern requires upfront design—retrofitting it is painful. Modern dependency injection containers often replace explicit Abstract Factories, but the concept persists in configuration-driven object creation.

**Template Method**  
Frameworks love this pattern. Define the algorithm skeleton in a base class; let subclasses override specific steps. Servlet's `doGet`/`doPost`, JUnit's `setUp`/`tearDown`, and Spring's lifecycle callbacks all use Template Method. The pattern enforces consistency—every subclass follows the same overall flow—while allowing customization at specific extension points. It's the "Hollywood Principle" in action: don't call us, we'll call you. The pattern is designed into frameworks from the start; it's rarely added later.

**Singleton**  
The most controversial GoF pattern. Logging, configuration, connection pools, and caches often use Singleton to ensure a single instance with global access. However, Singletons create hidden dependencies, complicate testing, and cause issues in concurrent environments. Modern best practice favors dependency injection: let a DI container manage the single instance rather than hardcoding it into the class. Despite criticism, Singleton remains common—just be aware of its trade-offs and prefer DI when possible.

### Performance Patterns

**Flyweight**  
When your application creates millions of similar objects, Flyweight dramatically reduces memory usage by sharing common state. Text editors use Flyweight for character objects—each character shares font/style data while only storing its position. Game engines use it for tiles, particles, and sprites. The pattern separates intrinsic state (shared) from extrinsic state (unique per instance). Implementation typically involves a factory that caches and returns existing flyweights. String interning in Java and Python is a language-level Flyweight.

**Prototype**  
When object creation is expensive—complex initialization, database lookups, or deep object graphs—Prototype avoids the cost by cloning existing instances. Game engines clone prototype entities rather than reconstructing them. Document editors clone template objects for new documents. The pattern is particularly valuable when the exact class to instantiate is determined at runtime. JavaScript's prototypal inheritance is the pattern built into the language. In languages with expensive constructors, Prototype can provide significant performance gains.

### Hierarchies & Trees

**Composite**  
The pattern for tree structures where you want to treat leaves and branches uniformly. File systems (files and directories), UI components (widgets and containers), and organizational charts all use Composite. The pattern enables recursive operations—calculating total size, rendering nested components, or traversing hierarchies—without type-checking at every level. Composite is often combined with Iterator (for traversal) and Visitor (for operations). The pattern is designed upfront when you recognize hierarchical data; it's fundamental to how we model nested structures.

**Visitor**  
When you have a stable object structure but need to add many operations over time, Visitor separates the operations from the structure. Compilers use Visitor extensively—the AST structure is stable, but you add visitors for type-checking, optimization, code generation, and pretty-printing. The pattern enables adding new operations without modifying existing classes (Open/Closed Principle). The trade-off: adding new element types requires modifying all visitors. Visitor works best when the structure changes rarely but operations change frequently.

---

### Most Useful Combinations and Pairings

**Command + Memento** — Undo/Redo Systems  
Command encapsulates actions as objects; Memento captures state snapshots before each action. Together they enable robust undo/redo. *Context*: Text editors, graphic design tools (Photoshop, Figma), IDEs, any application requiring reversible operations.

**Composite + Visitor** — Operations on Tree Structures  
Composite builds the tree; Visitor traverses it to perform operations without modifying node classes. *Context*: Compilers (AST traversal), file system utilities, report generators, XML/JSON processors.

**Composite + Iterator** — Uniform Tree Traversal  
Composite defines the hierarchy; Iterator provides a consistent way to traverse it. *Context*: UI component trees, document object models, organizational hierarchies.

**Factory Method + Template Method** — Framework Extension Points  
Template Method defines the algorithm skeleton; Factory Method lets subclasses decide which objects to create within that algorithm. *Context*: Application frameworks (Spring, Django), game engines, document processors.

**Abstract Factory + Singleton** — Centralized Object Families  
Abstract Factory creates related objects; Singleton ensures one factory instance. *Context*: UI toolkit factories, database connection factories, cross-platform application bootstrapping.

**Strategy + Factory** — Dynamic Algorithm Selection  
Factory creates the appropriate Strategy based on runtime conditions. *Context*: Payment processing (PayPal, Stripe, credit card), file format handlers, compression algorithm selection.

**Decorator + Strategy** — Layered Behavior with Swappable Core  
Strategy provides the core algorithm; Decorators wrap it with additional behavior. *Context*: I/O streams with encryption/compression, logging with different formatters, HTTP clients with retry/caching.

**Observer + Mediator** — Decoupled Event Coordination  
Observer notifies interested parties; Mediator coordinates complex interactions between them. *Context*: Chat applications, stock trading dashboards, multiplayer game lobbies.

**Proxy + Decorator** — Access Control with Enhanced Behavior  
Proxy controls access (authentication, lazy loading); Decorator adds functionality. *Context*: Secure API clients, cached remote services, logged database connections.

**State + Strategy** — Context-Dependent Behavior  
State manages transitions between behaviors; Strategy provides the interchangeable algorithms within each state. *Context*: Game AI (different strategies per game phase), order processing (different rules per status), media players (different controls per mode).

**Chain of Responsibility + Command** — Flexible Request Processing  
Command encapsulates the request; Chain of Responsibility routes it through handlers. *Context*: Middleware stacks (Express.js, ASP.NET), approval workflows, event processing pipelines.

**Builder + Prototype** — Complex Object Cloning  
Builder constructs a template object; Prototype clones it for variations. *Context*: Game level editors, document templates, test fixture generation.

**Facade + Adapter** — Simplified Legacy Integration  
Adapter converts interfaces; Facade provides a clean API over the adapted subsystem. *Context*: Wrapping legacy systems, third-party SDK integration, microservice API gateways.

**Flyweight + Factory** — Efficient Shared Object Management  
Factory manages a pool of Flyweight instances, returning existing ones when possible. *Context*: Text rendering (character glyphs), game tile systems, icon libraries, connection pooling.

**MVC: Observer + Strategy + Composite** — Model-View-Controller Architecture  
Observer keeps views synchronized with model state changes; Strategy allows controllers to implement different input handling behaviors; Composite enables nested view hierarchies. *Context*: GUI frameworks (Swing, Cocoa), web frameworks (Rails, Django), desktop applications—the foundational architecture for interactive applications.

**Command + Memento + Composite** — Macro Undo/Redo Systems  
Command encapsulates actions; Memento captures state snapshots; Composite groups commands into macro operations that can be undone/redone as a unit. *Context*: Professional editing software (Photoshop, Premiere), CAD systems, IDEs with complex refactoring, any application requiring grouped reversible operations.

**Composite + Iterator + Visitor** — Complete Tree Processing  
Composite builds the hierarchical structure; Iterator provides traversal mechanisms (depth-first, breadth-first); Visitor performs operations on nodes without modifying their classes. *Context*: Compilers (AST processing), XML/JSON document processors, file system utilities, report generators on complex hierarchies.

**Interpreter + Composite + Visitor + Iterator** — Language Processing Pipeline  
Interpreter defines grammar rules; Composite represents the abstract syntax tree; Visitor executes semantic analysis or code generation; Iterator traverses the tree structure. *Context*: DSL engines, rule engines, expression evaluators, query language processors, template engines.

**Chain of Responsibility + Command + Composite** — Hierarchical Request Processing  
Command encapsulates requests as objects; Composite groups handlers into hierarchical chains; Chain of Responsibility routes requests through the handler tree. *Context*: Middleware stacks, approval workflow systems, event bubbling in UI frameworks, plugin architectures with nested handlers.

**Flyweight + Factory + Singleton** — Centralized Shared Object Pool  
Singleton ensures one factory instance; Factory manages object creation and lookup; Flyweight shares intrinsic state across many contexts. *Context*: Font/glyph rendering systems, game asset management, connection pooling, symbol tables in compilers.

**State + Strategy + Factory** — Dynamic Behavioral Systems  
State manages object lifecycle and transitions; Strategy provides interchangeable algorithms within each state; Factory creates appropriate strategies based on current state. *Context*: Game AI (different behaviors per game phase), order processing systems, media player controls, workflow engines with state-dependent rules.

**Observer + Mediator + Command** — Decoupled Event Architecture  
Observer broadcasts state changes; Mediator coordinates complex interactions between multiple observers; Command encapsulates event handlers as objects for queuing/logging. *Context*: Real-time trading platforms, chat applications, multiplayer game lobbies, IoT device coordination, reactive dashboards.

**Abstract Factory + Builder + Prototype** — Flexible Complex Object Creation  
Abstract Factory creates families of related objects; Builder handles step-by-step construction of complex instances; Prototype clones configured templates for variations. *Context*: Game level editors, document template systems, test data generation, configuration management with multiple environments.

**Decorator + Proxy + Adapter** — Layered Interface Management  
Adapter converts incompatible interfaces; Proxy controls access and adds cross-cutting concerns; Decorator layers additional functionality. *Context*: API gateway implementations, secure service wrappers, legacy system integration with modern caching/logging/authentication layers.
