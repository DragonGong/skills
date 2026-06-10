# Abstract Deep Patterns

This file summarizes Abstract writing patterns from the 802 paper corpus. It uses structural signals only and avoids copying source-paper passages.

## Corpus Signals

- Abstracts detected: 14/14
- Abstracts used for deep-pattern statistics: 12/14
- Low-confidence Abstracts excluded from statistics: 2
- Median Abstract length: 190 words
- Median sentence count: 8 sentences

Low detected coverage for a role may come from rule-based detection limits, not from a recommended writing style. New Abstracts must include a contribution or implication sentence even if the automatic detector reports low contribution coverage in the corpus.

## Sentence-Level Functions

| Sentence/move position | Most common function | Papers |
| --- | --- | --- |
| 1 | background | 7 |
| 2 | existing insufficiency | 6 |
| 3 | background | 3 |
| 4 | experiment/result | 3 |
| 5 | experiment/result | 3 |
| 6 | key mechanism | 3 |
| 7 | key mechanism | 2 |


## Logic Coverage

| Expected Abstract role | Detected papers | Coverage |
| --- | --- | --- |
| background | 9 | 9/12 |
| specific problem/gap | 5 | 5/12 |
| existing insufficiency | 10 | 10/12 |
| proposed method | 6 | 6/12 |
| key mechanism | 10 | 10/12 |
| experiment/result | 10 | 10/12 |
| contribution/significance | 1 | 1/12 |


## Stronger Abstracts

| Paper | Why it is useful to learn from |
| --- | --- |
| Predictive Vehicle Stability Assessment Using Lyapunov Exponent Under Extreme C... | covers background, specific problem/gap, existing insufficiency, proposed method |
| Dynamic Testing for Autonomous Vehicles Using Random Quasi Monte Carlo | covers background, specific problem/gap, existing insufficiency, key mechanism |
| BEV-V2X Cooperative Birds-Eye-View Fusion and Grid Occupancy Prediction via V2X... | covers background, existing insufficiency, proposed method, key mechanism |
| Parallel Learning-Based Steering Control for Autonomous Driving | covers background, existing insufficiency, proposed method, key mechanism |


## Abstracts That Need Caution

| Paper | Likely weakness to avoid |
| --- | --- |
| Boosting the Training of Deep Reinforcement Learning Traffic Control by Using t... | result role unclear; may be truncated; missing/unclear specific problem/gap, proposed method, experiment/result |
| VistaScenario Interaction Scenario Engineering for Vehicles with Intelligent Sy... | result role unclear; missing/unclear specific problem/gap, experiment/result, contribution/significance |
| Analysis of cooperative driving strategies at road network level with macroscop... | method role unclear; missing/unclear background, proposed method, key mechanism |
| Life-long Learning and Testing for Automated Vehicles via Adaptive Scenario Sam... | missing/unclear background, specific problem/gap, existing insufficiency |


## 802 Abstract Writing Rules

- Start from a concrete domain/task context, not a broad slogan.
- Move quickly from background to a specific challenge or limitation.
- Name the proposed method or framework early enough that the reader sees the paper's identity.
- Explain the key mechanism in one compact move; avoid listing every module.
- Include experimental evidence when available. Numbers are best; if numbers are unavailable, state the evaluated setting and verified effect.
- End with a mandatory contribution or implication sentence that is tied to the method and evidence, not a generic claim.

## Fatal Problems

- No concrete research problem.
- No recognizable proposed method.
- No experimental result or evidence placeholder.
- Contribution or implication sentence is missing.
- Claims are invented beyond the supplied evidence.

## Major Problems

- Background is too broad or delays the task.
- Existing insufficiency is generic and does not explain the gap.
- Method description becomes a module list without a core mechanism.
- Result sentence lacks metric, setting, benchmark, or verified effect.
- Final sentence repeats the method without explaining significance.

## Minor Problems

- Sentence order is correct but transitions are stiff.
- Repeated words make the Abstract feel mechanical.
- One sentence is overloaded with too many clauses.
- Terminology is inconsistent with the rest of the manuscript.

## Executable Template

- Sentence 1: State the domain background and why the task matters.
- Sentence 2: State the concrete problem, difficulty, or existing-method limitation.
- Sentence 3: Introduce the proposed method with its name and target.
- Sentence 4: Explain the key mechanism that lets the method address the problem.
- Sentence 5: Summarize experimental setting and main result.
- Sentence 6: Close with the contribution or practical meaning.

## Common Abstract Failures To Avoid

- Opening with an empty background sentence that could fit any paper.
- Letting the problem stay broad instead of naming the actual bottleneck.
- Describing the method like a process list without a clear mechanism.
- Reporting results without numbers, benchmarks, or scenario context.
- Making the final sentence sound important without saying what changed.
