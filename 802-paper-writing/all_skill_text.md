# All 802 Paper Writing Skill Text

This file aggregates the current text files in the `802-paper-writing` skill root. PDFs and Git metadata are excluded.


---

## .gitignore

````text
pdf/(PDF) Heterogeneous Driver Modeling and Corner Scenarios Sampling for Automated Vehicles Testing.pdf
pdf/Chang 等 - 2023 - BEV-V2X Cooperative Birds-Eye-View Fusion and Grid Occupancy Prediction via V2X-Based Data Sharing.pdf
pdf/Chang 等 - 2024 - VistaScenario Interaction Scenario Engineering for Vehicles with Intelligent Systems for Transport.pdf
pdf/Ge 等 - 2024 - Dynamic Testing for Autonomous Vehicles Using Random Quasi Monte Carlo.pdf
pdf/Ge 等 - 2024 - Life-long Learning and Testing for Automated Vehicles via Adaptive Scenario Sampling as A Continuous.pdf
pdf/Guo 等 - 2024 - Mixing Left and Right-Hand Driving Data in a Hierarchical Framework With LLM Generation.pdf
pdf/Lian 等 - 2024 - Predictive Information Multiagent Deep Reinforcement Learning for Automated Truck Platooning Control.pdf
pdf/Lian 等 - 2024 - Predictive Vehicle Stability Assessment Using Lyapunov Exponent Under Extreme Conditions.pdf
pdf/Mao 等 - 2023 - Mastering Arterial Traffic Signal Control With Multi-Agent Attention-Based Soft Actor-Critic Model.pdf
pdf/Pei 等 - 2023 - Fault-Tolerant Cooperative Driving at Signal-Free Intersections.pdf
pdf/Tian 等 - 2023 - Parallel Learning-Based Steering Control for Autonomous Driving.pdf
pdf/Wang 等 - 2025 - Boosting the Training of Deep Reinforcement Learning Traffic Control by Using the World Model.pdf
pdf/Yu 等 - 2023 - CD-DB A Data Storage Model for Cooperative Driving.pdf
pdf/Zhang 等 - 2022 - Analysis of cooperative driving strategies at road network level with macroscopic fundamental diagra.pdf

````

---

## agents/openai.yaml

````yaml
interface:
  display_name: "802 Paper Writing"
  short_description: "Write papers in 802 lab style"
  default_prompt: "Use $802-paper-writing to draft or revise a paper section in the 802 lab style."

````

---

## references/abstract_deep_patterns.md

````markdown
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

````

---

## references/advisor_strict_examples.md

````markdown
# Advisor-Strict Examples

Use these examples to understand the expected behavior of Advisor-Strict Mode. They are synthetic examples, not copied from lab papers.

## Example 1: Vague Problem And Missing Evidence

### Weak Abstract

Autonomous driving has attracted increasing attention in recent years. Existing methods still face many challenges in complex scenarios. This paper proposes a learning-based framework to improve autonomous driving performance. The method contains several modules and can handle different situations. Experiments show that the proposed method is effective.

### Problem Diagnosis

The abstract has the surface order of a paper abstract, but the logic is weak. The problem is not concrete, the gap is only described as "many challenges", the method has no recognizable mechanism, and the result sentence gives no metric, scenario, baseline, or verified effect.

### Fatal / Major / Minor Problems

- Fatal: No specific research problem or evidence-facing result.
- Major: The proposed method is not identifiable beyond "learning-based framework".
- Major: The contribution or implication sentence is missing.
- Minor: The opening phrase is generic and does not create task pressure.

### Strong Abstract

Testing autonomous vehicles in rare interactive scenarios remains difficult because naturalistic data contain few safety-critical lane-change conflicts. To address this gap, this paper proposes a scenario sampling framework that combines driver-behavior modeling with risk-guided search. The framework first estimates heterogeneous interaction patterns and then prioritizes scenario parameters likely to expose unsafe responses. Simulation experiments in lane-change scenarios show that the sampled cases produce more informative safety evaluations than frequency-based sampling. These results suggest that behavior-aware sampling can improve the efficiency of AV testing under rare but safety-critical interactions.

## Example 2: Method Without Distinct Mechanism

### Weak Abstract

Traffic signal control is important for urban transportation. Current reinforcement learning methods have limitations in large networks. We propose a new model for traffic signal control. The model uses attention and reinforcement learning to make decisions. The results prove the superiority of the proposed model.

### Problem Diagnosis

The abstract identifies the area but does not explain the bottleneck in large networks. The method has components, but no mechanism: it does not say what attention solves. The result claim is too strong because no metric, baseline, or experimental condition is supplied.

### Fatal / Major / Minor Problems

- Fatal: Result claim is unsupported and overstrong.
- Major: Large-network limitation is not specified.
- Major: Key mechanism is component-level rather than problem-facing.
- Minor: "important" and "superiority" are generic words.

### Strong Abstract

Network-level traffic signal control requires policies that coordinate spatially related intersections while remaining scalable to changing traffic demand. Existing reinforcement learning controllers often model intersections independently or rely on fixed neighborhood assumptions, which limits their ability to capture long-range congestion propagation. This paper proposes an attention-based multi-agent control model that learns adaptive dependencies among intersections before selecting phase actions. By weighting upstream and downstream traffic states according to current congestion patterns, the model links local decisions with network-level coordination. Experiments on arterial traffic networks compare the proposed controller with conventional and reinforcement-learning baselines under multiple demand settings. The results indicate that adaptive intersection attention improves coordination and provides a more interpretable basis for signal-control decisions.

## Example 3: No Contribution Or Implication Ending

### Weak Abstract

Cooperative perception is useful for intelligent vehicles. Existing perception methods are affected by occlusion and sensor limitations. This paper proposes a V2X fusion method for bird's-eye-view perception. The method fuses information from vehicles and infrastructure. Experimental results show improved perception accuracy.

### Problem Diagnosis

The abstract is mostly coherent, but the ending stops at "improved accuracy" and does not say what the improvement means. The result lacks context, and the contribution is not elevated from method description to paper-level implication.

### Fatal / Major / Minor Problems

- Major: Contribution or implication sentence is missing.
- Major: Result sentence lacks dataset, metric, baseline, or scenario context.
- Minor: The key mechanism is too compressed.

### Strong Abstract

Cooperative perception can reduce occlusion-induced uncertainty in intelligent driving, but single-vehicle BEV perception remains vulnerable when critical objects are outside the local sensing range. Existing fusion methods often depend on raw sensor sharing or tightly coupled feature exchange, which can limit interpretability and communication flexibility. This paper proposes a V2X-based BEV occupancy fusion method that exchanges structured perception representations between vehicles and infrastructure. The method aligns local occupancy estimates in a shared BEV space and updates uncertain regions using cooperative observations. Experiments under occlusion-heavy traffic scenarios compare single-vehicle perception with cooperative fusion and show improved occupancy prediction accuracy. The results indicate that representation-level V2X sharing can strengthen BEV perception while preserving a clear interface for downstream driving modules.

````

---

## references/aic_common_weaknesses.md

````markdown
# AIC Common Weaknesses

| Weakness | Problem manifestation | Why it weakens persuasion | Revision strategy | Abstract before/after example |
| --- | --- | --- | --- | --- |
| Background is too broad | The opening could fit many papers and delays the real task. | The reader cannot see why this paper is necessary. | Name the application, task, and pressure point within one or two sentences. | Before: Intelligent transportation is important. After: Safe lane-change testing requires identifying rare interactive scenarios that expose AV failure modes. |
| Challenge is not concrete | The text says the problem is difficult but does not say why. | A vague challenge cannot justify a specific method. | State the technical cause: data sparsity, interaction uncertainty, distribution shift, limited observability, or optimization cost. | Before: Existing methods face many challenges. After: Existing sampling methods often miss low-probability but high-risk interactions. |
| Proposed method appears too late | Long background and literature delay the paper identity. | The reader may lose the thread before seeing the solution. | Introduce the core idea immediately after the gap, then expand details later. | Before: Several paragraphs of related work before the method. After: Gap paragraph followed by a concise method sentence. |
| Contribution list does not match the gap | Contributions list features without showing why they solve the stated problem. | The argument feels assembled rather than inevitable. | Map each contribution to one limitation or missing capability. | Before: We design a framework and conduct experiments. After: We formulate the scenario gap, design an adaptive sampler for it, and validate coverage gains. |
| Conclusion repeats the Abstract | It restates method and results without synthesis. | The ending misses the chance to explain what the evidence means. | Add a problem-facing takeaway and restrained implication. | Before: This paper proposed X and experiments show it works. After: The results indicate that X improves evaluation coverage under interactive corner cases. |
| Experimental results are disconnected | Numbers or comparisons are mentioned without linking to the research question. | Evidence does not strengthen the paper's central claim. | Interpret each result through the mechanism or gap. | Before: The method improves accuracy. After: The gain suggests that cooperative BEV information reduces occlusion-induced prediction errors. |
| Future work is too template-like | The final sentence says future work will improve or extend the method with no direction. | It sounds perfunctory and weakens the ending. | Name one restrained limitation and one concrete next direction. | Before: Future work will improve the method. After: Future work will test the framework under denser mixed-traffic scenarios. |

````

---

## references/aic_per_paper_inventory.md

````markdown
# AIC Per-Paper Inventory

This inventory records Abstract, Introduction, and Conclusion extraction status for each PDF. Low-confidence sections remain here for audit but are excluded from deep-pattern statistics.

| File | Abstract | Introduction | Conclusion | extraction_method | confidence | warning_reason | Abstract length | Introduction length | Conclusion length | AIC point to learn | AIC point to avoid |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| (PDF) Heterogeneous Driver Modeling and Corner Scenarios Sampling for Automated Vehicles Testing.pdf | Yes; check too short (<80 words); result role unclear | Yes | Yes | Abstract=front-matter fallback; Introduction=heading; Conclusion=heading | Abstract=low; Introduction=high; Conclusion=high | Abstract=too short (<80 words); result role unclear; Introduction=none; Conclusion=none | 7 sentences / 31 words | 2 approx paragraphs / 513 words | 2 approx paragraphs / 414 words | Introduction builds a usable route from task background to method motivation. | Abstract is low confidence: too short (<80 words); result role unclear. |
| Chang 等 - 2023 - BEV-V2X Cooperative Birds-Eye-View Fusion and Grid Occupancy Prediction via V2X-Based Data Sharing.pdf | Yes | Yes | Yes | Abstract=heading; Introduction=heading; Conclusion=heading | Abstract=high; Introduction=high; Conclusion=high | Abstract=none; Introduction=none; Conclusion=none | 11 sentences / 219 words | 10 approx paragraphs / 1234 words | 4 approx paragraphs / 550 words | Abstract provides a compact problem-method-evidence chain. | Avoid copying surface phrases; learn the structure rather than the wording. |
| Chang 等 - 2024 - VistaScenario Interaction Scenario Engineering for Vehicles with Intelligent Systems for Transport.pdf | Yes; check result role unclear | Yes | No | Abstract=heading; Introduction=heading; Conclusion=not detected | Abstract=medium; Introduction=high; Conclusion=low | Abstract=result role unclear; Introduction=none; Conclusion=not detected | 9 sentences / 189 words | 5 approx paragraphs / 1618 words | not detected | Abstract provides a compact problem-method-evidence chain. | Abstract needs caution: result role unclear. |
| Ge 等 - 2024 - Dynamic Testing for Autonomous Vehicles Using Random Quasi Monte Carlo.pdf | Yes | Yes | Yes | Abstract=heading; Introduction=heading; Conclusion=heading | Abstract=high; Introduction=high; Conclusion=high | Abstract=none; Introduction=none; Conclusion=none | 10 sentences / 253 words | 8 approx paragraphs / 969 words | 1 approx paragraphs / 191 words | Abstract provides a compact problem-method-evidence chain. | Avoid copying surface phrases; learn the structure rather than the wording. |
| Ge 等 - 2024 - Life-long Learning and Testing for Automated Vehicles via Adaptive Scenario Sampling as A Continuous.pdf | Yes | Yes; check may be truncated | Yes | Abstract=heading; Introduction=heading; Conclusion=heading | Abstract=high; Introduction=medium; Conclusion=high | Abstract=none; Introduction=may be truncated; Conclusion=none | 10 sentences / 221 words | 12 approx paragraphs / 1559 words | 2 approx paragraphs / 249 words | Introduction builds a usable route from task background to method motivation. | Introduction needs caution: may be truncated. |
| Guo 等 - 2024 - Mixing Left and Right-Hand Driving Data in a Hierarchical Framework With LLM Generation.pdf | Yes | Yes | Yes | Abstract=heading; Introduction=heading; Conclusion=heading | Abstract=high; Introduction=high; Conclusion=high | Abstract=none; Introduction=none; Conclusion=none | 5 sentences / 109 words | 9 approx paragraphs / 928 words | 1 approx paragraphs / 190 words | Abstract provides a compact problem-method-evidence chain. | Avoid copying surface phrases; learn the structure rather than the wording. |
| Lian 等 - 2024 - Predictive Information Multiagent Deep Reinforcement Learning for Automated Truck Platooning Control.pdf | Yes; check too short (<80 words); method role unclear; result role unclear | Yes; check may be truncated | Yes | Abstract=front-matter fallback; Introduction=heading; Conclusion=heading | Abstract=low; Introduction=medium; Conclusion=high | Abstract=too short (<80 words); method role unclear; result role unclear; may be truncated; Introduction=may be truncated; Conclusion=none | 5 sentences / 67 words | 4 approx paragraphs / 4083 words | 2 approx paragraphs / 337 words | Introduction builds a usable route from task background to method motivation. | Abstract is low confidence: too short (<80 words); method role unclear; result role unclear; may be truncated. |
| Lian 等 - 2024 - Predictive Vehicle Stability Assessment Using Lyapunov Exponent Under Extreme Conditions.pdf | Yes | Yes | Yes | Abstract=heading; Introduction=heading; Conclusion=heading | Abstract=high; Introduction=high; Conclusion=high | Abstract=none; Introduction=none; Conclusion=none | 11 sentences / 261 words | 15 approx paragraphs / 2300 words | 2 approx paragraphs / 367 words | Abstract provides a compact problem-method-evidence chain. | Avoid copying surface phrases; learn the structure rather than the wording. |
| Mao 等 - 2023 - Mastering Arterial Traffic Signal Control With Multi-Agent Attention-Based Soft Actor-Critic Model.pdf | Yes | Yes; check too long (>4500 words); possible section leakage; may be truncated | Yes | Abstract=heading; Introduction=heading; Conclusion=heading | Abstract=high; Introduction=low; Conclusion=high | Abstract=none; Introduction=too long (>4500 words); possible section leakage; may be truncated; Conclusion=none | 8 sentences / 152 words | 32 approx paragraphs / 4808 words | 4 approx paragraphs / 635 words | Abstract provides a compact problem-method-evidence chain. | Introduction is low confidence: too long (>4500 words); possible section leakage; may be truncated. |
| Pei 等 - 2023 - Fault-Tolerant Cooperative Driving at Signal-Free Intersections.pdf | Yes | Yes; check too long (>4500 words); possible section leakage | Yes; check too long (>900 words); may be truncated | Abstract=heading; Introduction=heading; Conclusion=heading | Abstract=high; Introduction=low; Conclusion=low | Abstract=none; Introduction=too long (>4500 words); possible section leakage; Conclusion=too long (>900 words); may be truncated | 6 sentences / 154 words | 38 approx paragraphs / 6328 words | 8 approx paragraphs / 1158 words | Abstract provides a compact problem-method-evidence chain. | Introduction is low confidence: too long (>4500 words); possible section leakage. |
| Tian 等 - 2023 - Parallel Learning-Based Steering Control for Autonomous Driving.pdf | Yes | Yes | Yes; check evidence summary not obvious | Abstract=heading; Introduction=heading; Conclusion=heading | Abstract=high; Introduction=high; Conclusion=medium | Abstract=none; Introduction=none; Conclusion=evidence summary not obvious | 12 sentences / 197 words | 10 approx paragraphs / 1197 words | 1 approx paragraphs / 152 words | Abstract provides a compact problem-method-evidence chain. | Conclusion needs caution: evidence summary not obvious. |
| Wang 等 - 2025 - Boosting the Training of Deep Reinforcement Learning Traffic Control by Using the World Model.pdf | Yes; check result role unclear; may be truncated | Yes; check may be truncated | Yes | Abstract=front-matter fallback; Introduction=heading; Conclusion=heading | Abstract=medium; Introduction=medium; Conclusion=high | Abstract=result role unclear; may be truncated; Introduction=may be truncated; Conclusion=none | 8 sentences / 123 words | 6 approx paragraphs / 822 words | 2 approx paragraphs / 161 words | Introduction builds a usable route from task background to method motivation. | Abstract needs caution: result role unclear. |
| Yu 等 - 2023 - CD-DB A Data Storage Model for Cooperative Driving.pdf | Yes | Yes; check too long (>4500 words); possible section leakage | Yes | Abstract=heading; Introduction=heading; Conclusion=heading | Abstract=high; Introduction=low; Conclusion=high | Abstract=none; Introduction=too long (>4500 words); possible section leakage; Conclusion=none | 5 sentences / 120 words | 47 approx paragraphs / 6666 words | 3 approx paragraphs / 352 words | Conclusion reconnects method and evidence to the research problem. | Introduction is low confidence: too long (>4500 words); possible section leakage. |
| Zhang 等 - 2022 - Analysis of cooperative driving strategies at road network level with macroscopic fundamental diagra.pdf | Yes; check method role unclear | Yes; check too long (>4500 words); possible section leakage | Yes | Abstract=heading; Introduction=heading; Conclusion=heading | Abstract=medium; Introduction=low; Conclusion=high | Abstract=method role unclear; Introduction=too long (>4500 words); possible section leakage; Conclusion=none | 6 sentences / 191 words | 3 approx paragraphs / 9330 words | 6 approx paragraphs / 796 words | Abstract provides a compact problem-method-evidence chain. | Abstract needs caution: method role unclear. |


