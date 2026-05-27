# Search Playbook

Search for fit first, then support.

## Query Expansion

Create 3-5 query variants from the user request:

- Direct phrase: "React data table library"
- Domain terms: "grid", "table", "datatable"
- Package terms: "component", "framework", "SDK", "CLI"
- Problem terms: "local-first sync", "offline database"
- Known ecosystem terms inferred from the prompt

Do not ask the user for language or ecosystem when it is clear from the query.

## GitHub Search

Use GitHub repository search when available. Useful qualifiers:

```text
archived:false
stars:>50
pushed:>YYYY-MM-DD
license:mit
license:apache-2.0
topic:<topic>
```

Use qualifiers as hints, not blind filters, unless the user requested strict license handling.

## Candidate Gathering

Fast mode target:

- 10-20 candidates found.
- 5 candidates shortlisted.
- 3 finalists.

Deep mode target:

- 20-40 candidates found.
- 8-10 candidates shortlisted.
- 3 finalists plus honorable mentions.

## Evidence Sources

Prefer:

- GitHub repo metadata.
- README and official docs.
- Release notes and tags.
- Issues and pull requests.
- Package registry pages.
- Official examples.
- Credible community discussion.
- Fork, watcher, contributor, dependent, and download signals that corroborate stars.

Be cautious with:

- Old blog posts.
- Star-only rankings.
- Sponsored lists.
- AI-generated package directories.
- Repos with many stars but no install path.
- Fast-growing or high-star repos whose forks, watchers, dependents, and contributor activity do not support the star count.
- Package download counts without dependents or real usage evidence.

## Popularity Trap Check

Before finalizing, search for alternatives to the obvious winner. Include "rejected popular options" when a highly visible repo loses due to fit, staleness, license, quality risk, or suspicious popularity signals.

For any candidate whose apparent strength is mostly stars, collect enough corroborating evidence to answer:

- Are forks and watchers proportionate to similar healthy projects?
- Are there real contributors beyond the maintainers?
- Are there production-looking issues, discussions, or support requests?
- Does the package have dependents or credible downstream users?
- If stargazer profiles are sampled, do they look like real developers rather than empty accounts?

If these checks are unavailable, lower confidence instead of treating stars as proven adoption.
