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
