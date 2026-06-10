---
name: software-design-patterns
description: Use when designing, editing, refactoring, or reviewing code that may need object-oriented design pattern guidance. Trigger especially for giant files, long functions, duplicated logic, scattered if/else or switch branches, unclear module boundaries, tight coupling, concrete class leakage, fragile construction, platform/vendor dependencies, tangled object communication, state-dependent behavior, interchangeable algorithms, tree structures, undoable actions, notifications, adapters, facades, proxies, decorators, or questions about whether to refactor before implementing.
---

# Software Design Patterns

This skill turns the design-pattern catalog into an agent workflow for preventing oversized files, long functions, duplicated logic, branch explosions, and muddy module boundaries.

## Operating Rule

Do not apply a pattern because it is famous, elegant, or available. Apply a pattern only when it isolates a real variation point, removes duplication, clarifies ownership, or reduces coupling that is already visible in the code or strongly implied by the task.

## Workflow

1. Inspect the local code before choosing a pattern.
2. Identify the change axis: creation, representation, interface, composition, access, algorithm, state, request flow, notification, traversal, snapshot, or operation set.
3. Check whether simple refactoring is enough: extract function, extract object/module, move behavior to the owner, introduce a narrow interface, or delete duplication.
4. If a pattern is justified, choose the smallest pattern that addresses the change axis.
5. Implement with domain names first and pattern role names second. `PaymentRetryPolicy` beats `ConcreteStrategy`.
6. Verify the result: callers got simpler, behavior stayed covered, the new boundary has one clear responsibility, and no speculative extension points were added.

## What To Read

- For the mental model and non-negotiable design principles, read [core-principles.md](references/core-principles.md).
- For choosing a pattern from a smell or variation point, read [selection-map.md](references/selection-map.md).
- For preventing giant files, long functions, and duplicated conditionals before adding abstractions, read [refactoring-before-patterns.md](references/refactoring-before-patterns.md).
- For the 23 pattern summaries, trade-offs, and implementation guidance, read [pattern-catalog.md](references/pattern-catalog.md).
- For how to read a pattern entry and how the document-editor case study maps design problems to patterns, read [book-method-and-case-study.md](references/book-method-and-case-study.md).
- For pattern combinations, near-miss distinctions, and final review checks, read [pattern-relationships.md](references/pattern-relationships.md).

Load only the references needed for the current task.

## Required Output When Design Is Non-Obvious

Before making substantial edits, briefly state:

- `Design pressure`: the smell or variation point found in the code.
- `Decision`: no pattern, refactor first, or the chosen pattern.
- `Reason`: why this is the smallest useful design move.

## Forbidden Behavior

- Do not use a design pattern just to use a design pattern.
- Do not create speculative abstractions for variants that do not exist.
- Do not replace a readable two-branch conditional with a class hierarchy.
- Do not grow a large file or long function when a cohesive helper, class, or module should own the behavior.
- Do not scatter the same business rule, construction rule, mapping, or type switch across files.
- Do not introduce global mutable Singleton state, service locators, or hidden registries unless the codebase already has a strong convention and the invariant is truly process-wide.
- Do not perform broad unrelated cleanup while applying a focused change.
