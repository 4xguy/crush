# .context workspace

Use this folder for local prompts, scratch notes, and agent configs specific to our fork. Do not store secrets; prefer env vars or a local keychain.

Suggested layout:
- `notes.md` for quick findings.
- `sessions/` for per-task context files.
- `snippets/` for reusable command snippets.

This directory is committed only on the `custom/main` line to avoid leaking into upstream-sync PRs.
