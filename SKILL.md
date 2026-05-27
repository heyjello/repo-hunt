---
name: repo-hunt
description: Use when searching for GitHub repositories, libraries, packages, frameworks, developer tools, or open-source projects and needing ranked recommendations based on fit, maintenance, adoption, quality, sentiment, and license risk.
---

# Repo Hunt

Repo Hunt finds well-supported repositories by evidence, not stars alone. It uses a Scout -> Challenger -> Curator review chain and defaults to fast, token-conscious research.

## Invocation

Use:

```text
/repo-hunt <query> [--depth fast|deep] [--license warn|commercial-friendly|permissive|strict]
```

Defaults:

```text
--depth fast
--license warn
```

Do not require language or ecosystem flags. Infer constraints from the query, such as "Python CLI framework" or "React table library".

## Reference Files

- Use [references/search-playbook.md](references/search-playbook.md) for search strategy and candidate gathering.
- Use [references/scoring-rubric.md](references/scoring-rubric.md) before ranking finalists.
- Use [references/output-format.md](references/output-format.md) for final answer shape.
- Use [references/portability.md](references/portability.md) when adapting to Codex, Claude Code, Cursor, or environments without subagents.

## Workflow

1. Parse the query and optional flags.
2. Run Scout to gather candidates and produce an initial shortlist.
3. Run Challenger to pressure-test the shortlist and search for missed alternatives.
4. Run Curator to reconcile Scout and Challenger findings into the final ranked output.
5. Include rejected popular options when relevant.

## Roles

### Scout

Find 10-20 candidate repositories using GitHub search, GitHub topics, package registries when relevant, and web search when available. Prefer official repo metadata, README, release notes, issue/PR activity, docs, and package pages over summaries.

Scout output: candidate list, initial top 5, search terms used, and one-line evidence for each candidate.

### Challenger

Receive Scout's shortlist. Look for reasons the ranking may be wrong: stale maintenance, weak fit, license risk, poor documentation, unresolved issues, fragile governance, abandoned releases, suspicious popularity signals, overhyped star counts, or stronger missed alternatives.

Challenger output: objections, risk flags, suggested score adjustments, and any replacement candidates.

### Curator

Receive Scout and Challenger outputs. Verify the top candidates, apply the scoring rubric, and produce the final answer. Prefer useful tradeoffs over a single absolute winner when use cases differ.

Curator output: top 3, honorable mentions, rejected popular options, warnings, confidence, and when to choose each.

## Depth Modes

Fast mode: run Scout, Challenger, and Curator sequentially in one model context. Keep the candidate set small and avoid broad sentiment research unless it is easy to obtain.

Deep mode: use separate agent contexts for Scout, Challenger, and Curator when the environment supports them. If subagents are unavailable, run the same roles sequentially and label each phase.

Automatically consider deep mode when the user asks for production, company, enterprise, high-confidence, thorough, exhaustive, or risky-decision research.

## License Modes

Default `--license warn`: do not filter by license, but always report license status and call out unknown, copyleft, source-available, commercial, or unclear licensing risk.

`--license commercial-friendly`: prefer permissive licenses and warn strongly on restrictions.

`--license permissive`: prefer MIT, Apache-2.0, BSD-2-Clause, BSD-3-Clause, ISC, and similarly permissive licenses.

`--license strict`: exclude candidates that do not satisfy the user's stated license requirement or whose license cannot be determined.

Never present license screening as legal advice. Recommend legal or compliance review for company adoption.

## Quality Bar

- Do not rank by stars alone.
- Every finalist needs evidence for fit, maintenance, adoption, quality, and license status.
- Treat stars as weak adoption evidence unless forks, watchers, contributors, dependents, or credible community usage corroborate them.
- Treat suspicious popularity as a risk signal, not an accusation, unless there is direct evidence of manipulation.
- Penalize archived, stale, undocumented, unlicensed, or abandoned projects even if popular.
- State uncertainty when data is thin or search tools are limited.
- Prefer current primary sources over stale articles or copied lists.
