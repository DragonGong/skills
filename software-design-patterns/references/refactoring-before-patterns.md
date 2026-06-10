# Refactoring Before Patterns

Use this file when code is already messy. Patterns should not be layered onto unclear code. First make the current responsibilities visible.

## Refactor-First Rule

If the change touches a long function, giant file, duplicated branch, or unclear boundary, do a small behavior-preserving refactor before introducing a pattern. The goal is to expose the real variation point.

Do not use a pattern to hide disorder. Use refactoring to reveal design.

## Giant File Playbook

Symptoms:

- imports from many layers
- unrelated public functions/classes
- several independent reasons to change
- mixed UI, IO, domain rules, persistence, parsing, and formatting
- global helpers that only one feature uses

Moves:

1. Group functions/classes by responsibility and dependency direction.
2. Extract cohesive modules around domain concepts, not around pattern names.
3. Keep orchestration at the edge and domain decisions in domain modules.
4. Move vendor/platform code behind adapter/facade modules.
5. Keep construction/bootstrap code separate from behavior.

Pattern candidates after cleanup:

- Facade when the file is acting as the only tolerable entry point to a complex subsystem.
- Adapter when the file translates a vendor API into the app's domain API.
- Builder when the file mostly assembles complex object graphs.
- Strategy/State/Command when branches dominate the file.

## Long Function Playbook

Symptoms:

- multiple comments marking phases
- validation, transformation, IO, and persistence in one routine
- local variables shared across distant blocks
- deeply nested conditionals
- repeated setup/teardown around different operations

Moves:

1. Extract named phases.
2. Separate pure computation from side effects.
3. Turn large local data clusters into a small value object or context object.
4. Move decisions to the module that owns the data.
5. Add focused tests around the old behavior before changing structure when risk is high.

Pattern candidates after cleanup:

- Template Method when phases are stable and subclasses should override some steps.
- Strategy when one phase is an interchangeable algorithm.
- Command when the function performs one of many actions selected at runtime.
- Builder when the function incrementally constructs a complex result.

Avoid:

- turning every extracted phase into a class
- adding inheritance when simple functions and data flow are clearer

## Duplicated Logic Playbook

Symptoms:

- same rule copied with small edits
- same mapping table appears in multiple modules
- same construction sequence appears in tests and production code
- fixing a policy requires touching many files

Moves:

1. Extract the shared rule into the owning module.
2. Replace repeated literals with a named value or configuration object when appropriate.
3. Centralize construction behind one factory/builder only if the construction policy is non-trivial.
4. Keep call sites explicit when a shared abstraction would obscure intent.

Pattern candidates:

- Factory Method or Abstract Factory for repeated concrete construction.
- Strategy for repeated algorithm variants.
- Command for repeated action dispatch.
- Observer for repeated manual update notifications.

Avoid:

- centralizing unrelated code just because it looks similar
- creating a generic utility module with no domain owner

## If/Else And Switch Explosion Playbook

Symptoms:

- the same condition appears in several functions
- adding a type/state/action requires changing multiple switch statements
- branches mix construction, behavior, validation, and output formatting
- condition values are leaked outside their owning module

Moves:

1. Classify the condition: type, state, algorithm, command, permission, platform, or data shape.
2. Move branch-specific behavior next to the data or concept it belongs to.
3. Replace repeated conditionals with a registry, map, polymorphic object, or pattern only when variants are open-ended or cross-cutting.
4. Keep a simple conditional when it is local and stable.

Pattern candidates:

- Strategy for algorithm/policy branches.
- State for state-dependent behavior across multiple operations.
- Command for action branches and undo/queue/log needs.
- Chain of Responsibility for ordered handler checks.
- Abstract Factory/Bridge for platform or product-family branches.
- Visitor for operation branches over a stable type hierarchy.

Avoid:

- class-per-branch when two branches are enough
- dynamic registries that hide valid cases from static search

## Module Boundary Playbook

Symptoms:

- domain code imports UI, HTTP, database, filesystem, or vendor SDKs directly
- low-level modules call high-level modules
- tests require real network/storage because dependencies are concrete
- callers know object representation, storage location, or construction order

Moves:

1. Draw the desired dependency direction in words.
2. Introduce a narrow boundary interface only where a module crosses layers.
3. Put translation code in adapters.
4. Put coarse subsystem entry points in facades.
5. Put object graph creation in factories/builders/bootstrap code.

Pattern candidates:

- Adapter for external APIs.
- Facade for subsystem entry points.
- Bridge when domain abstraction and implementation platform both vary.
- Proxy for lazy, remote, protected, cached, or copy-on-write access.
- Memento when snapshots must not expose internals.

## Pre-Implementation Checklist

Before using any pattern, answer:

- What code smell exists now?
- What exact change will be easier after this?
- Which clients become simpler?
- Which module owns the new abstraction?
- What tests prove the behavior stayed the same?
- What complexity does the pattern add?

If the answers are not concrete, refactor simply and stop.
