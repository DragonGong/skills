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
