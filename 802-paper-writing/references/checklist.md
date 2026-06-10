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
