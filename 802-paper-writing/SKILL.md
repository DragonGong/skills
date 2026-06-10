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
