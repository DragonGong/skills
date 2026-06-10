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
