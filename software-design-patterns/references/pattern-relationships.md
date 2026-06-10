# Pattern Relationships

Use this file after selecting a candidate pattern. It helps distinguish similar patterns, combine patterns intentionally, and review the design.

## Pattern-Level Rule

Patterns often work together, but each pattern must earn its place. Combining two patterns is justified only when there are two distinct variation points.

Bad reason: "This diagram resembles another pattern."

Good reason: "The domain has a tree structure, and operations over that tree change often, so Composite plus Visitor addresses two separate pressures."

## Creation Pattern Relationships

Factory Method is the lightest construction hook. Start here when a base workflow needs subclasses to create products.

Abstract Factory is for whole product families. Prefer it when products must be compatible as a set.

Builder is for multi-step construction. Prefer it when the construction algorithm is stable but output representation varies.

Prototype is for cloning configured examples. Prefer it when concrete product classes or configurations are runtime data.

Singleton can support factories/builders/prototype registries when a truly unique access point is required, but avoid turning it into hidden global state.

Evolution path:

- direct constructor
- centralized helper/factory function
- Factory Method when subclass hook is needed
- Abstract Factory when families matter
- Builder when assembly process matters
- Prototype when configured examples matter

## Structural Pattern Relationships

Adapter vs Bridge:

- Adapter is corrective: make an existing interface fit what clients expect.
- Bridge is architectural: split abstraction and implementation before their combinations explode.

Adapter vs Facade:

- Adapter preserves or targets an expected interface for compatibility.
- Facade invents a simpler high-level interface to a subsystem.

Facade vs Mediator:

- Facade simplifies how outside clients talk to a subsystem.
- Mediator coordinates how peer objects inside a collaboration talk to each other.

Composite vs Decorator:

- Composite is about part-whole representation.
- Decorator is about optional responsibilities.
- They can combine when tree nodes and wrappers share a component interface.

Decorator vs Proxy:

- Decorator adds behavior.
- Proxy controls access.
- If the wrapper decides whether/how to reach a real subject, think Proxy.
- If the wrapper adds responsibilities around a component, think Decorator.

Decorator vs Strategy:

- Decorator changes the object from the outside by wrapping it.
- Strategy changes one internal behavior slot by delegation.
- Use Strategy when the context has a clear algorithm/policy field.
- Use Decorator when responsibilities stack around the whole object interface.

Flyweight with Composite:

- Useful when a tree has many repeated leaves.
- Shared leaves cannot store context like parent references; pass external state explicitly.

## Behavioral Pattern Relationships

Strategy vs State:

- Strategy usually represents a chosen algorithm/policy.
- State represents the current internal mode of a context and may change as behavior runs.
- If clients pick it, Strategy is likely.
- If the object changes it internally over time, State is likely.

Strategy vs Template Method:

- Strategy uses composition and can vary at runtime.
- Template Method uses inheritance and fixes the algorithm skeleton in a base class.
- Prefer Strategy unless the codebase already uses framework-style inheritance hooks.

Command vs Strategy:

- Strategy answers "how should this operation be performed?"
- Command answers "what request should be performed, stored, invoked, undone, or queued?"

Command with Memento:

- Use Command for undoable actions.
- Use Memento when undo requires capturing originator state without exposing internals.

Chain of Responsibility vs Command:

- Chain chooses a handler by walking possible receivers.
- Command packages a request for later or decoupled execution.
- They can combine when each chain request is itself a command.

Observer vs Mediator:

- Observer distributes notification; subjects do not know concrete observers.
- Mediator centralizes coordination; colleagues talk through one protocol object.
- Observer is more reusable for simple dependencies.
- Mediator is easier to inspect when interaction rules are complex and should live in one place.

Iterator vs Visitor:

- Iterator controls traversal.
- Visitor controls what operation happens at each element.
- Use both when traversal should stay separate from the operation being applied.

Visitor vs Interpreter:

- Interpreter puts behavior on grammar/AST nodes for a language.
- Visitor is useful when many operations must be added to those nodes.

Composite With Behavioral Patterns:

- Composite + Iterator: traverse recursive structures without exposing representation.
- Composite + Visitor: add operations over a stable object tree.
- Composite + Chain of Responsibility: propagate requests along parent/child paths.
- Composite + Decorator: override or add behavior for selected subtrees.
- Composite + Builder: build complex trees step by step.
- Composite + Prototype: duplicate configured tree fragments.

## Implementation Protocol For Agents

When applying a pattern, do this in order:

1. Name the domain concept, not the pattern role.
2. Identify existing callers and keep their behavioral contract stable.
3. Create the smallest interface that callers need.
4. Move concrete knowledge behind the new boundary.
5. Delete duplicated branches/construction after the new boundary is in place.
6. Add or update tests at the behavior boundary.
7. Check whether any pattern participant is unnecessary and remove it.

## Naming Guidance

Use domain names:

- `RetryPolicy`, not `ConcreteStrategy`
- `GitHubIssueAdapter`, not `AdapterImpl`
- `CheckoutCommand`, not `Command1`
- `MarkdownDocumentBuilder`, not `ConcreteBuilder`
- `ThemeWidgetFactory`, not `AbstractFactoryFactory`

Pattern role names may appear as suffixes only when they clarify intent in the codebase.

## Review Checklist

After implementation, ask:

- Did a caller become simpler?
- Did repeated logic or branch duplication decrease?
- Is the variation point now local?
- Are concrete dependencies hidden at the right boundary?
- Is the new interface narrower than the implementation?
- Are tests focused on behavior rather than class names?
- Did the solution introduce global state, hidden lifecycle rules, or a registry that callers cannot reason about?
- Would a simpler function/module have solved the same problem?

If the last answer is yes, simplify.

## Signs Of Pattern Abuse

- more public classes but no deleted duplication
- pattern role names dominate domain names
- a registry exists only to avoid passing dependencies
- callers need to understand the whole pattern to do simple work
- one implementation exists and no realistic second implementation is visible
- tests assert class wiring instead of behavior
- debugging now requires stepping through layers that do no meaningful work

When these signs appear, remove the abstraction or collapse it to a simpler refactor.
