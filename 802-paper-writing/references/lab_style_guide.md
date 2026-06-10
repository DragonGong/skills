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
