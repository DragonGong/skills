# Figure And Table Writing

## Caption Corpus Signals

- Detected figure captions: 208
- Detected table captions: 48
- Frequent figure-caption terms: vehicle (78), data (40), different (40), under (36), time (33), vehicles (30), scenario (23), method (22), comparison (20), prediction (20), model (20), network (20), state (19), samples (18)
- Frequent table-caption terms: table (48), performance (12), different (10), parameters (7), execution (7), comparison (5), model (5), vehicle (5), state (5), methods (4), various (4), under (4), lyapunov (4), exponents (4)

## Figure Writing Pattern

1. Name the visual object first: framework, scenario, architecture, trajectory, comparison, or workflow.
2. State the variable or scenario condition that changes across panels.
3. Keep interpretation in the main text; use the caption to identify what the reader is seeing.
4. In the paragraph before or after the figure, explain the question the figure answers.

## Table Writing Pattern

1. Introduce the comparison purpose before the table.
2. Define metrics and arrows or units before interpreting numbers.
3. Read the table by research question: main performance, robustness, efficiency, and ablation.
4. After the table, summarize one main result and one diagnostic observation.

## Preferred Figure/Table Roles

- Framework figure: makes the method pipeline readable before equations.
- Scenario figure: grounds testing, simulation, or corner-case claims.
- Main result table: compares against baselines on shared metrics.
- Ablation table: isolates modules or design choices.
- Visualization figure: explains why the method behaves differently, not just that it scores higher.