## Extraction Notes

_No PDF-level extraction errors were detected._


````

---

## references/aic_revision_checklist.md

````markdown
# AIC Revision Checklist

Use this checklist before showing Abstract, Introduction, or Conclusion drafts to an advisor.

## Abstract

### Fatal Problems: Must Rewrite

- Missing a concrete research problem.
- Missing the proposed method or making it unrecognizable.
- Missing experimental evidence, evaluation setting, or an explicit evidence placeholder.
- Missing a contribution or implication sentence.
- Inventing results, numbers, novelty, or significance beyond the user's information.

### Major Problems: Structural Revision Needed

- The logic chain is incomplete: background -> problem -> insufficiency -> method -> mechanism -> evidence -> implication.
- The problem is too generic to justify the method.
- The gap is a slogan such as "existing methods are limited" without a cause.
- The method sentence lists components but not the core mechanism.
- The result sentence does not mention metric, benchmark, scenario, or verified effect.

### Minor Problems: Language Polishing

- Sentence order is good but transitions are stiff.
- Repetition weakens fluency.
- A sentence is too long or overloaded.
- Chinese-English literal phrasing or redundant academic wording remains.
- Terminology is inconsistent across sentences.

## Introduction

### Fatal Problems: Must Rewrite

- No clear research question or task emerges.
- The gap is missing before the proposed method appears.
- Existing work is only listed, with no synthesis or shared limitation.
- The proposed method does not answer the stated gap.
- The contribution list is absent or disconnected from the paper's claims.

### Major Problems: Structural Revision Needed

- The first paragraph is too broad and not task-facing.
- The challenge is not concrete enough.
- Existing methods are not grouped by family, assumption, or limitation.
- The method appears too suddenly or too late.
- Contributions describe features rather than advances.
- Claims are stronger than the experiments can support.

### Minor Problems: Language Polishing

- Topic sentences are functional but not sharp.
- Transitions between paragraphs are decorative rather than logical.
- Citation-group sentences are repetitive.
- Some sentences sound academic but carry little information.
- Terminology and abbreviations need harmonization.

## Conclusion

### Fatal Problems: Must Rewrite

- The Conclusion is only a compressed Abstract.
- It does not return to the research problem.
- It lacks evidence-facing synthesis of the main findings.
- It introduces unsupported new claims.
- It ends with generic future work instead of a takeaway.

### Major Problems: Structural Revision Needed

- Method summary is too procedural and does not state the contribution.
- Experimental evidence is mentioned but not interpreted.
- Practical or scientific meaning is vague or exaggerated.
- Limitation/future-work wording is too broad.
- The final sentence does not leave a clear contribution.

### Minor Problems: Language Polishing

- Repeated wording from the Abstract or Introduction remains.
- Evidence and meaning are connected by weak transitions.
- The conclusion is correct but stylistically flat.
- Future work is reasonable but phrased mechanically.
- Sentence length or rhythm needs smoothing.

````

---

## references/aic_style_guide.md

````markdown
# AIC Style Guide

This guide combines Abstract, Introduction, and Conclusion patterns from the 802 paper corpus.

## Corpus Coverage

- Abstract detected: 14/14
- Introduction detected: 14/14
- Conclusion detected: 13/14
- Abstract used for deep statistics: 12/14
- Introduction used for deep statistics: 10/14
- Conclusion used for deep statistics: 12/14

Low-confidence sections are retained only in `aic_per_paper_inventory.md`; they are excluded from deep-pattern statistics.

## Stable 802 Style

- The writing is engineering-evidence oriented: it values concrete tasks, mechanisms, experiments, and scenario-level validation.
- The central chain is problem -> gap -> method -> evidence -> meaning.
- The tone is assertive about what was built, but restrained about generality unless backed by experiments.
- Contributions are usually described through a concrete artifact: model, framework, control strategy, sampling method, scenario system, dataset, or evaluation pipeline.
- Experimental results are strongest when tied to baselines, scenarios, metrics, and ablations.

## How AIC Sections Work Together

- Abstract compresses the full chain into 5-7 functional moves.
- Introduction expands the chain and makes the gap unavoidable.
- Conclusion closes the chain by returning to the problem and explaining what the evidence now supports.

## Contribution Description Rules

- Name the contribution as a technical object or finding.
- State what gap it addresses.
- Explain how it was validated.
- Avoid "first", "novel", "significant", and "effective" unless the evidence is explicit.

## Result Description Rules

- Prefer measured improvements, scenario coverage, robustness, efficiency, stability, accuracy, or safety-related outcomes.
- If exact numbers are unavailable, mention the benchmark, simulator, dataset, or scenario type.
- Tie each result back to the research problem instead of treating it as isolated performance.

## Imitation Without Copying

- Imitate organization, not sentences.
- Reuse rhetorical roles: background, gap, method, mechanism, evidence, meaning.
- Replace generic paper-style phrases with task-specific claims.
- Use short phrase templates only as scaffolds, then rewrite with the user's actual technical content.

````

---

## references/checklist.md

````markdown
# Writing Checklist

Use this before returning any draft or revision produced with the 802-paper-writing skill.

## Scope

- Identify the requested section: abstract, introduction, related work, method, experiments, conclusion, highlights, cover letter, or reviewer response.
- Read `references/lab_style_guide.md` first.
- Read the most relevant section reference before drafting.

## Style And Originality

- Do not copy source-paper sentences.
- Follow the lab's organization patterns, argument order, and technical tone.
- Make each novelty claim specific to the user's actual method and evidence.
- Avoid unsupported superlatives such as "first", "best", or "significant" unless evidence is supplied.
- Keep claims proportional to the provided experiments.

## Section-Specific Checks

- Abstract follows background -> problem -> gap -> method -> result -> contribution.
- Introduction follows field background -> existing-method limitations -> core idea -> contribution list.
- Method follows problem definition -> overall framework -> module details -> objective/training -> implementation or complexity details.
- Experiments follow settings -> metrics -> baselines -> main results -> ablation -> visualization -> discussion.
- Reviewer response is polite, specific, acknowledges reasonable concerns, and states exact manuscript changes or planned locations.

## Output Quality

- Preserve technical terms, variables, dataset names, and metric names supplied by the user.
- Flag missing evidence instead of inventing results.
- For revisions, keep the user's intended meaning unless explicitly asked to rewrite freely.
- For reviewer responses, separate response text from manuscript-change text when helpful.

````

---

## references/conclusion_deep_patterns.md

````markdown
# Conclusion Deep Patterns

This file summarizes Conclusion writing patterns for the 802 corpus.

## Corpus Signals

- Conclusions detected: 13/14
- Conclusions used for deep-pattern statistics: 12/14
- Low-confidence Conclusions excluded from statistics: 1
- Median Conclusion length: 344 words
- Approximate median paragraph count: 2 paragraphs

The Conclusion must not be a compressed Abstract. It should add evidence-facing synthesis: what the experiments or analysis now support about the original research problem.

## Common Sentence/Move Order

| Move position | Most common function | Papers |
| --- | --- | --- |
| 1 | proposed method | 9 |
| 2 | experiment/result | 7 |
| 3 | key mechanism | 4 |
| 4 | description | 4 |
| 5 | key mechanism | 4 |
| 6 | key mechanism | 3 |
| 7 | background | 3 |


## Logic Coverage

| Expected Conclusion role | Detected papers | Coverage |
| --- | --- | --- |
| specific problem/gap | 3 | 3/12 |
| proposed method | 9 | 9/12 |
| key mechanism | 11 | 11/12 |
| experiment/result | 11 | 11/12 |
| contribution/significance | 2 | 2/12 |


## Stronger Conclusions

| Paper | Why it is useful to learn from |
| --- | --- |
| Analysis of cooperative driving strategies at road network level with macroscop... | covers specific problem/gap, key mechanism, experiment/result, contribution/significance |
| Mastering Arterial Traffic Signal Control With Multi-Agent Attention-Based Soft... | covers proposed method, key mechanism, experiment/result, contribution/significance |
| CD-DB A Data Storage Model for Cooperative Driving | covers specific problem/gap, proposed method, key mechanism, experiment/result |
| Predictive Vehicle Stability Assessment Using Lyapunov Exponent Under Extreme C... | covers proposed method, key mechanism, experiment/result |


## Conclusions That Need Caution

| Paper | Likely weakness to avoid |
| --- | --- |
| Parallel Learning-Based Steering Control for Autonomous Driving | evidence summary not obvious; missing/unclear specific problem/gap, experiment/result, contribution/significance |
| Heterogeneous Driver Modeling and Corner Scenarios Sampling for Automated Vehic... | missing/unclear specific problem/gap, key mechanism, contribution/significance |
| BEV-V2X Cooperative Birds-Eye-View Fusion and Grid Occupancy Prediction via V2X... | missing/unclear specific problem/gap, proposed method, contribution/significance |
| Boosting the Training of Deep Reinforcement Learning Traffic Control by Using t... | missing/unclear specific problem/gap, contribution/significance |


## 802 Conclusion Style

- Return to the research problem with a narrower angle than the Introduction.
- Summarize the proposed method as a contribution, not as a procedural replay.
- State the strongest experimental finding and connect it to the original challenge.
- Provide evidence-facing synthesis: interpret what the evidence proves, limits, or suggests.
- Explain practical or scientific meaning without overselling.
- Mention limitations or future work only after the achieved contribution is clear.

## Fatal Problems

- Conclusion only repeats the Abstract.
- No evidence-facing synthesis of experimental findings.
- No return to the research problem.
- New claims appear that were not supported earlier.
- Limitations or future work replace the main takeaway.

## Major Problems

- Method summary is too procedural and does not state the contribution.
- Evidence is mentioned but not interpreted.
- Practical meaning is vague or exaggerated.
- Final sentence is a generic future-work template.
- The paragraph order hides the main takeaway.

## Minor Problems

- Ending is clear but stylistically flat.
- Repeated phrases make the conclusion sound copied from earlier sections.
- Limitation wording is too cautious or too broad.
- Transitions between evidence and meaning are abrupt.

## Strong Vs. Weak Conclusion

- Strong: problem recap -> method contribution -> evidence -> meaning -> restrained limitation/future direction.
- Weak: a compressed Abstract with no new synthesis, no evidence recap, and a generic future-work sentence.

## Executable Template

- Sentence 1: Return to the research problem.
- Sentence 2: Summarize the proposed method or framework.
- Sentence 3: Summarize the key experimental finding.
- Sentence 4: State why the finding matters for the task or application.
- Sentence 5: Add limitation or future work in restrained language when appropriate.

````

---

## references/experiment_writing.md

````markdown
# Experiment Writing

## Corpus Signals

- Papers with detected experiment/evaluation sections: 7
- Median extracted experiment-section length: 1363 words
- Frequent experiment-analysis cues: improve (124), comparison (120), achieve (98), reduce (50), results show (22), compared with (21), outperform (18), results demonstrate (8), ablation (6)

| Common experiment move sequence | Papers |
| --- | --- |
| description -> field background -> description -> field background -> description -> experiment setup -> paper aim -> problem or limitation | 1 |
| description -> framework overview -> description -> field background -> framework overview -> description -> ablation or sensitivity -> description | 1 |
| experiment setup -> description -> field background -> description -> field background | 1 |
| description -> field background -> result analysis -> description -> paper aim -> description -> field background -> paper aim | 1 |
| description -> problem or limitation -> framework overview -> technical detail -> framework overview -> technical detail -> framework overview -> technical detail | 1 |
| description -> field background -> contribution list -> field background -> experiment setup -> description -> ablation or sensitivity -> field background | 1 |
| field background -> problem or limitation -> field background -> technical detail -> description -> field background -> description -> result analysis | 1 |


