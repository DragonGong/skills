# Introduction Deep Patterns

This file summarizes Introduction writing patterns for the 802 corpus.

## Corpus Signals

- Introductions detected: 14/14
- Introductions used for deep-pattern statistics: 10/14
- Low-confidence Introductions excluded from statistics: 4
- Median Introduction length: 1215 words
- Approximate median paragraph count: 8 paragraphs

## Common Paragraph/Move Order

| Move position | Most common function | Papers |
| --- | --- | --- |
| 1 | description | 5 |
| 2 | background | 3 |
| 3 | description | 5 |
| 4 | background | 4 |
| 5 | specific problem/gap | 2 |
| 6 | background | 5 |
| 7 | description | 4 |
| 8 | background | 3 |


## Logic Coverage

| Expected Introduction role | Detected papers | Coverage |
| --- | --- | --- |
| background | 10 | 10/10 |
| specific problem/gap | 9 | 9/10 |
| existing insufficiency | 10 | 10/10 |
| proposed method | 8 | 8/10 |
| key mechanism | 10 | 10/10 |
| contribution/significance | 4 | 4/10 |


## Stronger Introductions

| Paper | Why it is useful to learn from |
| --- | --- |
| VistaScenario Interaction Scenario Engineering for Vehicles with Intelligent Sy... | covers background, specific problem/gap, existing insufficiency, proposed method |
| Life-long Learning and Testing for Automated Vehicles via Adaptive Scenario Sam... | covers background, specific problem/gap, existing insufficiency, proposed method |
| Boosting the Training of Deep Reinforcement Learning Traffic Control by Using t... | covers background, specific problem/gap, existing insufficiency, proposed method |
| Predictive Vehicle Stability Assessment Using Lyapunov Exponent Under Extreme C... | covers background, specific problem/gap, existing insufficiency, proposed method |


## Introductions That Need Caution

| Paper | Likely weakness to avoid |
| --- | --- |
| Predictive Information Multiagent Deep Reinforcement Learning for Automated Tru... | may be truncated; missing/unclear proposed method |
| Boosting the Training of Deep Reinforcement Learning Traffic Control by Using t... | may be truncated |
| Life-long Learning and Testing for Automated Vehicles via Adaptive Scenario Sam... | may be truncated |
| Heterogeneous Driver Modeling and Corner Scenarios Sampling for Automated Vehic... | missing/unclear proposed method, contribution/significance |


## 802 Introduction Narrative Style

- Build a chain from real-world importance to a technical bottleneck.
- Classify existing methods by how they model, sample, control, perceive, or evaluate the target system.
- Critique existing methods through shared assumptions, missing variables, weak generalization, data cost, or limited evaluation, rather than by merely listing citations.
- Let the proposed method appear as the natural answer to the gap.
- Make the contribution list map back to the gap: formulation/data/scenario, method/model/control, and experimental validation.

## Paragraph-Level Template

| Unit | Writing goal | Self-check question | Common failure |
| --- | --- | --- | --- |
| Paragraph 1 | Establish why the research problem matters | Is the field context tied to the paper's task? | A generic domain opening with no task pressure. |
| Paragraph 2 | Narrow to practical challenge | Does the challenge name a concrete safety/efficiency/data/control issue? | A challenge paragraph that only says the problem is difficult. |
| Paragraph 3 | Classify existing methods and expose shared limits | Are method families compared by assumptions and failure modes? | A literature list with no synthesis. |
| Paragraph 4 | Introduce the core idea | Does the proposed method naturally answer the gap? | A sudden method claim that is not motivated by the previous gap. |
| Paragraph 5 | Summarize the framework | Can a reader see the method's modules and mechanism? | A long implementation preview without a high-level mechanism. |
| Paragraph 6 | List contributions | Does each contribution correspond to a stated gap? | Contributions that repeat features rather than advances. |


## How To Narrow From Background To Problem

1. Start with the application context and why it matters for safety, efficiency, robustness, or intelligence.
2. Identify the specific task inside that context.
3. Explain what makes the task difficult under realistic scenarios.
4. Summarize current solution families.
5. State the shared gap that remains after those solutions.
6. Introduce the proposed idea as a direct response to that gap.

## Contribution List Pattern

- Contribution 1: A formulation, dataset, scenario construction, or problem definition.
- Contribution 2: A method, model, controller, sampling strategy, or framework.
- Contribution 3: Evaluation evidence, ablation, benchmark, or real/simulation validation.
