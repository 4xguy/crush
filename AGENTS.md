# Repository Guidelines

## Project Structure & Module Organization
- Entry: `main.go` runs the TUI/CLI. Go modules defined in `go.mod`.
- Core code lives in `internal/` (UI, shell, config, update, agent tooling). Look at `internal/tui`, `internal/shell`, `internal/agent`, `internal/config`.
- Task automation: `Taskfile.yaml`. Build settings: `crush.json`. Schemas in `schema.json`.
- Tests colocate with code using Go `_test.go` files; snapshot/fixture data lives beside tests.
- Scripts for CI helpers: `scripts/` (e.g., `run-labeler.sh`).

## Build, Test, and Development Commands
- Build binary: `go build .`
- Run app: `go run .`
- Full test suite: `task test` or `go test ./...`
- Update golden files: `go test ./... -update`
- Format & lint: `task fmt` (gofumpt + goimports) and `task lint:fix`
- Dev loop with profiling: `task dev`

## Coding Style & Naming Conventions
- Go formatting enforced via gofumpt/goimports; commit only formatted code.
- Imports ordered stdlib → external → internal.
- Naming: PascalCase for exported, camelCase for unexported; keep identifiers short and clear.
- Errors: return/wrap with `fmt.Errorf("context: %w", err)`; avoid panics in library paths.
- JSON tags use `snake_case`; file perms in octal (e.g., `0o755`).
- Comments start with capitals, end with periods; wrap around 78 columns.

## Testing Guidelines
- Framework: standard `testing` with `testify/require`.
- Prefer `t.Parallel()` when safe; use `t.TempDir()` and `t.Setenv()` for isolation.
- Name tests `TestThing_Subject`; add table-driven cases when possible.
- Regenerate goldens with `go test ./... -update` after intentional output changes.

## Commit & Pull Request Guidelines
- Use semantic commit prefixes (`feat:`, `fix:`, `chore:`, `docs:`, `refactor:`, `sec:`).
- Keep commits focused and single-line subjects when possible.
- PRs: include a short summary, links to issues/tasks, test evidence (`task test` output), and screenshots for UI changes.
- Keep your fork’s `custom/main` rebased on `upstream/main`; open feature branches from `custom/main`.

## Security & Configuration Tips
- Avoid committing secrets; sample env lives in `internal/agent/.env.sample`.
- Set `GITHUB_TOKEN`/provider keys via environment, not files.
- Enable `git config --global rerere.enabled true` to reuse conflict resolutions during regular upstream syncs.
