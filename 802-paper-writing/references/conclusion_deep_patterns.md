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