## Default Experiment Section Order

1. Settings: dataset, simulator, scenario source, split, hardware, or training details.
2. Metrics: define what each metric measures and why it matters.
3. Baselines: group baselines by family and state fairness conditions.
4. Main results: make one table or figure carry the central claim.
5. Ablation: isolate modules, losses, data choices, or sampling strategies.
6. Visualization/case study: show behavior in concrete scenarios.
7. Discussion: explain failure cases, robustness, efficiency, or limitations.

## Analysis Style

- Interpret numbers through mechanism, not only rank.
- State whether gains are consistent, scenario-specific, or metric-specific.
- Link ablation changes back to modules described in the method.
- Use cautious language for small or mixed gains.
- Mention practical significance when the metric maps to safety, stability, efficiency, or data cost.

````

---

## references/figure_table_writing.md

````markdown
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

````

---

## references/introduction_deep_patterns.md

````markdown
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

````

---

## references/lab_style_guide.md

````markdown
# 802 Lab Paper Style Guide

Generated from the local PDF corpus in `C:\Users\dragongong\.cc-switch\skills\802-paper-writing\pdf`.

## Corpus Summary

- Successfully analyzed PDFs: 14
- Skipped PDFs: 0
- Average extracted paper length: 9562 words
- Median extracted sentence count: 380
- Dominant technical vocabulary: vehicle, vehicles, ieee, data, control, driving, model, scenario, traffic, time, intelligent, network, scenarios, samples, testing, tsinghua, cooperative, traf

| Paper | Words | Figures | Tables | Detected sections |
| --- | --- | --- | --- | --- |
| Heterogeneous Driver Modeling and Corner Scenarios Sampling for Automated Vehicles Testing | 6731 | 14 | 1 | Introduction, Related Work, Method, Experiments, Conclusion |
| BEV-V2X Cooperative Birds-Eye-View Fusion and Grid Occupancy Prediction via V2X-Based Data Sharing | 12790 | 15 | 4 | Abstract, Introduction, Related Work, Experiments, Conclusion |
| VistaScenario Interaction Scenario Engineering for Vehicles with Intelligent Systems for Transport | 14454 | 12 | 1 | Abstract, Introduction, Related Work, Method |
| Dynamic Testing for Autonomous Vehicles Using Random Quasi Monte Carlo | 9939 | 12 | 2 | Abstract, Introduction, Related Work, Method, Experiments, Conclusion |
| Life-long Learning and Testing for Automated Vehicles via Adaptive Scenario Sampling as A Continuous | 9486 | 14 | 3 | Abstract, Introduction, Related Work, Experiments, Conclusion |
| Mixing Left and Right-Hand Driving Data in a Hierarchical Framework With LLM Generation | 6808 | 7 | 5 | Abstract, Introduction, Method, Experiments, Conclusion |
| Predictive Information Multiagent Deep Reinforcement Learning for Automated Truck Platooning Control | 9976 | 17 | 6 | Introduction, Method, Conclusion |
| Predictive Vehicle Stability Assessment Using Lyapunov Exponent Under Extreme Conditions | 8100 | 25 | 8 | Abstract, Introduction, Method, Conclusion |
| Mastering Arterial Traffic Signal Control With Multi-Agent Attention-Based Soft Actor-Critic Model | 9049 | 15 | 9 | Abstract, Introduction, Method |
| Fault-Tolerant Cooperative Driving at Signal-Free Intersections | 11671 | 18 | 1 | Abstract, Introduction, Experiments, Conclusion |
| Parallel Learning-Based Steering Control for Autonomous Driving | 7531 | 18 | 1 | Abstract, Introduction, Related Work, Conclusion |
| Boosting the Training of Deep Reinforcement Learning Traffic Control by Using the World Model | 6245 | 4 | 3 | Introduction, Related Work, Experiments, Conclusion |
| CD-DB A Data Storage Model for Cooperative Driving | 8320 | 16 | 1 | Abstract, Introduction, Conclusion |
| Analysis of cooperative driving strategies at road network level with macroscopic fundamental diagra | 12771 | 21 | 3 | Abstract, Introduction, Conclusion |


## Extraction Log

_No PDFs were skipped._


## Core Style Conclusions

1. The corpus is application-driven and systems-oriented: papers usually start from autonomous driving, traffic control, cooperative driving, scenario engineering, or vehicle stability problems before narrowing to a concrete modeling or testing gap.
2. The preferred argument shape is problem-first: establish a safety, efficiency, generalization, data, or robustness issue; explain why existing methods are insufficient; then introduce a named framework, model, sampling strategy, or control method.
3. Method writing tends to combine formal problem definition with an engineering pipeline. The common rhythm is definition, framework overview, module mechanism, objective or algorithm, then implementation detail.
4. Experimental writing is comparative and diagnostic. Strong sections connect simulation or dataset settings, baselines, metrics, main comparisons, ablations or sensitivity checks, and scenario/case visualization.
5. The tone is technical, direct, and evidence-led. Active claims such as "we propose/design/develop" are common for contributions, while result claims are usually tied to measured improvements, robustness, or scenario-level behavior.
6. Figures and tables are used as argument anchors: framework diagrams, scenario illustrations, comparative result tables, and ablation summaries often carry the main evidence chain.

## Frequent Cues

- Transition cues: however (125), therefore (109), in addition (58), finally (35), instead (23), furthermore (22), meanwhile (21), moreover (16), specifically (11), as a result (9), nevertheless (4), to this end (4)
- Contribution cues: we propose (24), we design (19), explicit contribution list (9), we present (6), we construct (5), we introduce (5), we formulate (5), we develop (4), we build (1)
- Problem cues: limited (189), current (153), however (125), challenge (29), existing (27), remain (23), lack (21), limitation (15), difficult (13), ignore (7)
- Experiment-analysis cues: improve (124), comparison (120), achieve (98), reduce (50), results show (22), compared with (21), outperform (18), results demonstrate (8), ablation (6)

## Section Coverage

| Section | Detected papers |
| --- | --- |
| Introduction | 14 |
| Conclusion | 12 |
| Abstract | 11 |
| Related Work | 7 |
| Method | 7 |
| Experiments | 7 |


````

---

## references/phrase_patterns.md

````markdown
# Phrase Patterns

These are short generalized templates and cue inventories. Do not copy sentences from the source PDFs.

## Transition Cues

- Most frequent cues: however (125), therefore (109), in addition (58), finally (35), instead (23), furthermore (22), meanwhile (21), moreover (16), specifically (11), as a result (9), nevertheless (4), to this end (4), consequently (3), in particular (3)
- Use contrast cues to pivot from prior work to the target gap.
- Use additive cues to introduce modules, experimental settings, or additional evidence.
- Use causal cues only when the causal relation is explicit in the method or result.

## Problem Statement Templates

- "However, existing [methods/systems] often struggle with [specific condition]."
- "[Task] remains challenging because [technical cause] and [practical constraint] interact."
- "Although [prior direction] improves [aspect], it usually overlooks [missing factor]."
- "A key obstacle is to [goal] while maintaining [constraint]."

Observed problem cues: limited (189), current (153), however (125), challenge (29), existing (27), remain (23), lack (21), limitation (15), difficult (13), ignore (7)

## Contribution Templates

- "We propose [method name], a [framework/model/strategy] for [task]."
- "The main contributions are threefold: [formulation], [method], and [validation]."
- "To address [gap], we design [module] that [mechanism]."
- "We further develop [training/testing component] to improve [property]."

Observed contribution cues: we propose (24), we design (19), explicit contribution list (9), we present (6), we construct (5), we introduce (5), we formulate (5), we develop (4), we build (1)

## Experiment Analysis Templates

- "The results show that [method] consistently improves [metric] under [scenario]."
- "Compared with [baseline family], [method] achieves better [performance] because [mechanism]."
- "The ablation study verifies that [module] contributes most to [effect]."
- "The visualization indicates that [behavior] is aligned with [intended mechanism]."

Observed experiment cues: improve (124), comparison (120), achieve (98), reduce (50), results show (22), compared with (21), outperform (18), results demonstrate (8), ablation (6)

## Tone Rules

- Prefer precise verbs: formulate, design, sample, control, predict, evaluate, validate.
- Use cautious claims when evidence is indirect: suggest, indicate, imply.
- Use strong claims only when backed by a table, figure, statistical result, or ablation.
- Keep novelty claims tied to the actual technical difference.

````

---

## references/section_patterns.md

````markdown
# Section Patterns

Use these patterns as organization guidance. They are abstractions from the corpus, not source-paper text.

## Abstract

- Papers with detected section: 11
- Median extracted length: 191 words

| Common move sequence | Papers |
| --- | --- |
| field background -> problem or limitation -> field background | 2 |
| description -> field background -> description -> method claim -> field background -> result analysis -> description -> field background | 1 |
| field background -> paper aim -> field background -> experiment setup -> description -> framework overview -> experiment setup | 1 |
| field background -> description -> problem or limitation -> description -> technical detail -> contribution list -> result analysis -> description | 1 |
| description -> problem or limitation -> method claim -> description -> result analysis | 1 |


| Move position | Most common move | Papers |
| --- | --- | --- |
| 1 | field background | 8 |
| 2 | problem or limitation | 6 |
| 3 | field background | 5 |
| 4 | description | 2 |
| 5 | result analysis | 2 |
| 6 | result analysis | 1 |

- Prefer the order: background -> problem -> gap -> method -> result -> contribution.
- Keep the method name and target task visible before the result claim.
- Use one compact result sentence; avoid listing every metric unless the number is central.

## Introduction

- Papers with detected section: 14
- Median extracted length: 1588 words

| Common move sequence | Papers |
| --- | --- |
| experiment setup -> problem or limitation -> description -> problem or limitation -> description -> field background -> problem or limitation -> experiment setup | 1 |
| field background -> description -> result analysis -> field background -> technical detail -> description -> technical detail -> experiment setup | 1 |
| field background -> description -> field background -> description -> field background -> experiment setup -> field background -> technical detail | 1 |
| field background -> description -> problem or limitation -> experiment setup -> problem or limitation -> description -> problem or limitation -> description | 1 |
| description -> field background -> result analysis -> problem or limitation -> description -> result analysis -> field background -> experiment setup | 1 |


| Move position | Most common move | Papers |
| --- | --- | --- |
| 1 | field background | 8 |
| 2 | description | 5 |
| 3 | result analysis | 4 |
| 4 | description | 5 |
| 5 | field background | 5 |
| 6 | description | 4 |

- Prefer the order: field background -> limitations of existing work -> core idea -> contribution list.
- End with concrete contributions rather than a generic paper-organization paragraph.
- Move from real-world safety/efficiency need to technical gap before introducing the method.

## Related Work

- Papers with detected section: 7
- Median extracted length: 2406 words

| Common move sequence | Papers |
| --- | --- |
| description -> field background -> result analysis -> description -> field background -> description -> field background -> description | 1 |
| field background -> framework overview -> description -> field background -> description -> visualization or case -> field background -> technical detail | 1 |
| field background -> description -> field background -> visualization or case -> field background -> problem or limitation -> field background -> description | 1 |
| description -> experiment setup -> description -> experiment setup -> field background -> experiment setup -> description -> experiment setup | 1 |
| experiment setup -> description -> experiment setup -> description -> field background -> paper aim -> description -> method claim | 1 |


| Move position | Most common move | Papers |
| --- | --- | --- |
| 1 | field background | 4 |
| 2 | description | 2 |
| 3 | description | 3 |
| 4 | description | 2 |
| 5 | field background | 5 |
| 6 | description | 2 |

- Group prior work by methodological family or application setting, not by author chronology.
- End each group with a short limitation that motivates the current paper.
- Keep comparisons fair and specific; avoid dismissive language.

## Method

- Papers with detected section: 7
- Median extracted length: 3636 words

| Common move sequence | Papers |
| --- | --- |
| visualization or case -> experiment setup -> description -> experiment setup -> description -> problem or limitation -> experiment setup -> description | 1 |
| technical detail -> problem or limitation -> field background -> experiment setup -> field background -> problem or limitation -> description -> research gap | 1 |
| field background -> description -> framework overview -> problem or limitation -> result analysis -> description -> technical detail -> description | 1 |
| framework overview -> technical detail -> experiment setup -> visualization or case -> technical detail -> visualization or case -> problem or limitation -> framework overview | 1 |
| technical detail -> description -> problem or limitation -> description -> field background -> technical detail -> description -> framework overview | 1 |


| Move position | Most common move | Papers |
| --- | --- | --- |
| 1 | technical detail | 2 |
| 2 | description | 2 |
| 3 | field background | 2 |
| 4 | experiment setup | 2 |
| 5 | field background | 2 |
| 6 | problem or limitation | 2 |

- Prefer the order: problem definition -> overall framework -> module details -> training or optimization objective -> implementation or complexity notes.
- Introduce notation only when it is reused in equations, algorithms, or experiments.
- Tie each module back to the gap identified in the introduction.

## Experiments

- Papers with detected section: 7
- Median extracted length: 1363 words

| Common move sequence | Papers |
| --- | --- |
| description -> field background -> description -> field background -> description -> experiment setup -> paper aim -> problem or limitation | 1 |
| description -> framework overview -> description -> field background -> framework overview -> description -> ablation or sensitivity -> description | 1 |
| experiment setup -> description -> field background -> description -> field background | 1 |
| description -> field background -> result analysis -> description -> paper aim -> description -> field background -> paper aim | 1 |
| description -> problem or limitation -> framework overview -> technical detail -> framework overview -> technical detail -> framework overview -> technical detail | 1 |


| Move position | Most common move | Papers |
| --- | --- | --- |
| 1 | description | 5 |
| 2 | field background | 3 |
| 3 | description | 2 |
| 4 | field background | 3 |
| 5 | description | 2 |
| 6 | description | 3 |

- Prefer the order: setup -> metrics -> baselines -> main results -> ablation -> visualization -> discussion.
- Make each table or figure answer one research question.
- Explain why a metric or scenario matters before interpreting the numbers.

## Conclusion

- Papers with detected section: 12
- Median extracted length: 344 words

| Common move sequence | Papers |
| --- | --- |
| paper aim -> field background -> experiment setup -> result analysis -> description -> result analysis -> description | 1 |
| technical detail -> field background -> description -> problem or limitation -> description -> experiment setup -> field background -> problem or limitation | 1 |
| method claim -> result analysis -> paper aim -> result analysis -> problem or limitation -> description | 1 |
| paper aim -> problem or limitation -> result analysis -> paper aim -> experiment setup -> problem or limitation -> description -> paper aim | 1 |
| paper aim -> framework overview -> field background -> framework overview -> experiment setup -> framework overview -> paper aim | 1 |


