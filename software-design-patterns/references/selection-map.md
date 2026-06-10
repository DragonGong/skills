# Selection Map

Use this file to decide whether the task needs no pattern, refactor-first cleanup, or a specific pattern family.

## Fast Decision

1. Is the current code readable, local, and single-purpose?
   - Yes: implement directly.
   - No: refactor first.
2. Is there a named variation point?
   - No: do the smallest cleanup; avoid a pattern.
   - Yes: continue.
3. Is the variation about object creation?
   - Use a creational pattern.
4. Is the variation about object shape, interface, access, or composition?
   - Use a structural pattern.
5. Is the variation about algorithms, state, requests, traversal, notifications, or object collaboration?
   - Use a behavioral pattern.
6. If two patterns seem plausible, choose the one whose intent matches the design pressure, not the one whose class diagram looks similar.

## Common Causes Of Redesign And Pattern Families

| Redesign pressure | What is leaking | Patterns to consider |
| --- | --- | --- |
| Callers instantiate concrete classes everywhere | product identity and construction policy | Factory Method, Abstract Factory, Prototype, Builder |
| Multiple related products must stay consistent | product family constraint | Abstract Factory |
| Construction is multi-step or representation-dependent | assembly process | Builder |
| Many nearly identical creator subclasses appear | product class identity | Prototype or Abstract Factory |
| One object must be unique across a process | instance access policy | Singleton, usually with caution |
| Code depends on a platform, vendor, or subsystem internals | implementation detail | Bridge, Abstract Factory, Facade, Adapter |
| Clients know object representation, storage, location, or loading rules | representation/access detail | Proxy, Memento, Bridge |
| Algorithms are copied or selected by conditionals | algorithm identity | Strategy, Template Method, Visitor, Builder |
| Long `if`/`switch` handles states | state identity and transitions | State |
| Multiple possible handlers are wired with nested conditionals | receiver choice | Chain of Responsibility, Command |
| Many peers talk to each other directly | communication protocol | Mediator, Observer |
| One change should notify many dependents | dependency update | Observer |
| Tree-like structures have leaf/composite special cases | part-whole structure | Composite, Iterator, Visitor |
| Optional features cause subclass explosion | combinable responsibility | Decorator, Strategy |
| Cannot modify a class but need it to fit | interface or behavior wrapping | Adapter, Decorator, Visitor |

## Variation Axis To Pattern

| What must vary independently? | First candidates |
| --- | --- |
| Product family | Abstract Factory |
| Complex construction process | Builder |
| Concrete class chosen by subclass/framework | Factory Method |
| Concrete class or state chosen at runtime by cloning | Prototype |
| Single instance access | Singleton |
| External or legacy interface | Adapter |
| Abstraction and implementation dimensions | Bridge |
| Part-whole tree | Composite |
| Optional stackable responsibilities | Decorator |
| Subsystem entry point | Facade |
| Memory cost of many similar objects | Flyweight |
| Access, laziness, remote object, protection | Proxy |
| Handler selected along an existing chain | Chain of Responsibility |
| Request as data; undo, queue, log, macro | Command |
| Simple grammar as objects | Interpreter |
| Traversal policy | Iterator |
| Peer interaction protocol | Mediator |
| Snapshot without exposing internals | Memento |
| Dependent updates | Observer |
| State-specific behavior | State |
| Algorithm/policy | Strategy |
| Stable algorithm skeleton with overridable steps | Template Method |
| New operations over stable object structure | Visitor |

## Smell To First Move

| Smell | First move | Pattern only if... |
| --- | --- | --- |
| Giant file | split by responsibility and dependency direction | each extracted responsibility has a stable variation point |
| Long function | extract phases and name decisions | phases vary independently or form an algorithm skeleton |
| Repeated branches on type | move behavior to polymorphic types or strategies | new variants are expected and callers should be closed to them |
| Repeated branches on state | extract state transition table or state objects | state-specific behavior spans multiple operations |
| Repeated construction code | centralize construction | construction policy varies by family, runtime, or subclass |
| Similar subclasses differ only by constants/config | collapse to configuration/prototype | instances can be cloned or configured safely |
| Vendor SDK appears across domain code | create an adapter/facade boundary | multiple vendors or test replacement matter |
| Object graph setup leaks everywhere | introduce builder/factory | assembly is complex or reused |
| Many observers manually updated | centralize notification | multiple dependents must stay in sync |

## No-Pattern Gates

Do not introduce a pattern when:

- one small helper function removes the duplication
- a single cohesive module is enough
- only one implementation exists and no boundary needs substitution
- the branch is short, local, and unlikely to grow
- a pattern would create more public API than the feature needs
- the codebase already has a simpler established convention

## Choosing Between Similar Patterns

- Factory Method vs Abstract Factory: Factory Method lets subclasses choose one product; Abstract Factory supplies a whole compatible product family.
- Abstract Factory vs Builder: Abstract Factory returns related products; Builder performs a multi-step assembly of one complex product.
- Builder vs Template Method: Builder separates construction result from construction algorithm; Template Method fixes an algorithm skeleton and lets subclasses fill steps.
- Prototype vs Factory Method: Prototype clones configured examples; Factory Method asks subclasses or creators to instantiate.
- Adapter vs Bridge: Adapter reconciles existing incompatible interfaces; Bridge is designed early to let abstraction and implementation evolve separately.
- Adapter vs Facade: Adapter makes one interface look like another expected interface; Facade creates a simpler entry point to a subsystem.
- Decorator vs Proxy: Decorator adds responsibilities; Proxy controls access.
- Decorator vs Strategy: Decorator wraps the object from outside; Strategy changes an internal behavior slot.
- Composite vs Decorator: Composite represents part-whole trees; Decorator stacks extra behavior around one component.
- State vs Strategy: State changes behavior as internal state changes; Strategy is usually chosen by a client or configuration as an algorithm/policy.
- Mediator vs Observer: Mediator centralizes interaction logic; Observer distributes update notification through subscriptions.
- Visitor vs Iterator: Iterator traverses; Visitor performs type-specific operations during or after traversal.
- Visitor vs Strategy: Visitor adds operations across many element types; Strategy swaps one algorithm behind a stable context.
