# Core Principles

Use these principles before reading the catalog. They are the filter that prevents pattern overuse.

## What A Pattern Is For

A design pattern is a named solution to a recurring design pressure. It is not a template to paste. A pattern is useful when it helps an agent name the moving part, assign responsibility, and keep one future change local.

A pattern should answer:

- What varies?
- Which object or module should own that variation?
- What interface should clients depend on?
- What coupling or duplication will disappear?
- What cost does the added indirection introduce?

If these answers are weak, do not use a pattern.

## Design For The Current Variation

Prefer to isolate variation that is already present or strongly implied:

- multiple concrete products or product families
- multiple algorithms, policies, commands, handlers, states, or platforms
- incompatible external APIs
- complex subsystem internals leaking to callers
- optional responsibilities that are being combined by subclassing or branching
- a stable object structure that needs many external operations

Avoid speculative design for imaginary variants. A clean extraction is usually enough until the second real implementation appears.

## Program To Interfaces At Boundaries

At module boundaries, depend on the smallest interface/protocol that clients need. Keep concrete classes inside factories, adapters, facades, repositories, or dependency injection wiring.

Use an interface when:

- callers should not know the concrete implementation
- tests need to replace a dependency cleanly
- the implementation is selected by configuration, platform, vendor, or runtime state
- multiple implementations already exist

Do not introduce an interface when there is one concrete class, no test seam needed, and no visible variation point.

## Prefer Composition For Changeable Behavior

Inheritance is useful for stable subtype relationships and shared contracts. Composition is usually better when behavior must change independently, be selected at runtime, or be combined in multiple ways.

Prefer composition/delegation when:

- subclass count is growing to cover combinations
- behavior needs runtime configuration
- parent internals would leak into subclasses
- a long method is switching on mode, type, or state

Use inheritance cautiously for Template Method, Factory Method, Interpreter nodes, or framework hooks, and only when the base contract is stable and honest.

## Encapsulate The Concept That Varies

Most patterns work by turning a variable concept into an object:

- creation knowledge becomes a factory, builder, or prototype
- an algorithm becomes a strategy
- a state becomes a state object
- a request becomes a command
- a traversal becomes an iterator
- a notification relationship becomes observer links
- a subsystem entry point becomes a facade
- an external interface mismatch becomes an adapter

When the variable concept is still unnamed, name it before coding.

## Keep Granularity Honest

Bad code often has the wrong object or module size:

- Too large: one file/class/function owns unrelated decisions.
- Too small: many tiny objects exist only to satisfy a pattern and obscure the domain.
- Wrong boundary: clients know representation, storage, platform, or construction details that belong elsewhere.

Choose granularity by responsibility, not by pattern diagram.

## Evaluate Consequences

Every pattern buys flexibility by spending something:

- more indirection
- more classes/files
- harder debugging
- more lifecycle/configuration rules
- possible runtime cost
- weaker type guarantees for dynamic dispatch schemes

Use a pattern only when the expected maintenance gain is larger than these costs.

## Agent Design Checklist

Before editing:

- Identify the current smell and the likely next change.
- Locate the owning module for the behavior.
- Decide whether a small refactor removes the smell without a pattern.
- If using a pattern, name the pattern and the reason in domain terms.

After editing:

- Check that callers depend on a narrower boundary.
- Check that duplication or branching actually decreased.
- Check that tests cover old behavior and at least one variation path.
- Check that no new global state or hidden registry appeared accidentally.