| Move position | Most common move | Papers |
| --- | --- | --- |
| 1 | field background | 5 |
| 2 | problem or limitation | 3 |
| 3 | description | 3 |
| 4 | field background | 4 |
| 5 | description | 3 |
| 6 | description | 3 |

- Restate the problem and method in one sentence, then summarize the strongest evidence.
- Mention limitations or future work only after the demonstrated contribution is clear.
- Keep the ending concise and avoid introducing new technical components.

````

---

## scripts/analyze_paper_corpus.py

````python
#!/usr/bin/env python3
"""Analyze a lab paper PDF corpus and generate writing-style references.

The script intentionally writes structural summaries, cue counts, and short
generalized templates instead of copying full source-paper passages.
"""

from __future__ import annotations

import argparse
import collections
import dataclasses
import re
import statistics
import sys
from pathlib import Path
from typing import Dict, Iterable, List, Optional, Sequence, Tuple


SECTION_ORDER = [
    "abstract",
    "introduction",
    "related_work",
    "method",
    "experiments",
    "conclusion",
]

SECTION_DISPLAY = {
    "abstract": "Abstract",
    "introduction": "Introduction",
    "related_work": "Related Work",
    "method": "Method",
    "experiments": "Experiments",
    "conclusion": "Conclusion",
}

HEADING_ALIASES = {
    "abstract": {
        "abstract",
        "summary",
    },
    "introduction": {
        "introduction",
        "introductory remarks",
    },
    "related_work": {
        "related work",
        "related works",
        "literature review",
        "background",
        "preliminaries",
        "related studies",
    },
    "method": {
        "method",
        "methods",
        "methodology",
        "approach",
        "proposed method",
        "proposed approach",
        "proposed framework",
        "framework",
        "model",
        "system model",
        "problem formulation",
        "formulation",
        "algorithm",
        "technical approach",
        "method design",
    },
    "experiments": {
        "experiment",
        "experiments",
        "experimental result",
        "experimental results",
        "experimental evaluation",
        "evaluation",
        "results",
        "results and discussion",
        "simulation",
        "simulations",
        "simulation results",
        "numerical experiments",
        "case study",
        "case studies",
    },
    "conclusion": {
        "conclusion",
        "conclusions",
        "concluding remarks",
        "discussion and conclusion",
        "conclusion and future work",
        "conclusions and future work",
        "conclusion and discussion",
        "conclusions and discussion",
        "summary and conclusion",
        "summary and future work",
    },
    "stop": {
        "references",
        "reference",
        "acknowledgment",
        "acknowledgments",
        "appendix",
        "supplementary material",
    },
}

LABEL_RULES = [
    (
        "field background",
        [
            r"\brecent(ly)?\b",
            r"\bwith the development\b",
            r"\bhas become\b",
            r"\bplays? an important role\b",
            r"\bautonomous\b",
            r"\btraffic\b",
            r"\bvehicle\b",
            r"\btransportation\b",
        ],
    ),
    (
        "problem or limitation",
        [
            r"\bhowever\b",
            r"\bchallenge",
            r"\blimit",
            r"\bexisting\b",
            r"\bcurrent\b",
            r"\bdifficult",
            r"\bremain",
            r"\black\b",
            r"\bfail",
            r"\bignore",
        ],
    ),
    (
        "research gap",
        [
            r"\bfew\b",
            r"\blittle attention\b",
            r"\bnot been\b",
            r"\bunderexplored\b",
            r"\binsufficient\b",
            r"\bwithout considering\b",
        ],
    ),
    (
        "paper aim",
        [
            r"\bthis paper\b",
            r"\bin this work\b",
            r"\bwe aim\b",
            r"\bwe focus\b",
            r"\bwe address\b",
            r"\bto address\b",
        ],
    ),
    (
        "method claim",
        [
            r"\bwe propose\b",
            r"\bwe present\b",
            r"\bwe develop\b",
            r"\bwe introduce\b",
            r"\bwe design\b",
            r"\bwe formulate\b",
            r"\bwe construct\b",
        ],
    ),
    (
        "contribution list",
        [
            r"\bcontribution",
            r"\bmain contributions?\b",
            r"\bfirst\b",
            r"\bsecond\b",
            r"\bthird\b",
        ],
    ),
    (
        "framework overview",
        [
            r"\bframework\b",
            r"\boverall\b",
            r"\barchitecture\b",
            r"\bpipeline\b",
            r"\bsystem\b",
            r"\bmodule\b",
        ],
    ),
    (
        "technical detail",
        [
            r"\balgorithm\b",
            r"\bnetwork\b",
            r"\btraining\b",
            r"\boptimiz",
            r"\bloss\b",
            r"\bobjective\b",
            r"\bparameter\b",
            r"\bstate\b",
            r"\baction\b",
            r"\bconstraint\b",
        ],
    ),
    (
        "experiment setup",
        [
            r"\bdataset\b",
            r"\bbenchmark\b",
            r"\bmetric\b",
            r"\bbaseline\b",
            r"\bsimulator\b",
            r"\bscenario\b",
            r"\bsetting\b",
        ],
    ),
    (
        "result analysis",
        [
            r"\bresult",
            r"\bshow\b",
            r"\bdemonstrat",
            r"\bindicat",
            r"\boutperform",
            r"\bimprov",
            r"\breduce",
            r"\bachiev",
            r"\bcompare",
        ],
    ),
    (
        "ablation or sensitivity",
        [
            r"\bablation\b",
            r"\bsensitivity\b",
            r"\bcomponent\b",
            r"\bvariant\b",
            r"\bwithout\b",
        ],
    ),
    (
        "visualization or case",
        [
            r"\bfigure\b",
            r"\bfig\.\b",
            r"\bvisual",
            r"\bcase study\b",
            r"\bexample\b",
            r"\btrajectory\b",
        ],
    ),
    (
        "conclusion and future work",
        [
            r"\bin conclusion\b",
            r"\bconclude\b",
            r"\bfuture work\b",
            r"\bin future\b",
            r"\bsummary\b",
        ],
    ),
]

TRANSITION_MARKERS = [
    "however",
    "therefore",
    "moreover",
    "furthermore",
    "in addition",
    "to this end",
    "specifically",
    "in particular",
    "as a result",
    "consequently",
    "nevertheless",
    "meanwhile",
    "instead",
    "finally",
]

CONTRIBUTION_VERBS = [
    "propose",
    "present",
    "develop",
    "introduce",
    "design",
    "construct",
    "formulate",
    "build",
]

PROBLEM_CUES = [
    "however",
    "challenge",
    "limitation",
    "limited",
    "existing",
    "current",
    "difficult",
    "remain",
    "lack",
    "ignore",
]

EXPERIMENT_CUES = [
    "results show",
    "results demonstrate",
    "outperform",
    "improve",
    "reduce",
    "achieve",
    "ablation",
    "compared with",
    "comparison",
]

STOPWORDS = {
    "about",
    "after",
    "also",
    "among",
    "based",
    "because",
    "been",
    "being",
    "between",
    "both",
    "could",
    "during",
    "each",
    "from",
    "have",
    "into",
    "more",
    "most",
    "only",
    "other",
    "over",
    "paper",
    "proposed",
    "results",
    "show",
    "such",
    "than",
    "that",
    "their",
    "these",
    "this",
    "through",
    "using",
    "were",
    "when",
    "where",
    "which",
    "with",
    "within",
    "would",
}


@dataclasses.dataclass
class PaperAnalysis:
    path: Path
    title: str
    extractor: str
    word_count: int
    sentence_count: int
    sections: Dict[str, str]
    section_sequence: List[str]
    figure_captions: List[str]
    table_captions: List[str]
    label_sequences: Dict[str, List[str]]
    section_word_counts: Dict[str, int]
    transition_counts: collections.Counter
    contribution_counts: collections.Counter
    problem_counts: collections.Counter
    experiment_counts: collections.Counter
    keyword_counts: collections.Counter


@dataclasses.dataclass
class AICSectionInfo:
    name: str
    found: bool
    text: str
    word_count: int
    sentence_count: int
    paragraph_count: int
    roles: List[str]
    suspicious: List[str]
    extraction_method: str
    confidence: str
    warning_reason: str
    note: str = ""


@dataclasses.dataclass
class AICPaperRecord:
    path: Path
    title: str
    extractor: str
    word_count: int
    extraction_error: str
    sections: Dict[str, AICSectionInfo]


AIC_SECTION_ORDER = ["abstract", "introduction", "conclusion"]
AIC_SECTION_DISPLAY = {
    "abstract": "Abstract",
    "introduction": "Introduction",
    "conclusion": "Conclusion",
}

AIC_LENGTH_LIMITS = {
    "abstract": (80, 450),
    "introduction": (450, 4500),
    "conclusion": (80, 900),
}


def extract_pdf_text(pdf_path: Path) -> Tuple[Optional[str], str, Optional[str]]:
    try:
        import fitz  # type: ignore

        with fitz.open(str(pdf_path)) as doc:
            text = "\n".join(page.get_text("text") for page in doc)
        if text.strip():
            return text, "PyMuPDF", None
    except Exception as exc:
        fitz_error = f"PyMuPDF unavailable or failed: {exc}"
    else:
        fitz_error = "PyMuPDF returned empty text"

    try:
        from pypdf import PdfReader  # type: ignore

        reader = PdfReader(str(pdf_path))
        if getattr(reader, "is_encrypted", False):
            try:
                reader.decrypt("")
            except Exception:
                pass
        pages = []
        for page in reader.pages:
            pages.append(page.extract_text() or "")
        text = "\n".join(pages)
        if text.strip():
            return text, "pypdf", fitz_error
        return None, "pypdf", f"{fitz_error}; pypdf returned empty text"
    except Exception as exc:
        return None, "none", f"{fitz_error}; pypdf failed: {exc}"


def normalize_text(text: str) -> str:
    text = text.replace("\x00", " ").replace("\r", "\n")
    text = re.sub(r"-\n(?=[a-z])", "", text)
    text = re.sub(r"[ \t]+", " ", text)
    text = re.sub(r"\n[ \t]+", "\n", text)
    text = re.sub(r"\n{3,}", "\n\n", text)
    return text.strip()


def clean_line(line: str) -> str:
    return re.sub(r"\s+", " ", line).strip()


def title_from_filename(path: Path) -> str:
    name = path.stem
    name = re.sub(r"^\(PDF\)\s*", "", name, flags=re.I)
    name = re.sub(r"\s+\S\s+-\s+", " - ", name)
    match = re.match(r"^.+?\s+-\s+(?:19|20)\d{2}\s+-\s+(?P<title>.+)$", name)
    if match:
        name = match.group("title")
    name = re.sub(r"\s+", " ", name.replace("_", " ")).strip(" -")
    return name or path.stem


def canonical_heading(line: str) -> Optional[str]:
    candidate = clean_line(line)
    if not candidate:
        return None
    if len(candidate) > 90 or len(candidate.split()) > 12:
        return None
    candidate = re.sub(r"^\d+(?:\.\d+)*\.?\s*", "", candidate)
    candidate = re.sub(r"^[IVXLCDMivxlcdm]+(?:\.|\s+)\s*", "", candidate)
    candidate = re.sub(r"^(?:\(?[a-zA-Z]\)|[a-zA-Z]\.)\s+", "", candidate)
    candidate = candidate.strip(" .:-\t").lower()
    candidate = re.sub(r"\s+", " ", candidate)
    compact_candidate = candidate.replace(" ", "")
    for canonical, aliases in HEADING_ALIASES.items():
        compact_aliases = {alias.replace(" ", "") for alias in aliases}
        if candidate in aliases or compact_candidate in compact_aliases:
            return canonical
    return None


def iter_lines_with_offsets(text: str) -> Iterable[Tuple[int, int, str]]:
    offset = 0
    for raw in text.splitlines(True):
        stripped = raw.strip()
        start = offset + raw.find(stripped) if stripped else offset
        end = start + len(stripped)
        yield start, end, stripped
        offset += len(raw)


def extract_sections(text: str) -> Tuple[Dict[str, str], List[str]]:
    headings: List[Tuple[int, int, str]] = []
    for start, end, line in iter_lines_with_offsets(text):
        heading = canonical_heading(line)
        if heading:
            headings.append((start, end, heading))

    sections: Dict[str, str] = {}
    sequence: List[str] = []
    for index, (start, end, heading) in enumerate(headings):
        if heading == "stop":
            continue
        next_start = len(text)
        for later_start, _, later_heading in headings[index + 1 :]:
            next_start = later_start
            if later_heading == "stop" or later_heading in SECTION_ORDER:
                break
        body = text[end:next_start].strip()
        if len(body) < 80:
            continue
        if heading not in sections or len(body) > len(sections[heading]):
            sections[heading] = body
        if heading in SECTION_ORDER and heading not in sequence:
            sequence.append(heading)

    if "abstract" not in sections:
        abstract_match = re.search(
            r"\bAbstract\s*[-:—–]*\s*(?P<body>.*?)(?=\b(?:Index Terms|Keywords|I\.?\s+Introduction|1\.?\s*Introduction|Introduction)\b)",
            text,
            flags=re.I | re.S,
        )
        if abstract_match:
            body = abstract_match.group("body").strip()
            if len(body) >= 80:
                sections["abstract"] = body
                sequence.insert(0, "abstract")

    return sections, sequence


def sentence_split(text: str) -> List[str]:
    text = re.sub(r"\s+", " ", text).strip()
    if not text:
        return []
    parts = re.split(r"(?<=[.!?])\s*(?=[A-Z(])", text)
    sentences = []
    for part in parts:
        sent = part.strip()
        if 35 <= len(sent) <= 450 and (word_count(sent) >= 6 or len(sent) >= 80):
            sentences.append(sent)
    return sentences


def word_count(text: str) -> int:
    return len(re.findall(r"[A-Za-z][A-Za-z0-9-]*", text))


def label_sentence(sentence: str) -> str:
    lower = sentence.lower()
    for label, patterns in LABEL_RULES:
        if any(re.search(pattern, lower) for pattern in patterns):
            return label
    return "description"


def compressed_label_sequence(sentences: Sequence[str], limit: int = 8) -> List[str]:
    labels: List[str] = []
    for sentence in sentences:
        label = label_sentence(sentence)
        if not labels or labels[-1] != label:
            labels.append(label)
        if len(labels) >= limit:
            break
    return labels


def detect_captions(text: str) -> Tuple[List[str], List[str]]:
    lines = [clean_line(line) for line in text.splitlines()]
    figure_captions: List[str] = []
    table_captions: List[str] = []
    fig_re = re.compile(r"^(?:fig\.?|figure)\s*\d+[\w().-]*\s*[:.\-]?\s+(.+)", re.I)
    table_re = re.compile(r"^(?:table|tab\.)\s*(?:\d+|[ivxlcdm]+)[\w().-]*\s*[:.\-]?\s*(.*)", re.I)
    for index, line in enumerate(lines):
        if not line:
            continue
        target: Optional[List[str]] = None
        if fig_re.match(line):
            target = figure_captions
        elif table_re.match(line):
            target = table_captions
        if target is None:
            continue
        caption_parts = [line]
        for lookahead in lines[index + 1 : index + 3]:
            if not lookahead or canonical_heading(lookahead):
                break
            if fig_re.match(lookahead) or table_re.match(lookahead):
                break
            if len(lookahead.split()) <= 18:
                caption_parts.append(lookahead)
        target.append(" ".join(caption_parts)[:300])
    return figure_captions, table_captions


