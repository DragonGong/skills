# Pattern Catalog

This is a working catalog for agents. Each pattern entry is written as: problem pressure, use when, implementation moves, benefits, and traps.

## Creational Patterns

Creational patterns hide concrete construction so clients can work through interfaces. Use them when construction policy is a source of coupling or duplication. Do not use them for every `new`/constructor call.

### Abstract Factory

Problem pressure: callers must create a family of related objects, and mixing products from different families would be wrong.

Use when:

- the system must be configured with one product family at a time
- product objects must be compatible with each other
- callers should see product interfaces, not concrete product classes
- platform, theme, vendor, database, or protocol families vary together

Implementation moves:

- define abstract product interfaces
- define a factory interface with one creation method per product type
- create one concrete factory per product family
- pass the factory into clients or bootstrap code

Benefits:

- concrete product classes are isolated
- switching a whole product family becomes localized
- family consistency is enforced by construction

Traps:

- adding a new product kind changes every factory
- too many product families can make the design heavy
- do not use when only one product varies independently

### Builder

Problem pressure: constructing a complex object is a multi-step process, and the same construction sequence should produce different representations.

Use when:

- parsing, importing, compiling, report generation, query building, or object graph assembly is complex
- construction steps are stable but the result representation varies
- clients should not know assembly order or intermediate representation

Implementation moves:

- separate the director/orchestration from the builder/result representation
- put step methods on the builder
- let concrete builders store intermediate state and expose the final result
- keep validation near the builder when it concerns construction invariants

Benefits:

- separates construction algorithm from representation
- lets one process produce multiple outputs
- keeps complex assembly out of callers

Traps:

- overkill for simple constructors or parameter objects
- builder state can become mutable and error-prone; document lifecycle

### Factory Method

Problem pressure: a framework or superclass knows when an object is needed but not which concrete subclass should be created.

Use when:

- subclasses should decide which product to instantiate
- a base class needs a hook for creating collaborators
- creation is part of a framework lifecycle
- parallel hierarchies need corresponding helper objects

Implementation moves:

- define a product interface
- put a creation method on the creator/base class
- let subclasses override the creation method
- keep client code using the product interface

Benefits:

- removes concrete product names from the base workflow
- gives subclasses a controlled extension hook

Traps:

- can force subclassing just for construction
- unnecessary when the created class never varies
- often a stepping stone toward Abstract Factory, Builder, or Prototype as variation grows

### Prototype

Problem pressure: creating new objects by class name would create many trivial creator classes, or product classes are selected/configured at runtime.

Use when:

- instances can be cloned safely
- configured examples are easier than many subclasses
- products can be registered dynamically
- loading or plugin systems specify classes at runtime

Implementation moves:

- define a clone/copy operation
- store prototypes in the client, factory, registry, or palette
- clone the selected prototype and then adjust instance-specific state
- make deep vs shallow copy rules explicit

Benefits:

- reduces subclass/factory proliferation
- can add/remove product kinds at runtime
- captures configured state directly in the prototype

Traps:

- cloning object graphs can be hard
- shared mutable state bugs are common
- not suitable when identity, external handles, or resources cannot be copied safely

### Singleton

Problem pressure: exactly one instance must coordinate a process-wide resource or invariant.

Use only when:

- there is a true process-wide single instance requirement
- access must be controlled centrally
- lifecycle and test replacement are understood

Implementation moves:

- hide direct construction
- expose a controlled access point
- handle lazy initialization and thread safety
- prefer dependency injection around singleton-backed services when tests need replacement

Benefits:

- controlled access to the sole instance
- avoids uncontrolled global variable sprawl

Traps:

- often becomes global mutable state
- hides dependencies from tests and callers
- subclass/configuration/lifecycle issues can become subtle
- do not use as a convenient service locator

## Structural Patterns

Structural patterns shape how objects/classes are composed. Use them when boundaries, interfaces, object graphs, access, or representation are the pressure point.

### Adapter

