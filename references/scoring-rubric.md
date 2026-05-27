# Scoring Rubric

Use scores to make recommendations comparable, not mathematically absolute.

## Score Categories

Total: 100 points.

| Category | Points | Evidence |
| --- | ---: | --- |
| Fit | 35 | Matches user need, supported use cases, API shape, docs/examples, project scope |
| Maintenance/support | 25 | Recent commits/releases, issue response, PR activity, maintainer presence |
| Adoption/community | 15 | Stars, forks, watchers, contributors, dependents, downloads, topic visibility, popularity integrity |
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
- High star count with weak engagement signals, such as very low fork-to-star ratio, very low watcher-to-star ratio, few dependents, shallow contributor activity, or many low-activity stargazer accounts.

## Popularity Integrity

Treat stars as weak evidence until engagement agrees. For high-star repos, fast-growing repos, AI/agent repos, crypto-adjacent repos, or user-visible "trending" claims, Challenger should check whether popularity looks organic.

Use these first-pass heuristics:

- Fork-to-star ratio below `0.05` on a repo with more than `10,000` stars warrants scrutiny unless the repo type naturally discourages forks, such as an educational list or static reference.
- Watcher-to-star ratio far below similar projects is a warning sign, especially when paired with a low fork-to-star ratio.
- Package downloads are easy to inflate; prefer dependents, real downstream usage, issues from production users, and recurring contributors.
- A stargazer sample with many zero-repo, zero-follower, no-bio accounts should reduce adoption confidence.
- Sudden star growth without matching forks, contributors, issues, releases, package dependents, or community discussion should be treated as a vanity-metric risk.

When these signals appear, do not necessarily disqualify the repo. Downgrade adoption/community points, add a hard warning, and explain what evidence would clear the concern.

## Challenger Adjustments

Challenger does not need to rescore every candidate from scratch. Prefer adjustments:

```text
Scout score: 86
Challenger adjustment: -12
Reason: stale releases, weak issue response, unclear license
Final score: 74
```

Do not invent precision. If evidence is thin, use a score band and lower confidence.