def cue_counts(sentences: Sequence[str], cues: Sequence[str]) -> collections.Counter:
    counts: collections.Counter = collections.Counter()
    for sentence in sentences:
        lower = sentence.lower()
        for cue in cues:
            if cue in lower:
                counts[cue] += 1
    return counts


def contribution_counts(sentences: Sequence[str]) -> collections.Counter:
    counts: collections.Counter = collections.Counter()
    for sentence in sentences:
        lower = sentence.lower()
        if "contribution" in lower:
            counts["explicit contribution list"] += 1
        for verb in CONTRIBUTION_VERBS:
            if re.search(rf"\bwe\s+{verb}\b", lower):
                counts[f"we {verb}"] += 1
    return counts


def keyword_counts(text: str) -> collections.Counter:
    counts: collections.Counter = collections.Counter()
    for word in re.findall(r"[A-Za-z][A-Za-z-]{3,}", text.lower()):
        word = word.strip("-")
        if word and word not in STOPWORDS:
            counts[word] += 1
    return counts


def analyze_paper(pdf_path: Path) -> Tuple[Optional[PaperAnalysis], Optional[str]]:
    raw_text, extractor, warning = extract_pdf_text(pdf_path)
    if not raw_text:
        return None, warning or "No extractable text"
    text = normalize_text(raw_text)
    wc = word_count(text)
    if wc < 800:
        return None, f"Extracted text too short for reliable analysis ({wc} words)"

    sections, sequence = extract_sections(text)
    fig_caps, table_caps = detect_captions(text)
    all_sentences = sentence_split(text)
    label_sequences: Dict[str, List[str]] = {}
    section_word_counts: Dict[str, int] = {}
    for section_name, section_text in sections.items():
        section_sentences = sentence_split(section_text)
        label_sequences[section_name] = compressed_label_sequence(section_sentences)
        section_word_counts[section_name] = word_count(section_text)

    analysis = PaperAnalysis(
        path=pdf_path,
        title=title_from_filename(pdf_path),
        extractor=extractor if not warning else f"{extractor} (fallback: {warning})",
        word_count=wc,
        sentence_count=len(all_sentences),
        sections=sections,
        section_sequence=sequence,
        figure_captions=fig_caps,
        table_captions=table_caps,
        label_sequences=label_sequences,
        section_word_counts=section_word_counts,
        transition_counts=cue_counts(all_sentences, TRANSITION_MARKERS),
        contribution_counts=contribution_counts(all_sentences),
        problem_counts=cue_counts(all_sentences, PROBLEM_CUES),
        experiment_counts=cue_counts(all_sentences, EXPERIMENT_CUES),
        keyword_counts=keyword_counts(text),
    )
    return analysis, None


def find_heading_start(text: str, target: str) -> Optional[int]:
    for start, _, line in iter_lines_with_offsets(text):
        if canonical_heading(line) == target:
            return start
    return None


def infer_front_matter_abstract(text: str) -> Tuple[str, str]:
    intro_start = find_heading_start(text, "introduction")
    if intro_start is None or intro_start < 300:
        return "", "No reliable Introduction boundary for front-matter fallback"

    front_matter = text[:intro_start]
    sentences = sentence_split(front_matter)
    if len(sentences) >= 3:
        candidate = " ".join(sentences[-8:])
        note = "Inferred from front matter before Introduction"
    else:
        candidate = front_matter[-2500:]
        note = "Inferred from front matter before Introduction with weak sentence boundaries"

    wc = word_count(candidate)
    if wc < 60 and len(candidate) < 450:
        return "", "Front-matter fallback was too short"
    if wc > 520:
        words = re.findall(r"\S+", candidate)
        candidate = " ".join(words[-520:])
        note += "; trimmed to likely abstract-sized tail"
    return candidate.strip(), note


def paragraph_count(text: str, section_name: str, sentence_count_value: int) -> int:
    paragraphs = [
        paragraph
        for paragraph in re.split(r"\n\s*\n", text)
        if word_count(paragraph) >= 35
    ]
    if len(paragraphs) > 1:
        return len(paragraphs)
    if section_name == "abstract":
        return 1 if text.strip() else 0
    if not text.strip():
        return 0
    return max(1, int(round(sentence_count_value / 6.0)))


def aic_role(sentence: str) -> str:
    lower = sentence.lower()
    compact = re.sub(r"[^a-z0-9]+", "", lower)
    if re.search(r"\b(contribution|contributes?|significance|benefit|enable|facilitate)\b", lower):
        return "contribution/significance"
    if re.search(r"\b(results?|experiments?|simulation|evaluation|show|demonstrat|outperform|improv|reduce|achiev|validate)\b", lower) or "experimentalresults" in compact:
        return "experiment/result"
    if re.search(r"\b(we propose|we present|we develop|we introduce|we design|this paper proposes|this work proposes)\b", lower) or any(marker in compact for marker in ["wepropose", "wepresent", "wedevelop", "weintroduce", "wedesign", "thispaperproposes"]):
        return "proposed method"
    if re.search(r"\b(framework|architecture|module|algorithm|model|strategy|sampling|training|optimization|objective|loss|mechanism)\b", lower):
        return "key mechanism"
    if re.search(r"\b(existing|previous|current|traditional|state-of-the-art|however|nevertheless|limited|limitation|fail|lack|ignore)\b", lower) or any(marker in compact for marker in ["existing", "however", "limitation", "limitations", "currentmethods"]):
        return "existing insufficiency"
    if re.search(r"\b(challenge|difficult|critical|problem|need|require|gap|underexplored|insufficient)\b", lower):
        return "specific problem/gap"
    if re.search(r"\b(autonomous|traffic|transportation|vehicle|driving|cooperative|scenario|safety|control|perception)\b", lower):
        return "background"
    return "description"


def compressed_roles(roles: Sequence[str], limit: int = 10) -> List[str]:
    compressed: List[str] = []
    for role in roles:
        if not compressed or compressed[-1] != role:
            compressed.append(role)
        if len(compressed) >= limit:
            break
    return compressed


def role_coverage(info: AICSectionInfo) -> set:
    return set(info.roles)


def is_stat_eligible(record: AICPaperRecord, section_name: str) -> bool:
    info = record.sections[section_name]
    return info.found and info.confidence != "low"


def stat_records(
    records: Sequence[AICPaperRecord], section_name: str
) -> List[AICPaperRecord]:
    return [record for record in records if is_stat_eligible(record, section_name)]


def inspect_section(
    section_name: str,
    text: str,
    found: bool,
    extraction_method: str = "heading",
    note: str = "",
) -> AICSectionInfo:
    text = text.strip()
    sentences = sentence_split(text)
    roles = [aic_role(sentence) for sentence in sentences]
    wc = word_count(text)
    pc = paragraph_count(text, section_name, len(sentences))
    suspicious: List[str] = []
    min_words, max_words = AIC_LENGTH_LIMITS[section_name]

    low_confidence = False
    if not found:
        suspicious.append("not detected")
        low_confidence = True
    elif wc < min_words:
        suspicious.append(f"too short (<{min_words} words)")
        if section_name == "abstract":
            low_confidence = True
    elif wc > max_words:
        suspicious.append(f"too long (>{max_words} words)")
        if section_name == "introduction":
            suspicious.append("possible section leakage")
            low_confidence = True
        elif section_name == "conclusion":
            low_confidence = True

    if found and section_name == "abstract":
        if len(sentences) < 3:
            suspicious.append("few sentence boundaries")
        coverage = role_coverage(
            AICSectionInfo(
                section_name,
                found,
                text,
                wc,
                len(sentences),
                pc,
                roles,
                [],
                extraction_method,
                "high",
                "",
            )
        )
        if "proposed method" not in coverage and "key mechanism" not in coverage:
            suspicious.append("method role unclear")
        if "experiment/result" not in coverage:
            suspicious.append("result role unclear")

    if found and section_name == "introduction":
        coverage = set(roles)
        if "specific problem/gap" not in coverage and "existing insufficiency" not in coverage:
            suspicious.append("gap or insufficiency not explicit")
        if "proposed method" not in coverage and "key mechanism" not in coverage:
            suspicious.append("method entry not obvious")

    if found and section_name == "conclusion":
        coverage = set(roles)
        if "experiment/result" not in coverage:
            suspicious.append("evidence summary not obvious")
        if "background" in roles[:2] and "proposed method" not in coverage and "key mechanism" not in coverage:
            suspicious.append("may repeat broad framing without method recap")

    if found and text and text[-1] not in ".!?)]}":
        suspicious.append("may be truncated")

    warning_reason = "; ".join(suspicious)
    if low_confidence:
        confidence = "low"
    elif suspicious:
        confidence = "medium"
    else:
        confidence = "high"

    return AICSectionInfo(
        name=section_name,
        found=found,
        text=text,
        word_count=wc,
        sentence_count=len(sentences),
        paragraph_count=pc,
        roles=roles,
        suspicious=suspicious,
        extraction_method=extraction_method if found else "not detected",
        confidence=confidence,
        warning_reason=warning_reason,
        note=note,
    )


def extract_aic_sections(text: str) -> Dict[str, AICSectionInfo]:
    sections, _ = extract_sections(text)
    aic_sections: Dict[str, AICSectionInfo] = {}
    for section_name in AIC_SECTION_ORDER:
        section_text = sections.get(section_name, "")
        note = "Detected by heading"
        found = bool(section_text)
        extraction_method = "heading"
        if section_name == "abstract" and not found:
            section_text, note = infer_front_matter_abstract(text)
            found = bool(section_text)
            extraction_method = "front-matter fallback" if found else "not detected"
        aic_sections[section_name] = inspect_section(
            section_name=section_name,
            text=section_text,
            found=found,
            extraction_method=extraction_method,
            note=note if found else "Section heading or fallback not found",
        )
    return aic_sections


def analyze_aic_paper(pdf_path: Path) -> AICPaperRecord:
    raw_text, extractor, warning = extract_pdf_text(pdf_path)
    if not raw_text:
        empty_sections = {
            name: inspect_section(
                name,
                "",
                False,
                extraction_method="not detected",
                note="PDF text extraction failed",
            )
            for name in AIC_SECTION_ORDER
        }
        return AICPaperRecord(
            path=pdf_path,
            title=title_from_filename(pdf_path),
            extractor=extractor,
            word_count=0,
            extraction_error=warning or "No extractable text",
            sections=empty_sections,
        )

    text = normalize_text(raw_text)
    wc = word_count(text)
    sections = extract_aic_sections(text)
    return AICPaperRecord(
        path=pdf_path,
        title=title_from_filename(pdf_path),
        extractor=extractor if not warning else f"{extractor} (fallback: {warning})",
        word_count=wc,
        extraction_error="" if wc >= 800 else f"Extracted text may be too short ({wc} words)",
        sections=sections,
    )


def aic_score(info: AICSectionInfo, expected_roles: Sequence[str]) -> int:
    coverage = role_coverage(info)
    return sum(1 for role in expected_roles if role in coverage)


def strongest_records(
    records: Sequence[AICPaperRecord], section_name: str, expected_roles: Sequence[str], n: int = 4
) -> List[AICPaperRecord]:
    available = stat_records(records, section_name)
    return sorted(
        available,
        key=lambda record: (
            aic_score(record.sections[section_name], expected_roles),
            -len(record.sections[section_name].suspicious),
            record.sections[section_name].word_count,
        ),
        reverse=True,
    )[:n]


def weakest_records(
    records: Sequence[AICPaperRecord], section_name: str, expected_roles: Sequence[str], n: int = 4
) -> List[AICPaperRecord]:
    available = stat_records(records, section_name)
    return sorted(
        available,
        key=lambda record: (
            record.sections[section_name].found,
            -len(record.sections[section_name].suspicious),
            aic_score(record.sections[section_name], expected_roles),
            record.sections[section_name].word_count,
        ),
    )[:n]


def short_title(title: str, limit: int = 82) -> str:
    return title if len(title) <= limit else title[: limit - 3].rstrip() + "..."


def status_text(info: AICSectionInfo) -> str:
    if not info.found:
        return "No"
    if info.suspicious:
        return "Yes; check " + "; ".join(info.suspicious[:3])
    return "Yes"


def section_summary(
    sections: Dict[str, AICSectionInfo], attr: str, empty: str = "none"
) -> str:
    parts = []
    for name in AIC_SECTION_ORDER:
        value = getattr(sections[name], attr)
        parts.append(f"{AIC_SECTION_DISPLAY[name]}={value or empty}")
    return "; ".join(parts)


def role_sequence_text(info: AICSectionInfo) -> str:
    if not info.roles:
        return "not available"
    return " -> ".join(compressed_roles(info.roles))


def abstract_expected_roles() -> List[str]:
    return [
        "background",
        "specific problem/gap",
        "existing insufficiency",
        "proposed method",
        "key mechanism",
        "experiment/result",
        "contribution/significance",
    ]


def introduction_expected_roles() -> List[str]:
    return [
        "background",
        "specific problem/gap",
        "existing insufficiency",
        "proposed method",
        "key mechanism",
        "contribution/significance",
    ]


def conclusion_expected_roles() -> List[str]:
    return [
        "specific problem/gap",
        "proposed method",
        "key mechanism",
        "experiment/result",
        "contribution/significance",
    ]


def median_section_value(
    records: Sequence[AICPaperRecord], section_name: str, attr: str
) -> int:
    values = [
        getattr(record.sections[section_name], attr)
        for record in records
        if is_stat_eligible(record, section_name)
    ]
    return median_or_zero(values)


def section_role_positions(
    records: Sequence[AICPaperRecord], section_name: str, max_positions: int = 8
) -> List[List[object]]:
    positions: List[collections.Counter] = [collections.Counter() for _ in range(max_positions)]
    for record in records:
        info = record.sections[section_name]
        if not is_stat_eligible(record, section_name):
            continue
        for index, role in enumerate(compressed_roles(info.roles, max_positions)):
            positions[index][role] += 1
    rows: List[List[object]] = []
    for index, counter in enumerate(positions, start=1):
        if counter:
            role, count = counter.most_common(1)[0]
            rows.append([index, role, count])
    return rows


def logic_coverage_rows(
    records: Sequence[AICPaperRecord], section_name: str, expected_roles: Sequence[str]
) -> List[List[object]]:
    rows = []
    detected = stat_records(records, section_name)
    for role in expected_roles:
        count = sum(1 for record in detected if role in role_coverage(record.sections[section_name]))
        rows.append([role, count, f"{count}/{len(detected)}" if detected else "0/0"])
    return rows