Problem pressure: an existing class or external API has the wrong interface for the client.

Use when:

- a vendor/legacy class should work behind a domain interface
- you cannot or should not modify the existing class
- one boundary needs translation between representations
- several unrelated implementations must satisfy one expected client interface

Implementation moves:

- define the target interface the client wants
- wrap or subclass the adaptee depending on language and ownership
- translate calls, data shapes, errors, and lifecycle semantics
- keep adapter logic at the boundary, not inside domain code

Benefits:

- reuses existing code without leaking its interface
- keeps clients stable while dependencies vary

Traps:

- adapter is not a place for business rules
- too many adapters may indicate the target interface is wrong

### Bridge

Problem pressure: abstraction and implementation vary along independent dimensions, and inheritance would create a combinatorial subclass grid.

Use when:

- both the public abstraction and backend/platform implementation evolve
- implementation must be selected or changed at runtime
- clients should not depend on platform-specific classes
- subclass names start combining two axes, such as `XIconWindow`, `PMIconWindow`

Implementation moves:

- split abstraction hierarchy from implementation hierarchy
- give the abstraction a reference to an implementor interface
- implement high-level operations in terms of primitive implementor operations
- choose implementor in construction/bootstrap code

Benefits:

- decouples interface and implementation
- avoids subclass explosion
- lets implementation change without changing clients

Traps:

- heavier than Adapter; use Bridge when you anticipate both axes
- abstraction and implementor interfaces need careful naming

### Composite

Problem pressure: clients should treat individual objects and object groups uniformly in a part-whole tree.

Use when:

- domain has recursive structures: UI components, ASTs, scene graphs, menu trees, file trees
- leaf-vs-container checks are spreading through clients
- operations should naturally recurse over children

Implementation moves:

- define a component interface for common operations
- implement leaves without children
- implement composites that store child components and forward/reduce operations
- decide whether parent references are needed

Benefits:

- simplifies clients by removing leaf/composite special cases
- makes new component types easier to add
- expresses part-whole structure explicitly

Traps:

- type system may not enforce allowed child types
- component interface can become too broad if child operations are forced onto leaves

### Decorator

Problem pressure: optional responsibilities must be added to individual objects without subclassing every combination.

Use when:

- behavior should be added/removed dynamically
- responsibilities are stackable
- subclass combinations are exploding
- base classes should stay lightweight

Implementation moves:

- define a component interface
- wrap a component in a decorator implementing the same interface
- forward calls and add behavior before/after delegation
- compose decorators in the order required by behavior

Benefits:

- flexible alternative to inheritance
- pay only for features in use
- keeps optional responsibilities separate

Traps:

- many tiny wrappers can be hard to debug
- decorator identity differs from wrapped object identity
- use Strategy instead when changing an internal algorithm is simpler than wrapping externally

### Facade

Problem pressure: clients depend on too many subsystem classes or need a simple entry point to a complex subsystem.

Use when:

- a subsystem is powerful but hard for ordinary callers to use
- clients import many internal classes from one subsystem
- you want to layer subsystems through stable entry points
- you need a default workflow while still permitting advanced access

Implementation moves:

- define a small high-level API around common use cases
- keep subsystem internals behind the facade boundary
- let advanced clients access internals only when necessary and intentional
- use the facade to stabilize dependency direction

Benefits:

- reduces client knowledge
- weakens coupling between subsystem and clients
- improves layering and portability

Traps:

- facade can become a god object if it owns all behavior
- do not hide necessary domain concepts behind a vague API

### Flyweight

Problem pressure: there are many fine-grained objects with shareable intrinsic state, and memory cost matters.

Use when:

- object count is very large
- much state can be shared
- context-dependent state can be stored/passed externally
- identity of individual flyweight instances is not semantically important

Implementation moves:

- split intrinsic state from extrinsic state
- share flyweight objects through a factory/cache
- pass context into operations instead of storing it on each object
- measure memory and runtime trade-offs

Benefits:

- large memory savings when sharing is high
- can make fine-grained object models practical

Traps:

- extra lookup/context-passing cost
- parent/context references cannot live directly on shared objects
- do not use without evidence of object-count or memory pressure

### Proxy

Problem pressure: clients need the same subject interface, but direct access requires control, laziness, remote forwarding, protection, caching, or bookkeeping.

Use when:

- expensive objects should load on demand
- remote objects need local representatives
- access must be checked
- copy-on-write, reference counting, caching, or locking should be hidden

Implementation moves:

- define a subject interface
- implement proxy with the same interface
- store a reference or identifier for the real subject
- perform access logic, then forward

Benefits:

- hides access complexity
- keeps clients unaware of remote/lazy/protected mechanics

Traps:

- proxy is not for adding optional behavior; use Decorator for that
- forwarding boilerplate can grow
- identity/equality semantics may surprise callers

## Behavioral Patterns

Behavioral patterns assign responsibility for algorithms and object communication. They are especially useful for branch explosions, state machines, command dispatch, and notification logic.

### Chain Of Responsibility

Problem pressure: one of several objects may handle a request, and senders should not know which one.

Use when:

- an existing object chain/tree can naturally pass requests upward or onward
- handler order matters
- handlers can be added/removed dynamically
- sender should not depend on every possible receiver

Implementation moves:

- define a common handler interface
- give each handler a successor or next handler
- handle or forward the request
- decide what happens when no handler accepts the request

Benefits:

- decouples sender from receiver
- flexible responsibility assignment

Traps:

- request handling is not guaranteed unless enforced
- debugging long chains can be hard
- avoid when a direct receiver is known

### Command

Problem pressure: a request should be represented as an object so it can be queued, logged, undone, composed, scheduled, retried, or bound to UI actions.

Use when:

- invoker should not know receiver details
- actions need undo/redo or history
- operations must be queued, logged, retried, or composed
- callbacks need richer state than a function pointer/closure

Implementation moves:

- define a command interface such as execute/undo when needed
- store receiver and request parameters in the command
- let invokers depend only on command interface
- use composite commands for macros

Benefits:

- decouples invoker from receiver
- commands become first-class values
- easy to add new actions

Traps:

- command classes can proliferate
- closures/functions may be enough for simple callbacks
- undo requires careful state capture, often with Memento

### Interpreter

Problem pressure: a simple language or rule grammar should be represented directly as objects.

Use when:

- grammar is small and stable enough to model by classes
- expressions form an AST
- new interpretation operations are useful

Implementation moves:

- define expression node types for grammar rules
- implement an interpret/evaluate operation
- use Composite for tree structure when needed
- consider Visitor for additional operations over the AST

Benefits:

- grammar extensions can be localized
- AST objects make expressions explicit

Traps:

- complex grammars create many classes
- parser/compiler generators may be better

### Iterator

Problem pressure: clients need to traverse an aggregate without knowing its representation.

Use when:

- aggregate internals should remain hidden
- multiple traversal orders exist
- multiple traversals may be active at once
- clients should not carry indexing/tree-walking logic

Implementation moves:

- define iterator operations for movement/current/done semantics or use language iteration protocols
- let aggregate create the appropriate iterator
- store traversal state in the iterator
- consider internal vs external iterator style

Benefits:

- simplifies aggregate interface
- supports traversal variants
- hides representation

Traps:

- fail-fast/concurrent mutation rules must be clear
- built-in language iterators may already solve this

### Mediator

Problem pressure: many peer objects communicate directly, producing tangled dependencies and protocols.

Use when:

- colleagues have many-to-many interactions
- communication rules are complex but localized
- you want colleagues reusable independently
- a UI/dialog/workflow coordinator owns interaction rules

Implementation moves:

- define a mediator/coordinator object
- make colleagues notify or call the mediator
- centralize interaction policy in the mediator
- keep colleague interfaces small

Benefits:

- reduces peer coupling
- makes protocol easier to inspect
- limits subclassing of colleagues

