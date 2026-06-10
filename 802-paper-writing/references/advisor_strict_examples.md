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