def strength_reason(info: AICSectionInfo, expected_roles: Sequence[str]) -> str:
    coverage = role_coverage(info)
    hits = [role for role in expected_roles if role in coverage]
    if not hits:
        return "structure needs manual inspection"
    return "covers " + ", ".join(hits[:4])


def weakness_reason(info: AICSectionInfo, expected_roles: Sequence[str]) -> str:
    if not info.found:
        return "section not detected"
    missing = [role for role in expected_roles if role not in role_coverage(info)]
    reasons = list(info.suspicious[:2])
    if missing:
        reasons.append("missing/unclear " + ", ".join(missing[:3]))
    return "; ".join(reasons) if reasons else "mostly complete; inspect for rhetorical tightness"


def build_abstract_deep_patterns(records: Sequence[AICPaperRecord]) -> str:
    expected = abstract_expected_roles()
    detected = [record for record in records if record.sections["abstract"].found]
    usable = stat_records(records, "abstract")
    strong_rows = [
        [short_title(record.title), strength_reason(record.sections["abstract"], expected)]
        for record in strongest_records(records, "abstract", expected)
    ]
    weak_rows = [
        [short_title(record.title), weakness_reason(record.sections["abstract"], expected)]
        for record in weakest_records(records, "abstract", expected)
    ]
    return f"""# Abstract Deep Patterns

This file summarizes Abstract writing patterns from the 802 paper corpus. It uses structural signals only and avoids copying source-paper passages.

## Corpus Signals

- Abstracts detected: {len(detected)}/{len(records)}
- Abstracts used for deep-pattern statistics: {len(usable)}/{len(records)}
- Low-confidence Abstracts excluded from statistics: {len(detected) - len(usable)}
- Median Abstract length: {median_section_value(records, "abstract", "word_count")} words
- Median sentence count: {median_section_value(records, "abstract", "sentence_count")} sentences

Low detected coverage for a role may come from rule-based detection limits, not from a recommended writing style. New Abstracts must include a contribution or implication sentence even if the automatic detector reports low contribution coverage in the corpus.

## Sentence-Level Functions

{md_table(["Sentence/move position", "Most common function", "Papers"], section_role_positions(records, "abstract", 7))}

## Logic Coverage

{md_table(["Expected Abstract role", "Detected papers", "Coverage"], logic_coverage_rows(records, "abstract", expected))}

## Stronger Abstracts

{md_table(["Paper", "Why it is useful to learn from"], strong_rows)}

## Abstracts That Need Caution

{md_table(["Paper", "Likely weakness to avoid"], weak_rows)}

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
"""


def build_introduction_deep_patterns(records: Sequence[AICPaperRecord]) -> str:
    expected = introduction_expected_roles()
    detected = [record for record in records if record.sections["introduction"].found]
    usable = stat_records(records, "introduction")
    strong_rows = [
        [short_title(record.title), strength_reason(record.sections["introduction"], expected)]
        for record in strongest_records(records, "introduction", expected)
    ]
    weak_rows = [
        [short_title(record.title), weakness_reason(record.sections["introduction"], expected)]
        for record in weakest_records(records, "introduction", expected)
    ]
    paragraph_rows = [
        ["Paragraph 1", "Establish why the research problem matters", "Is the field context tied to the paper's task?", "A generic domain opening with no task pressure."],
        ["Paragraph 2", "Narrow to practical challenge", "Does the challenge name a concrete safety/efficiency/data/control issue?", "A challenge paragraph that only says the problem is difficult."],
        ["Paragraph 3", "Classify existing methods and expose shared limits", "Are method families compared by assumptions and failure modes?", "A literature list with no synthesis."],
        ["Paragraph 4", "Introduce the core idea", "Does the proposed method naturally answer the gap?", "A sudden method claim that is not motivated by the previous gap."],
        ["Paragraph 5", "Summarize the framework", "Can a reader see the method's modules and mechanism?", "A long implementation preview without a high-level mechanism."],
        ["Paragraph 6", "List contributions", "Does each contribution correspond to a stated gap?", "Contributions that repeat features rather than advances."],
    ]
    return f"""# Introduction Deep Patterns

This file summarizes Introduction writing patterns for the 802 corpus.

## Corpus Signals

- Introductions detected: {len(detected)}/{len(records)}
- Introductions used for deep-pattern statistics: {len(usable)}/{len(records)}
- Low-confidence Introductions excluded from statistics: {len(detected) - len(usable)}
- Median Introduction length: {median_section_value(records, "introduction", "word_count")} words
- Approximate median paragraph count: {median_section_value(records, "introduction", "paragraph_count")} paragraphs

## Common Paragraph/Move Order

{md_table(["Move position", "Most common function", "Papers"], section_role_positions(records, "introduction", 8))}

## Logic Coverage

{md_table(["Expected Introduction role", "Detected papers", "Coverage"], logic_coverage_rows(records, "introduction", expected))}

## Stronger Introductions

{md_table(["Paper", "Why it is useful to learn from"], strong_rows)}

## Introductions That Need Caution

{md_table(["Paper", "Likely weakness to avoid"], weak_rows)}

## 802 Introduction Narrative Style

- Build a chain from real-world importance to a technical bottleneck.
- Classify existing methods by how they model, sample, control, perceive, or evaluate the target system.
- Critique existing methods through shared assumptions, missing variables, weak generalization, data cost, or limited evaluation, rather than by merely listing citations.
- Let the proposed method appear as the natural answer to the gap.
- Make the contribution list map back to the gap: formulation/data/scenario, method/model/control, and experimental validation.

## Paragraph-Level Template

{md_table(["Unit", "Writing goal", "Self-check question", "Common failure"], paragraph_rows)}

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
"""


def build_conclusion_deep_patterns(records: Sequence[AICPaperRecord]) -> str:
    expected = conclusion_expected_roles()
    detected = [record for record in records if record.sections["conclusion"].found]
    usable = stat_records(records, "conclusion")
    strong_rows = [
        [short_title(record.title), strength_reason(record.sections["conclusion"], expected)]
        for record in strongest_records(records, "conclusion", expected)
    ]
    weak_rows = [
        [short_title(record.title), weakness_reason(record.sections["conclusion"], expected)]
        for record in weakest_records(records, "conclusion", expected)
    ]
    return f"""# Conclusion Deep Patterns

This file summarizes Conclusion writing patterns for the 802 corpus.

## Corpus Signals

- Conclusions detected: {len(detected)}/{len(records)}
- Conclusions used for deep-pattern statistics: {len(usable)}/{len(records)}
- Low-confidence Conclusions excluded from statistics: {len(detected) - len(usable)}
- Median Conclusion length: {median_section_value(records, "conclusion", "word_count")} words
- Approximate median paragraph count: {median_section_value(records, "conclusion", "paragraph_count")} paragraphs

The Conclusion must not be a compressed Abstract. It should add evidence-facing synthesis: what the experiments or analysis now support about the original research problem.

## Common Sentence/Move Order

{md_table(["Move position", "Most common function", "Papers"], section_role_positions(records, "conclusion", 7))}

## Logic Coverage

{md_table(["Expected Conclusion role", "Detected papers", "Coverage"], logic_coverage_rows(records, "conclusion", expected))}

## Stronger Conclusions

{md_table(["Paper", "Why it is useful to learn from"], strong_rows)}

## Conclusions That Need Caution

{md_table(["Paper", "Likely weakness to avoid"], weak_rows)}

## 802 Conclusion Style

- Return to the research problem with a narrower angle than the Introduction.
- Summarize the proposed method as a contribution, not as a procedural replay.
- State the strongest experimental finding and connect it to the original challenge.
- Provide evidence-facing synthesis: interpret what the evidence proves, limits, or suggests.
- Explain practical or scientific meaning without overselling.
- Mention limitations or future work only after the achieved contribution is clear.

## Fatal Problems

- Conclusion only repeats the Abstract.
- No evidence-facing synthesis of experimental findings.
- No return to the research problem.
- New claims appear that were not supported earlier.
- Limitations or future work replace the main takeaway.

## Major Problems

- Method summary is too procedural and does not state the contribution.
- Evidence is mentioned but not interpreted.
- Practical meaning is vague or exaggerated.
- Final sentence is a generic future-work template.
- The paragraph order hides the main takeaway.

## Minor Problems

- Ending is clear but stylistically flat.
- Repeated phrases make the conclusion sound copied from earlier sections.
- Limitation wording is too cautious or too broad.
- Transitions between evidence and meaning are abrupt.

## Strong Vs. Weak Conclusion

- Strong: problem recap -> method contribution -> evidence -> meaning -> restrained limitation/future direction.
- Weak: a compressed Abstract with no new synthesis, no evidence recap, and a generic future-work sentence.

## Executable Template

- Sentence 1: Return to the research problem.
- Sentence 2: Summarize the proposed method or framework.
- Sentence 3: Summarize the key experimental finding.
- Sentence 4: State why the finding matters for the task or application.
- Sentence 5: Add limitation or future work in restrained language when appropriate.
"""


def build_aic_style_guide(records: Sequence[AICPaperRecord]) -> str:
    found_counts = {
        section: sum(1 for record in records if record.sections[section].found)
        for section in AIC_SECTION_ORDER
    }
    usable_counts = {
        section: len(stat_records(records, section))
        for section in AIC_SECTION_ORDER
    }
    return f"""# AIC Style Guide

This guide combines Abstract, Introduction, and Conclusion patterns from the 802 paper corpus.

## Corpus Coverage

- Abstract detected: {found_counts["abstract"]}/{len(records)}
- Introduction detected: {found_counts["introduction"]}/{len(records)}
- Conclusion detected: {found_counts["conclusion"]}/{len(records)}
- Abstract used for deep statistics: {usable_counts["abstract"]}/{len(records)}
- Introduction used for deep statistics: {usable_counts["introduction"]}/{len(records)}
- Conclusion used for deep statistics: {usable_counts["conclusion"]}/{len(records)}

Low-confidence sections are retained only in `aic_per_paper_inventory.md`; they are excluded from deep-pattern statistics.

## Stable 802 Style

- The writing is engineering-evidence oriented: it values concrete tasks, mechanisms, experiments, and scenario-level validation.
- The central chain is problem -> gap -> method -> evidence -> meaning.
- The tone is assertive about what was built, but restrained about generality unless backed by experiments.
- Contributions are usually described through a concrete artifact: model, framework, control strategy, sampling method, scenario system, dataset, or evaluation pipeline.
- Experimental results are strongest when tied to baselines, scenarios, metrics, and ablations.

## How AIC Sections Work Together

- Abstract compresses the full chain into 5-7 functional moves.
- Introduction expands the chain and makes the gap unavoidable.
- Conclusion closes the chain by returning to the problem and explaining what the evidence now supports.

## Contribution Description Rules

- Name the contribution as a technical object or finding.
- State what gap it addresses.
- Explain how it was validated.
- Avoid "first", "novel", "significant", and "effective" unless the evidence is explicit.

## Result Description Rules

- Prefer measured improvements, scenario coverage, robustness, efficiency, stability, accuracy, or safety-related outcomes.
- If exact numbers are unavailable, mention the benchmark, simulator, dataset, or scenario type.
- Tie each result back to the research problem instead of treating it as isolated performance.

## Imitation Without Copying

- Imitate organization, not sentences.
- Reuse rhetorical roles: background, gap, method, mechanism, evidence, meaning.
- Replace generic paper-style phrases with task-specific claims.
- Use short phrase templates only as scaffolds, then rewrite with the user's actual technical content.
"""


def build_aic_revision_checklist() -> str:
    return """# AIC Revision Checklist

Use this checklist before showing Abstract, Introduction, or Conclusion drafts to an advisor.

## Abstract

### Fatal Problems: Must Rewrite

- Missing a concrete research problem.
- Missing the proposed method or making it unrecognizable.
- Missing experimental evidence, evaluation setting, or an explicit evidence placeholder.
- Missing a contribution or implication sentence.
- Inventing results, numbers, novelty, or significance beyond the user's information.

### Major Problems: Structural Revision Needed

- The logic chain is incomplete: background -> problem -> insufficiency -> method -> mechanism -> evidence -> implication.
- The problem is too generic to justify the method.
- The gap is a slogan such as "existing methods are limited" without a cause.
- The method sentence lists components but not the core mechanism.
- The result sentence does not mention metric, benchmark, scenario, or verified effect.

### Minor Problems: Language Polishing

- Sentence order is good but transitions are stiff.
- Repetition weakens fluency.
- A sentence is too long or overloaded.
- Chinese-English literal phrasing or redundant academic wording remains.
- Terminology is inconsistent across sentences.

## Introduction

### Fatal Problems: Must Rewrite

- No clear research question or task emerges.
- The gap is missing before the proposed method appears.
- Existing work is only listed, with no synthesis or shared limitation.
- The proposed method does not answer the stated gap.
- The contribution list is absent or disconnected from the paper's claims.

### Major Problems: Structural Revision Needed

- The first paragraph is too broad and not task-facing.
- The challenge is not concrete enough.
- Existing methods are not grouped by family, assumption, or limitation.
- The method appears too suddenly or too late.
- Contributions describe features rather than advances.
- Claims are stronger than the experiments can support.

### Minor Problems: Language Polishing

- Topic sentences are functional but not sharp.
- Transitions between paragraphs are decorative rather than logical.
- Citation-group sentences are repetitive.
- Some sentences sound academic but carry little information.
- Terminology and abbreviations need harmonization.

## Conclusion

### Fatal Problems: Must Rewrite

- The Conclusion is only a compressed Abstract.
- It does not return to the research problem.
- It lacks evidence-facing synthesis of the main findings.
- It introduces unsupported new claims.
- It ends with generic future work instead of a takeaway.

### Major Problems: Structural Revision Needed

- Method summary is too procedural and does not state the contribution.
- Experimental evidence is mentioned but not interpreted.
- Practical or scientific meaning is vague or exaggerated.
- Limitation/future-work wording is too broad.
- The final sentence does not leave a clear contribution.

### Minor Problems: Language Polishing

- Repeated wording from the Abstract or Introduction remains.
- Evidence and meaning are connected by weak transitions.
- The conclusion is correct but stylistically flat.
- Future work is reasonable but phrased mechanically.
- Sentence length or rhythm needs smoothing.
"""