Traps:

- mediator can become a monolith
- Observer may be better for simple data-change notification

### Memento

Problem pressure: object state must be captured and restored without exposing internals.

Use when:

- undo/rollback/snapshot is needed
- exposing state would break encapsulation
- another object should hold snapshots but not inspect them

Implementation moves:

- originator creates and restores mementos
- caretaker stores mementos without depending on internals
- keep a narrow public memento interface
- use incremental snapshots if full copies are expensive

Benefits:

- preserves encapsulation
- simplifies originator by letting caretakers manage history

Traps:

- snapshots may be expensive
- lifecycle and memory cleanup matter
- language visibility rules may not enforce narrow/wide interfaces cleanly

### Observer

Problem pressure: when one object changes, multiple dependents must stay up to date without tight coupling.

Use when:

- one subject has many dynamic dependents
- subject and observers live in different layers
- updates should be broadcast to unknown subscribers
- UI/model, cache invalidation, metrics, or event-style dependency updates are needed

Implementation moves:

- define subject attach/detach/notify operations
- define observer update interface
- decide push vs pull update style
- guard against cycles, ordering surprises, and stale subscriptions

Benefits:

- subject and observers vary independently
- subscribers can be added/removed dynamically
- supports broadcast communication

Traps:

- update chains can be hard to trace
- unexpected cascading notifications
- Mediator may be better when a central protocol must be explicit

### State

Problem pressure: behavior depends on internal state, and state conditionals are spreading across operations.

Use when:

- several methods switch on the same state
- adding a state would require editing many branches
- transitions and state-specific behavior are important domain concepts

Implementation moves:

- define a state interface matching state-dependent operations
- put state-specific behavior in concrete state objects
- let context delegate to current state
- decide whether state objects or context owns transitions

Benefits:

- localizes state-specific behavior
- removes large state conditionals
- makes new states explicit

Traps:

- more classes/files
- transition logic can become scattered if not assigned clearly
- do not use for one local conditional

### Strategy

Problem pressure: an algorithm or policy varies independently from the object using it.

Use when:

- many related algorithms share one role
- a long function switches on algorithm/policy
- clients should configure behavior
- algorithm details should be hidden from the context

Implementation moves:

- define a strategy interface for the varying operation
- create concrete strategies for algorithms/policies
- inject or select a strategy in the context
- keep context data passed through a narrow parameter set

Benefits:

- replaces algorithm conditionals
- isolates algorithm implementation
- makes policies testable independently

Traps:

- clients must know or be given the right strategy
- many tiny strategies may be overkill
- use Template Method when inheritance hooks are already the natural extension point

### Template Method

Problem pressure: an algorithm skeleton is stable, but some steps vary in subclasses.

Use when:

- framework/base class should control operation order
- subclasses fill primitive steps
- common code should be factored into a base workflow

Implementation moves:

- put the final/high-level algorithm in the base class where language allows
- call primitive/hook operations for variable steps
- document which hooks are required vs optional
- keep base class invariants protected

Benefits:

- avoids duplicating algorithm skeletons
- gives subclasses controlled extension points

Traps:

- inheritance couples subclasses to base internals
- too many hooks make lifecycle hard to understand
- Strategy is often better when behavior should vary at runtime

### Visitor

Problem pressure: many operations must be performed over a stable object structure, and adding operations should not require editing every element class.

Use when:

- object structure has many element types but changes rarely
- operations over elements change often
- operation code is currently scattered across element classes or type switches
- traversal can be separated from operation behavior

Implementation moves:

- define a visitor interface with visit methods for element types
- give elements an accept method that calls the right visit method
- put each operation in a concrete visitor
- combine with Composite/Iterator for traversal

Benefits:

- adds new operations without changing element classes
- gathers related operation code in one visitor
- can work across heterogeneous object structures

Traps:

- adding new element types changes every visitor
- visitor may need too much access to element internals
- double dispatch mechanics can be awkward in some languages
