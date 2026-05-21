# Repo Hunt Pressure Cases

Use these prompts to validate that Repo Hunt guides agents toward stable, evidenced recommendations instead of popularity-only lists.

## Case 1: Popularity Trap

Prompt: `/repo-hunt best React data table library`

Expected behavior:
- Searches beyond the highest-starred obvious choices.
- Includes at least one rejected popular option with a concrete reason.
- Scores fit, maintenance, adoption, quality, and external validation separately.
- Mentions license status without filtering by default.

## Case 2: Company License Warning

Prompt: `/repo-hunt best open-source auth service for a SaaS product --license commercial-friendly`

Expected behavior:
- Treats license as a prominent risk signal.
- Warns on unknown, copyleft, source-available, or paid/commercial restrictions.
- Does not provide legal advice.
- Prefers permissive options when tradeoffs are otherwise close.

## Case 3: Deep Adversarial Review

Prompt: `/repo-hunt local vector database for offline RAG --depth deep`

Expected behavior:
- Runs Scout, Challenger, and Curator as separate contexts when supported, otherwise sequentially.
- Challenger pressure-tests Scout's shortlist and can introduce better alternatives.
- Curator reconciles both views and gives a top 3 with confidence.

## Case 4: Natural Constraint Inference

Prompt: `/repo-hunt best Python CLI framework`

Expected behavior:
- Infers Python from the prompt without requiring a language flag.
- Searches GitHub and broader web signals when available.
- Avoids suggesting unrelated packages from other ecosystems.

## Case 5: Sparse Results

Prompt: `/repo-hunt niche tool for generating SPDX SBOM visual diffs`

Expected behavior:
- Reports low confidence when evidence is thin.
- Expands search terms rather than forcing weak matches.
- Separates usable candidates from honorable mentions and rejected options.
