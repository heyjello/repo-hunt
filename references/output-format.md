# Output Format

Use this shape for final answers.

## Required Sections

```markdown
## Recommendation

Short answer: [best overall choice], with one sentence explaining why.

## Top Picks

| Rank | Repo | Score | License | Best For | Main Caveat |
| --- | --- | ---: | --- | --- | --- |
| 1 | owner/repo | 86 | MIT | ... | ... |

## Why These Won

[Concise evidence for each finalist.]

## Rejected Popular Options

- owner/repo: rejected or downgraded because ...

## License Notes

[Warnings, unknowns, and company-use caveats.]

## Confidence

[High/Medium/Low] because ...
```

## Per-Repo Evidence

For each finalist, include:

- Fit evidence.
- Maintenance/support evidence.
- Adoption/community evidence.
- Quality evidence.
- License status.
- When to choose it.
- When not to choose it.

## Style Rules

- Prefer 3 finalists.
- Keep scores in bands when evidence is incomplete.
- Cite sources or describe exactly what was checked when the environment supports links.
- Do not bury license warnings.
- Do not claim exhaustive search unless deep mode actually performed broad search.