def build_aic_common_weaknesses() -> str:
    rows = [
        [
            "Background is too broad",
            "The opening could fit many papers and delays the real task.",
            "The reader cannot see why this paper is necessary.",
            "Name the application, task, and pressure point within one or two sentences.",
            "Before: Intelligent transportation is important. After: Safe lane-change testing requires identifying rare interactive scenarios that expose AV failure modes.",
        ],
        [
            "Challenge is not concrete",
            "The text says the problem is difficult but does not say why.",
            "A vague challenge cannot justify a specific method.",
            "State the technical cause: data sparsity, interaction uncertainty, distribution shift, limited observability, or optimization cost.",
            "Before: Existing methods face many challenges. After: Existing sampling methods often miss low-probability but high-risk interactions.",
        ],
        [
            "Proposed method appears too late",
            "Long background and literature delay the paper identity.",
            "The reader may lose the thread before seeing the solution.",
            "Introduce the core idea immediately after the gap, then expand details later.",
            "Before: Several paragraphs of related work before the method. After: Gap paragraph followed by a concise method sentence.",
        ],
        [
            "Contribution list does not match the gap",
            "Contributions list features without showing why they solve the stated problem.",
            "The argument feels assembled rather than inevitable.",
            "Map each contribution to one limitation or missing capability.",
            "Before: We design a framework and conduct experiments. After: We formulate the scenario gap, design an adaptive sampler for it, and validate coverage gains.",
        ],
        [
            "Conclusion repeats the Abstract",
            "It restates method and results without synthesis.",
            "The ending misses the chance to explain what the evidence means.",
            "Add a problem-facing takeaway and restrained implication.",
            "Before: This paper proposed X and experiments show it works. After: The results indicate that X improves evaluation coverage under interactive corner cases.",
        ],
        [
            "Experimental results are disconnected",
            "Numbers or comparisons are mentioned without linking to the research question.",
            "Evidence does not strengthen the paper's central claim.",
            "Interpret each result through the mechanism or gap.",
            "Before: The method improves accuracy. After: The gain suggests that cooperative BEV information reduces occlusion-induced prediction errors.",
        ],
        [
            "Future work is too template-like",
            "The final sentence says future work will improve or extend the method with no direction.",
            "It sounds perfunctory and weakens the ending.",
            "Name one restrained limitation and one concrete next direction.",
            "Before: Future work will improve the method. After: Future work will test the framework under denser mixed-traffic scenarios.",
        ],
    ]
    return "# AIC Common Weaknesses\n\n" + md_table(
        ["Weakness", "Problem manifestation", "Why it weakens persuasion", "Revision strategy", "Abstract before/after example"],
        rows,
    )


def per_paper_learning_point(record: AICPaperRecord) -> str:
    abstract = record.sections["abstract"]
    introduction = record.sections["introduction"]
    conclusion = record.sections["conclusion"]
    if abstract.found and abstract.confidence != "low" and aic_score(abstract, abstract_expected_roles()) >= 4:
        return "Abstract provides a compact problem-method-evidence chain."
    if introduction.found and introduction.confidence != "low" and aic_score(introduction, introduction_expected_roles()) >= 4:
        return "Introduction builds a usable route from task background to method motivation."
    if conclusion.found and conclusion.confidence != "low" and aic_score(conclusion, conclusion_expected_roles()) >= 3:
        return "Conclusion reconnects method and evidence to the research problem."
    return "Use the detected AIC structure as inventory, but inspect rhetorical completeness manually."


def per_paper_avoid_point(record: AICPaperRecord) -> str:
    for section_name in AIC_SECTION_ORDER:
        info = record.sections[section_name]
        if not info.found:
            return f"{AIC_SECTION_DISPLAY[section_name]} was not reliably detected; avoid relying on this paper for that section without manual checking."
        if info.confidence == "low":
            return f"{AIC_SECTION_DISPLAY[section_name]} is low confidence: {info.warning_reason or 'manual check needed'}."
        if info.suspicious:
            return f"{AIC_SECTION_DISPLAY[section_name]} needs caution: {info.suspicious[0]}."
    return "Avoid copying surface phrases; learn the structure rather than the wording."


def build_aic_per_paper_inventory(records: Sequence[AICPaperRecord]) -> str:
    rows = []
    for record in records:
        abstract = record.sections["abstract"]
        introduction = record.sections["introduction"]
        conclusion = record.sections["conclusion"]
        rows.append(
            [
                record.path.name,
                status_text(abstract),
                status_text(introduction),
                status_text(conclusion),
                section_summary(record.sections, "extraction_method"),
                section_summary(record.sections, "confidence"),
                section_summary(record.sections, "warning_reason"),
                f"{abstract.sentence_count} sentences / {abstract.word_count} words" if abstract.found else "not detected",
                f"{introduction.paragraph_count} approx paragraphs / {introduction.word_count} words" if introduction.found else "not detected",
                f"{conclusion.paragraph_count} approx paragraphs / {conclusion.word_count} words" if conclusion.found else "not detected",
                per_paper_learning_point(record),
                per_paper_avoid_point(record),
            ]
        )
    notes = [
        [record.path.name, record.extraction_error]
        for record in records
        if record.extraction_error
    ]
    return f"""# AIC Per-Paper Inventory

This inventory records Abstract, Introduction, and Conclusion extraction status for each PDF. Low-confidence sections remain here for audit but are excluded from deep-pattern statistics.

{md_table(["File", "Abstract", "Introduction", "Conclusion", "extraction_method", "confidence", "warning_reason", "Abstract length", "Introduction length", "Conclusion length", "AIC point to learn", "AIC point to avoid"], rows)}

## Extraction Notes

{md_table(["File", "Note"], notes) if notes else "_No PDF-level extraction errors were detected._\n"}
"""


def write_aic_outputs(output_dir: Path, records: Sequence[AICPaperRecord]) -> None:
    output_dir.mkdir(parents=True, exist_ok=True)
    files = {
        "abstract_deep_patterns.md": build_abstract_deep_patterns(records),
        "introduction_deep_patterns.md": build_introduction_deep_patterns(records),
        "conclusion_deep_patterns.md": build_conclusion_deep_patterns(records),
        "aic_style_guide.md": build_aic_style_guide(records),
        "aic_revision_checklist.md": build_aic_revision_checklist(),
        "aic_common_weaknesses.md": build_aic_common_weaknesses(),
        "aic_per_paper_inventory.md": build_aic_per_paper_inventory(records),
    }
    for filename, content in files.items():
        (output_dir / filename).write_text(content, encoding="utf-8", newline="\n")


def md_table(headers: Sequence[str], rows: Sequence[Sequence[object]]) -> str:
    if not rows:
        return "_No data available._\n"
    output = [
        "| " + " | ".join(headers) + " |",
        "| " + " | ".join("---" for _ in headers) + " |",
    ]
    for row in rows:
        output.append("| " + " | ".join(str(cell) for cell in row) + " |")
    return "\n".join(output) + "\n"


def most_common(counter: collections.Counter, n: int = 10) -> str:
    if not counter:
        return "_No repeated cues detected._"
    return ", ".join(f"{item} ({count})" for item, count in counter.most_common(n))


def median_or_zero(values: Sequence[int]) -> int:
    if not values:
        return 0
    return int(statistics.median(values))


def aggregate_section_presence(papers: Sequence[PaperAnalysis]) -> collections.Counter:
    counter: collections.Counter = collections.Counter()
    for paper in papers:
        for section in paper.sections:
            counter[section] += 1
    return counter


def aggregate_sequences(papers: Sequence[PaperAnalysis]) -> Dict[str, collections.Counter]:
    section_counters: Dict[str, collections.Counter] = {
        section: collections.Counter() for section in SECTION_ORDER
    }
    for paper in papers:
        for section, labels in paper.label_sequences.items():
            if labels:
                section_counters.setdefault(section, collections.Counter())[tuple(labels)] += 1
    return section_counters


def aggregate_position_labels(
    papers: Sequence[PaperAnalysis], section: str, max_positions: int = 6
) -> List[Tuple[int, str, int]]:
    positions: List[collections.Counter] = [collections.Counter() for _ in range(max_positions)]
    for paper in papers:
        labels = paper.label_sequences.get(section, [])
        for index, label in enumerate(labels[:max_positions]):
            positions[index][label] += 1
    rows = []
    for index, counter in enumerate(positions, start=1):
        if counter:
            label, count = counter.most_common(1)[0]
            rows.append((index, label, count))
    return rows


def aggregate_captions(
    papers: Sequence[PaperAnalysis], kind: str
) -> Tuple[int, collections.Counter]:
    captions: List[str] = []
    for paper in papers:
        captions.extend(paper.figure_captions if kind == "figure" else paper.table_captions)
    words = keyword_counts(" ".join(captions))
    return len(captions), words


def build_style_guide(
    papers: Sequence[PaperAnalysis],
    failures: Sequence[Tuple[Path, str]],
    pdf_dir: Path,
) -> str:
    section_presence = aggregate_section_presence(papers)
    all_keywords = collections.Counter()
    transitions = collections.Counter()
    contributions = collections.Counter()
    problems = collections.Counter()
    experiments = collections.Counter()
    for paper in papers:
        all_keywords.update(paper.keyword_counts)
        transitions.update(paper.transition_counts)
        contributions.update(paper.contribution_counts)
        problems.update(paper.problem_counts)
        experiments.update(paper.experiment_counts)

    avg_words = int(statistics.mean([paper.word_count for paper in papers])) if papers else 0
    median_sentences = median_or_zero([paper.sentence_count for paper in papers])
    top_terms = ", ".join(term for term, _ in all_keywords.most_common(18))

    rows = []
    for paper in papers:
        present = ", ".join(SECTION_DISPLAY[s] for s in SECTION_ORDER if s in paper.sections)
        rows.append(
            [
                paper.title,
                paper.word_count,
                len(paper.figure_captions),
                len(paper.table_captions),
                present or "not detected",
            ]
        )

    failure_rows = [[failure_path.name, reason] for failure_path, reason in failures]

    return f"""# 802 Lab Paper Style Guide

Generated from the local PDF corpus in `{pdf_dir}`.

## Corpus Summary

- Successfully analyzed PDFs: {len(papers)}
- Skipped PDFs: {len(failures)}
- Average extracted paper length: {avg_words} words
- Median extracted sentence count: {median_sentences}
- Dominant technical vocabulary: {top_terms or "not enough text extracted"}

{md_table(["Paper", "Words", "Figures", "Tables", "Detected sections"], rows)}

## Extraction Log

{md_table(["Skipped PDF", "Reason"], failure_rows) if failures else "_No PDFs were skipped._\n"}

## Core Style Conclusions

1. The corpus is application-driven and systems-oriented: papers usually start from autonomous driving, traffic control, cooperative driving, scenario engineering, or vehicle stability problems before narrowing to a concrete modeling or testing gap.
2. The preferred argument shape is problem-first: establish a safety, efficiency, generalization, data, or robustness issue; explain why existing methods are insufficient; then introduce a named framework, model, sampling strategy, or control method.
3. Method writing tends to combine formal problem definition with an engineering pipeline. The common rhythm is definition, framework overview, module mechanism, objective or algorithm, then implementation detail.
4. Experimental writing is comparative and diagnostic. Strong sections connect simulation or dataset settings, baselines, metrics, main comparisons, ablations or sensitivity checks, and scenario/case visualization.
5. The tone is technical, direct, and evidence-led. Active claims such as "we propose/design/develop" are common for contributions, while result claims are usually tied to measured improvements, robustness, or scenario-level behavior.
6. Figures and tables are used as argument anchors: framework diagrams, scenario illustrations, comparative result tables, and ablation summaries often carry the main evidence chain.

## Frequent Cues

- Transition cues: {most_common(transitions, 12)}
- Contribution cues: {most_common(contributions, 12)}
- Problem cues: {most_common(problems, 12)}
- Experiment-analysis cues: {most_common(experiments, 12)}

## Section Coverage

{md_table(["Section", "Detected papers"], [[SECTION_DISPLAY.get(k, k), v] for k, v in section_presence.most_common()])}
"""


def build_section_patterns(papers: Sequence[PaperAnalysis]) -> str:
    sequence_counters = aggregate_sequences(papers)
    parts = [
        "# Section Patterns",
        "",
        "Use these patterns as organization guidance. They are abstractions from the corpus, not source-paper text.",
        "",
    ]
    for section in SECTION_ORDER:
        counter = sequence_counters.get(section, collections.Counter())
        section_lengths = [
            paper.section_word_counts[section]
            for paper in papers
            if section in paper.section_word_counts
        ]
        parts.append(f"## {SECTION_DISPLAY[section]}")
        parts.append("")
        parts.append(f"- Papers with detected section: {len(section_lengths)}")
        parts.append(f"- Median extracted length: {median_or_zero(section_lengths)} words")
        if counter:
            sequence_rows = []
            for labels, count in counter.most_common(5):
                sequence_rows.append([" -> ".join(labels), count])
            parts.append("")
            parts.append(md_table(["Common move sequence", "Papers"], sequence_rows))
        position_rows = aggregate_position_labels(papers, section)
        if position_rows:
            parts.append("")
            parts.append(md_table(["Move position", "Most common move", "Papers"], position_rows))
        parts.append(section_guidance(section))
        parts.append("")
    return "\n".join(parts).strip() + "\n"


def section_guidance(section: str) -> str:
    guidance = {
        "abstract": [
            "Prefer the order: background -> problem -> gap -> method -> result -> contribution.",
            "Keep the method name and target task visible before the result claim.",
            "Use one compact result sentence; avoid listing every metric unless the number is central.",
        ],
        "introduction": [
            "Prefer the order: field background -> limitations of existing work -> core idea -> contribution list.",
            "End with concrete contributions rather than a generic paper-organization paragraph.",
            "Move from real-world safety/efficiency need to technical gap before introducing the method.",
        ],
        "related_work": [
            "Group prior work by methodological family or application setting, not by author chronology.",
            "End each group with a short limitation that motivates the current paper.",
            "Keep comparisons fair and specific; avoid dismissive language.",
        ],
        "method": [
            "Prefer the order: problem definition -> overall framework -> module details -> training or optimization objective -> implementation or complexity notes.",
            "Introduce notation only when it is reused in equations, algorithms, or experiments.",
            "Tie each module back to the gap identified in the introduction.",
        ],
        "experiments": [
            "Prefer the order: setup -> metrics -> baselines -> main results -> ablation -> visualization -> discussion.",
            "Make each table or figure answer one research question.",
            "Explain why a metric or scenario matters before interpreting the numbers.",
        ],
        "conclusion": [
            "Restate the problem and method in one sentence, then summarize the strongest evidence.",
            "Mention limitations or future work only after the demonstrated contribution is clear.",
            "Keep the ending concise and avoid introducing new technical components.",
        ],
    }
    return "\n".join(f"- {item}" for item in guidance[section])


