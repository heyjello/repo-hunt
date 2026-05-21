# Scoring Rubric

Use scores to make recommendations comparable, not mathematically absolute.

## Score Categories

Total: 100 points.

| Category | Points | Evidence |
| --- | ---: | --- |
| Fit | 35 | Matches user need, supported use cases, API shape, docs/examples, project scope |
| Maintenance/support | 25 | Recent commits/releases, issue response, PR activity, maintainer presence |
| Adoption/community | 15 | Stars, forks, contributors, dependents, downloads, topic visibility |
| Project quality | 15 | Docs, tests, CI, examples, security posture, release process, license file |
| External validation | 10 | Mentions from credible users, HN/Reddit/blogs, ecosystem reputation |

## Score Bands

- 90-100: exceptional default pick.
- 75-89: strong recommendation.
- 60-74: usable with caveats.
- Below 60: not recommended unless the niche has weak alternatives.

## License Handling

License is a warning or gate, not part of the default 100-point score.

- `warn`: report license and risks without filtering.
- `commercial-friendly`: prefer permissive options when close.
- `permissive`: strongly favor permissive licenses.
- `strict`: exclude license mismatches and unknown licenses.

Always distinguish "GitHub detected license" from "license manually inferred from repo contents." Do not provide legal advice.

## Hard Warnings

Surface these even when the numeric score is high:

- Archived repository.
- No meaningful commit or release activity for years.
- Unknown or missing license.
- Copyleft, source-available, commercial, or custom license when company use matters.
- High unresolved issue backlog with little maintainer response.
- README-only, demo-only, or "awesome list" repo when the user needs a usable package.
- Single maintainer with no recent activity for critical infrastructure.

## Challenger Adjustments

Challenger does not need to rescore every candidate from scratch. Prefer adjustments:

```text
Scout score: 86
Challenger adjustment: -12
Reason: stale releases, weak issue response, unclear license
Final score: 74
```

Do not invent precision. If evidence is thin, use a score band and lower confidence.
