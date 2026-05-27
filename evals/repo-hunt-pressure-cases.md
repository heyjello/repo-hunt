# Repo Hunt Pressure Cases

Use these prompts to validate that Repo Hunt guides agents toward stable, evidenced recommendations instead of popularity-only lists.

## Cross-Case Evaluation Checks

- Fails if it ranks a repository primarily by stars, downloads, or trending status.
- Passes only if high popularity is corroborated with forks, watchers, contributors, dependents, releases, production-looking issues, or credible community usage.
- Flags suspicious popularity as a risk signal without making unsupported fake-star accusations.
- Lowers confidence when popularity-integrity checks are unavailable.

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

## Case 6: Fake Popularity Signals

Prompt: `/repo-hunt choose the best agent framework. Candidate A has 80k stars, 900 forks, 90 watchers, few external dependents, and many stargazers with empty profiles. Candidate B has 14k stars, 3k forks, 600 watchers, active releases, production-looking issues, and many dependents.`

Expected behavior:
- Does not rank Candidate A first based on stars alone.
- Flags Candidate A's low fork-to-star and watcher-to-star ratios as suspicious popularity signals.
- Treats Candidate B's corroborating usage signals as stronger adoption evidence.
- Explains what additional evidence would be needed to clear Candidate A.

## Case 7: Inflated Package Metrics

Prompt: `/repo-hunt compare two npm packages for request validation. Package A has huge weekly downloads but almost no dependents, low GitHub issue activity, and little contributor activity. Package B has fewer downloads but many dependents, active maintainers, and production issue discussions.`

Expected behavior:
- Does not treat downloads alone as proof of adoption.
- Uses dependents, maintainer activity, production-looking issues, and release quality as stronger evidence.
- Calls out metric inflation risk without making an unsupported accusation.
- Keeps confidence proportional to the available evidence.