def build_phrase_patterns(papers: Sequence[PaperAnalysis]) -> str:
    transitions = collections.Counter()
    contributions = collections.Counter()
    problems = collections.Counter()
    experiments = collections.Counter()
    for paper in papers:
        transitions.update(paper.transition_counts)
        contributions.update(paper.contribution_counts)
        problems.update(paper.problem_counts)
        experiments.update(paper.experiment_counts)

    return f"""# Phrase Patterns

These are short generalized templates and cue inventories. Do not copy sentences from the source PDFs.

## Transition Cues

- Most frequent cues: {most_common(transitions, 14)}
- Use contrast cues to pivot from prior work to the target gap.
- Use additive cues to introduce modules, experimental settings, or additional evidence.
- Use causal cues only when the causal relation is explicit in the method or result.

## Problem Statement Templates

- "However, existing [methods/systems] often struggle with [specific condition]."
- "[Task] remains challenging because [technical cause] and [practical constraint] interact."
- "Although [prior direction] improves [aspect], it usually overlooks [missing factor]."
- "A key obstacle is to [goal] while maintaining [constraint]."

Observed problem cues: {most_common(problems, 12)}

## Contribution Templates

- "We propose [method name], a [framework/model/strategy] for [task]."
- "The main contributions are threefold: [formulation], [method], and [validation]."
- "To address [gap], we design [module] that [mechanism]."
- "We further develop [training/testing component] to improve [property]."

Observed contribution cues: {most_common(contributions, 12)}

## Experiment Analysis Templates

- "The results show that [method] consistently improves [metric] under [scenario]."
- "Compared with [baseline family], [method] achieves better [performance] because [mechanism]."
- "The ablation study verifies that [module] contributes most to [effect]."
- "The visualization indicates that [behavior] is aligned with [intended mechanism]."

Observed experiment cues: {most_common(experiments, 12)}

## Tone Rules

- Prefer precise verbs: formulate, design, sample, control, predict, evaluate, validate.
- Use cautious claims when evidence is indirect: suggest, indicate, imply.
- Use strong claims only when backed by a table, figure, statistical result, or ablation.
- Keep novelty claims tied to the actual technical difference.
"""


def build_figure_table_writing(papers: Sequence[PaperAnalysis]) -> str:
    figure_count, figure_terms = aggregate_captions(papers, "figure")
    table_count, table_terms = aggregate_captions(papers, "table")
    return f"""# Figure And Table Writing

## Caption Corpus Signals

- Detected figure captions: {figure_count}
- Detected table captions: {table_count}
- Frequent figure-caption terms: {most_common(figure_terms, 14)}
- Frequent table-caption terms: {most_common(table_terms, 14)}

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
"""


def build_experiment_writing(papers: Sequence[PaperAnalysis]) -> str:
    sequences = aggregate_sequences(papers).get("experiments", collections.Counter())
    sequence_rows = [
        [" -> ".join(labels), count] for labels, count in sequences.most_common(8)
    ]
    experiment_lengths = [
        paper.section_word_counts["experiments"]
        for paper in papers
        if "experiments" in paper.section_word_counts
    ]
    experiment_cues = collections.Counter()
    for paper in papers:
        experiment_cues.update(paper.experiment_counts)

    return f"""# Experiment Writing

## Corpus Signals

- Papers with detected experiment/evaluation sections: {len(experiment_lengths)}
- Median extracted experiment-section length: {median_or_zero(experiment_lengths)} words
- Frequent experiment-analysis cues: {most_common(experiment_cues, 14)}

{md_table(["Common experiment move sequence", "Papers"], sequence_rows)}

## Default Experiment Section Order

1. Settings: dataset, simulator, scenario source, split, hardware, or training details.
2. Metrics: define what each metric measures and why it matters.
3. Baselines: group baselines by family and state fairness conditions.
4. Main results: make one table or figure carry the central claim.
5. Ablation: isolate modules, losses, data choices, or sampling strategies.
6. Visualization/case study: show behavior in concrete scenarios.
7. Discussion: explain failure cases, robustness, efficiency, or limitations.

## Analysis Style

- Interpret numbers through mechanism, not only rank.
- State whether gains are consistent, scenario-specific, or metric-specific.
- Link ablation changes back to modules described in the method.
- Use cautious language for small or mixed gains.
- Mention practical significance when the metric maps to safety, stability, efficiency, or data cost.
"""


def build_checklist() -> str:
    return """# Writing Checklist

Use this before returning any draft or revision produced with the 802-paper-writing skill.

## Scope

- Identify the requested section: abstract, introduction, related work, method, experiments, conclusion, highlights, cover letter, or reviewer response.
- Read `references/lab_style_guide.md` first.
- Read the most relevant section reference before drafting.

## Style And Originality

- Do not copy source-paper sentences.
- Follow the lab's organization patterns, argument order, and technical tone.
- Make each novelty claim specific to the user's actual method and evidence.
- Avoid unsupported superlatives such as "first", "best", or "significant" unless evidence is supplied.
- Keep claims proportional to the provided experiments.

## Section-Specific Checks

- Abstract follows background -> problem -> gap -> method -> result -> contribution.
- Introduction follows field background -> existing-method limitations -> core idea -> contribution list.
- Method follows problem definition -> overall framework -> module details -> objective/training -> implementation or complexity details.
- Experiments follow settings -> metrics -> baselines -> main results -> ablation -> visualization -> discussion.
- Reviewer response is polite, specific, acknowledges reasonable concerns, and states exact manuscript changes or planned locations.

## Output Quality

- Preserve technical terms, variables, dataset names, and metric names supplied by the user.
- Flag missing evidence instead of inventing results.
- For revisions, keep the user's intended meaning unless explicitly asked to rewrite freely.
- For reviewer responses, separate response text from manuscript-change text when helpful.
"""


def write_outputs(
    output_dir: Path,
    papers: Sequence[PaperAnalysis],
    failures: Sequence[Tuple[Path, str]],
    pdf_dir: Path,
) -> None:
    output_dir.mkdir(parents=True, exist_ok=True)
    files = {
        "lab_style_guide.md": build_style_guide(papers, failures, pdf_dir),
        "section_patterns.md": build_section_patterns(papers),
        "phrase_patterns.md": build_phrase_patterns(papers),
        "figure_table_writing.md": build_figure_table_writing(papers),
        "experiment_writing.md": build_experiment_writing(papers),
        "checklist.md": build_checklist(),
    }
    for filename, content in files.items():
        (output_dir / filename).write_text(content, encoding="utf-8", newline="\n")


def parse_args(argv: Optional[Sequence[str]] = None) -> argparse.Namespace:
    parser = argparse.ArgumentParser(
        description="Analyze local PDF papers and generate 802 paper-writing references."
    )
    parser.add_argument("--pdf-dir", default="pdf", help="Directory containing PDF files.")
    parser.add_argument(
        "--output-dir",
        default=None,
        help="Output directory for generated markdown references.",
    )
    parser.add_argument(
        "--focus-aic",
        action="store_true",
        help="Generate deep Abstract/Introduction/Conclusion analysis references.",
    )
    return parser.parse_args(argv)


def default_output_dir() -> Path:
    return Path(__file__).resolve().parents[1] / "references"


def main(argv: Optional[Sequence[str]] = None) -> int:
    args = parse_args(argv)
    pdf_dir = Path(args.pdf_dir).resolve()
    output_dir = Path(args.output_dir).resolve() if args.output_dir else default_output_dir()

    if not pdf_dir.exists() or not pdf_dir.is_dir():
        print(f"PDF directory not found: {pdf_dir}", file=sys.stderr)
        return 2

    pdfs = sorted(pdf_dir.glob("*.pdf"))
    if not pdfs:
        print(f"No PDF files found in: {pdf_dir}", file=sys.stderr)
        return 2

    if args.focus_aic:
        records: List[AICPaperRecord] = []
        for pdf_path in pdfs:
            record = analyze_aic_paper(pdf_path)
            records.append(record)
            found = [
                name
                for name in AIC_SECTION_ORDER
                if record.sections[name].found
            ]
            suspicious = sum(
                1
                for name in AIC_SECTION_ORDER
                if record.sections[name].suspicious
            )
            if record.extraction_error:
                print(f"[warn] {pdf_path.name}: {record.extraction_error}")
            print(
                f"[aic] {pdf_path.name}: found={','.join(found) or 'none'}, "
                f"suspicious_sections={suspicious}, extractor={record.extractor}"
            )

        write_aic_outputs(output_dir, records)
        fully_detected = sum(
            1
            for record in records
            if all(record.sections[name].found for name in AIC_SECTION_ORDER)
        )
        print(
            f"\nAIC analyzed {len(records)} PDFs; "
            f"all three AIC sections detected in {fully_detected} PDFs."
        )
        print(f"Wrote AIC markdown references to: {output_dir}")
        return 0

    papers: List[PaperAnalysis] = []
    failures: List[Tuple[Path, str]] = []
    for pdf_path in pdfs:
        analysis, error = analyze_paper(pdf_path)
        if analysis is None:
            failures.append((pdf_path, error or "Unknown extraction failure"))
            print(f"[skip] {pdf_path.name}: {failures[-1][1]}")
            continue
        papers.append(analysis)
        print(
            f"[ok] {pdf_path.name}: {analysis.word_count} words, "
            f"{len(analysis.sections)} sections, extractor={analysis.extractor}"
        )

    if not papers:
        print("No PDFs produced enough text for analysis.", file=sys.stderr)
        return 1

    write_outputs(output_dir, papers, failures, pdf_dir)
    print(f"\nAnalyzed {len(papers)} PDFs; skipped {len(failures)} PDFs.")
    print(f"Wrote markdown references to: {output_dir}")
    return 0


if __name__ == "__main__":
    raise SystemExit(main())

````

---

## SKILL.md

````markdown
---
name: 802-paper-writing
description: Use when writing, revising, polishing, or structurally improving academic papers in the 802 lab style, especially for high-standard abstract, introduction, conclusion, related work, method, experiments, highlights, cover letter, and reviewer response tasks that should reflect patterns from the lab's existing and in-progress papers. Also use for advisor-strict paper revision when the user asks for strict checking, higher persuasiveness, logic diagnosis, or not merely polishing language.
---

# 802 Paper Writing

## Workflow

1. Determine the user's target output before writing: abstract, introduction, related work, method, experiments, conclusion, highlights, cover letter, reviewer response, or a full-paper revision.
2. For Abstract, Introduction, or Conclusion tasks, read the AIC references first:
   - `references/aic_style_guide.md`
   - The corresponding deep pattern file: `references/abstract_deep_patterns.md`, `references/introduction_deep_patterns.md`, or `references/conclusion_deep_patterns.md`
   - `references/aic_revision_checklist.md`
   - `references/aic_common_weaknesses.md` when revising weak or advisor-sensitive text
   - `references/advisor_strict_examples.md` when Advisor-Strict Mode is requested or the expected output style is unclear
3. For other paper sections, read `references/lab_style_guide.md` first. Then read the most relevant reference:
   - `references/section_patterns.md` for section organization.
   - `references/phrase_patterns.md` for short rhetorical templates and transition patterns.
   - `references/figure_table_writing.md` for captions, figure callouts, and table interpretation.
   - `references/experiment_writing.md` for evaluation sections, result analysis, ablations, and discussions.
   - `references/checklist.md` before final output.
4. Imitate the lab papers' organization, argument order, and academic tone, but do not copy source-paper sentences.
5. Preserve the user's technical content. If key evidence is missing, flag the gap instead of inventing results, datasets, numbers, baselines, or reviewer-requested changes.
6. Before returning, check the draft against `references/checklist.md` or `references/aic_revision_checklist.md`.

## Section Defaults

- Abstract: write in the order background -> specific problem -> existing insufficiency -> method -> key mechanism -> experimental result -> contribution/meaning. Check that all seven roles are present or explain what evidence is missing.
- Introduction: write in the order field background -> concrete challenge -> existing-method families -> shared gap -> core idea -> method overview -> contribution list. Check that the first paragraph is not too broad, the challenge is concrete, the gap is explicit, the method appears naturally, and contributions map to the gap.
- Related work: group prior work by theme or method family; end each group with the limitation that motivates the current paper.
- Method: prefer problem definition -> overall framework -> module details -> training/optimization objective -> complexity or implementation details.
- Experiments: prefer setup -> metrics -> baselines -> main results -> ablation -> visualization -> discussion.
- Conclusion: return to the research problem, summarize the method, synthesize the main evidence, state meaning without exaggeration, then mention limitations or future work only in a restrained and specific way.
- Highlights: make each bullet a compact claim about problem, method, evidence, or contribution; avoid hype.
- Cover letter: explain fit, novelty, evidence, and why the manuscript matters to the venue.
- Reviewer response: be polite and specific; acknowledge reasonable concerns; explain the revision and, when possible, identify where it was made in the manuscript.

## AIC Revision Workflow

When the user asks to revise an abstract, introduction, or conclusion, follow this order:

1. Identify the target venue, paper task, and section type if available.
2. Extract the current text's research problem, existing insufficiency, method, experimental evidence, and contribution.
3. Compare the text against `references/aic_revision_checklist.md` and identify missing logic roles.
4. Give a brief diagnosis first when the logic is weak. Do not only polish language.
5. Provide the revised version.
6. Briefly explain what the revision strengthens: problem specificity, gap clarity, method identity, evidence, contribution, or restrained significance.

## Advisor-Strict Mode

Enable Advisor-Strict Mode when the user says or implies: "老师要求高", "严格检查", "不要只润色", "提高说服力", advisor-level revision, strict logic review, or similar.

In Advisor-Strict Mode, use this fixed output order:

1. Logic diagnosis.
2. Fatal / major / minor problems.
3. Missing information that cannot be invented.
4. Revised version.
5. What was strengthened.

In this mode, diagnose structure before language. Treat missing research problem, unclear gap, unrecognizable method, unsupported results, missing contribution/implication, or Abstract-like Conclusion as higher priority than fluency.

Language polishing is forbidden before logic diagnosis. If the argument is weak, rewrite the logic before polishing sentences.

## AIC Guardrails

- Do not copy sentences from PDFs.
- Do not use empty academic formulas merely to imitate style.
- Do not make contribution or result claims stronger than the user's supplied evidence.
- If the user's draft has a structural problem, point it out before rewriting.
- Treat automatic AIC statistics as heuristic. Low-confidence extraction records are audit evidence only; use the checklist and the user's manuscript content as the authority.
- For Abstracts, never omit method identity and experimental evidence unless the user has not provided them; in that case, mark the missing information.
- For Introductions, make the contribution list correspond to the gap and method, not just a list of features.
- For Conclusions, avoid writing a compressed Abstract; add synthesis about what the evidence supports.

## Corpus Analysis Script

Use `scripts/analyze_paper_corpus.py` to refresh the reference files from local PDFs:

```bash
python scripts/analyze_paper_corpus.py --pdf-dir pdf
python scripts/analyze_paper_corpus.py --pdf-dir pdf --focus-aic
```

The script writes markdown summaries to `references/`. It skips PDFs with insufficient extractable text and records skipped files in `references/lab_style_guide.md`. The generated references should summarize structure, style, and short phrase patterns only; they must not contain long copied passages from the original papers.

````
