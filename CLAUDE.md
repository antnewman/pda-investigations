# Claude Code: project instructions

This file gives Claude Code the standing instructions for working in this repository. It is loaded automatically when Claude Code runs in this directory.

## What this repo is

The umbrella repository for the PDA Investigations programme. This repo does not hold any single investigation; each case lives in its own repository, linked from [`cases/`](cases/). Work in this repo is almost always one of three things:

1. Adding a new case to the [`cases/`](cases/) index and to the table in [`README.md`](README.md).
2. Updating [`methodology-shared.md`](methodology-shared.md) to reflect a decision that applies across every case.
3. Administrative updates (`README.md`, `CITATION.cff`, licences, `.gitignore`).

If the change is case-specific, it belongs in the case repository, not here.

## Read these first

1. [`AGENT_CONTEXT.md`](AGENT_CONTEXT.md): shared working context and non-negotiable coding standards for all PDA Investigations work. British English, no em dashes, git identity `antnewman` / `antjsnewman@outlook.com`, feature branches only, append-only data model, no direct commits to `main`.
2. [`methodology-shared.md`](methodology-shared.md): the programme-level methodology. Anything that applies to every case lives here, not in a case repo.

## Do not

- Do not commit directly to `main`. Feature branches and pull requests only.
- Do not force-push or run destructive git operations.
- Do not commit secrets, `.env` files, or Supabase service-role keys.
- Do not modify `methodology-shared.md` for a case-specific reason; that change belongs in the case's own `methodology.md`.
- Do not use em dashes. Commas, semicolons, full stops, and hyphens cover every case.
- Do not add a new entry to `cases/` without a corresponding repository existing under `github.com/antnewman/`.

## When adding a case

A new case belongs in `cases/<case-repo-name>.md`. Follow the structure of the existing file in `cases/` (anchor, question, assumptions, external series, links).

When a case's status changes (for example, "In progress" to "Published"), update both the `cases/` file and the status column in `README.md`. Keep them in sync.

## Commit style

Conventional commits: `feat:`, `fix:`, `chore:`, `refactor:`, `docs:`. Descriptive subject line; body explains *why*. No Claude or AI co-author trailers; git identity is `antnewman` / `antjsnewman@outlook.com`.

## On stopping

Stop and ask before:

- Making a change to `methodology-shared.md` that would affect an in-progress case.
- Adding a dependency.
- Committing anything that contradicts `AGENT_CONTEXT.md`.
