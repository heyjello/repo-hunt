# Portability

Repo Hunt is skill-first and tool-agnostic. The selected model does the reasoning; the skill provides the process, rubric, and output contract.

## Subagent Support

When subagents or parallel agents are available:

- Use separate contexts for Scout, Challenger, and Curator in deep mode.
- Pass Scout output to Challenger.
- Pass Scout and Challenger output to Curator.

When subagents are unavailable:

- Run the same roles sequentially in one conversation.
- Label each phase.
- Keep intermediate outputs concise.

## Codex

Use the installed skill directly when available. In deep mode, use subagents only when the user or environment permits them. Otherwise run the three roles sequentially.

## Claude Code

Install as an Agent Skill. Invoke with `/repo-hunt` or natural language that matches the skill description. Use Task/subagent-style workflows in deep mode when available.

## Cursor

Use the main `SKILL.md` instructions as a project rule or paste them into the active Cursor context. If Cursor does not expose subagents, run Scout, Challenger, and Curator sequentially in the active chat.

## Minimal Fallback

If no web search is available, say so, then use available GitHub context, package metadata, or user-provided candidates. Lower confidence and ask for permission before making a high-stakes recommendation.
