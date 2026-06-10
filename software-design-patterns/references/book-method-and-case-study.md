# Book Method And Case Study

Use this file when an agent needs a more book-shaped design process rather than a quick pattern lookup.

## How To Read A Pattern Entry

When considering a pattern, evaluate it in this order:

1. Intent: does the pattern solve the exact design pressure?
2. Applicability: do the conditions match the current code?
3. Consequences: are the trade-offs acceptable for this codebase?
4. Participants and collaborations: what responsibilities move, and where?
5. Implementation: what language/framework constraints matter?
6. Related patterns: is there a simpler or more accurate pattern nearby?

Do not start from the structure diagram. Class diagrams can look similar while intents differ.

## Pattern Description Anatomy

The book's pattern entries repeatedly answer these questions. Agents should answer the same questions before editing:

- Pattern name: what common vocabulary does this introduce?
- Problem: what context and forces make the problem recur?
- Solution shape: what objects/classes collaborate?
- Applicability: when should this be used?
- Consequences: what improves and what gets worse?
- Implementation notes: what details commonly go wrong?
- Related patterns: what alternatives or companions exist?

For coding agents, the most important sections are applicability and consequences. They prevent pattern overuse.

## Lessons From The Document Editor Case Study

The document editor case study is useful because it starts from design problems, not pattern names. Use it as a model for choosing patterns from pressures.

### Document Structure -> Composite

Pressure: documents contain characters, images, rows, columns, and larger structures recursively. Clients should draw, format, and manipulate them without constantly checking whether an item is a leaf or a container.

Design lesson: when part-whole hierarchy is central, introduce a common component interface and let composite nodes forward work to children.

Agent use: if code has repeated `is_leaf`/`has_children` checks across a tree, consider Composite first, then Iterator or Visitor for traversal/operations.

### Formatting -> Strategy

Pressure: line-breaking and layout algorithms can change independently from document structure.

Design lesson: do not bake algorithm choice into the document object. Put the algorithm in a separate policy object.

Agent use: if a long function switches between algorithms or policies, extract a Strategy after naming the policy.

### UI Embellishment -> Decorator

Pressure: scrollbars, borders, shadows, and similar UI responsibilities combine in many ways.

Design lesson: optional stackable features should not create subclasses for every combination.

Agent use: when features can be layered around the same interface, use Decorator. When the feature is just one internal policy, use Strategy instead.

### Look-And-Feel Families -> Abstract Factory

Pressure: widgets from one look-and-feel family should be created consistently together.

Design lesson: when a whole product family varies, centralize creation behind a family factory.

Agent use: for platform/theme/vendor product families, hide concrete classes behind Abstract Factory or a simpler factory boundary.

### Window System Portability -> Bridge

Pressure: window abstractions and window-system implementations vary independently. A combined inheritance hierarchy would multiply classes.

Design lesson: split abstraction from implementation when two dimensions evolve separately.

Agent use: if class names are combining axes, such as feature + platform, consider Bridge.

### User Operations -> Command

Pressure: menu items, buttons, undo history, and macros need actions as data.

Design lesson: turn a request into an object when it must be stored, undone, composed, queued, or invoked by different UI controls.

Agent use: when action dispatch is repeated across UI/API/CLI surfaces, consider Command.

### Traversal -> Iterator

Pressure: clients need to walk document structures without knowing their representation.

Design lesson: traversal state belongs in an iterator, not in every client.

Agent use: if clients manually traverse internal collections/trees, expose an iterator or language-native iterable boundary.

### Analysis Over Structure -> Visitor

Pressure: spelling checks, hyphenation, code generation, or analysis may be performed over a stable structure.

Design lesson: when new operations are more common than new element types, put operations in visitors instead of editing every element class.

Agent use: if operations over many node types keep accumulating and the node type set is stable, consider Visitor.

## How The Case Study Guides Agents

Start from the design pressure:

- recursive structure -> Composite
- algorithm choice -> Strategy
- optional wrappers -> Decorator
- product family -> Abstract Factory
- two independent dimensions -> Bridge
- actions as objects -> Command
- traversal -> Iterator
- external operations over stable structure -> Visitor

Then apply the no-pattern gate:

- Is the current version small and local?
- Does the second real variant exist?
- Will the pattern delete branching or duplication?
- Can a simpler extraction solve the problem?

If the gate fails, do the simpler refactor.
