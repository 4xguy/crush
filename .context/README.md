# .context workspace

Use this folder for local prompts, scratch notes, and agent configs specific to our fork. Do not store secrets; prefer env vars or a local keychain.

Suggested layout:
- `notes.md` for quick findings.
- `sessions/` for per-task context files.
- `snippets/` for reusable command snippets.

Branch policy:
- `.context` exists only on `custom/main` (and its feature branches) so it never enters upstream sync PRs.
- Stay on `custom/main` when editing here; changes will be ignored on `main`/upstream.

Reminder: keep keys out of this folder—use environment variables or a local secrets manager instead.
