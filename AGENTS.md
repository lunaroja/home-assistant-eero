<!-- second-brain-repository-bootstrap:v1 -->

# Repository agent guide

This repository extends Abraham's canonical agent contract at
`/Users/abraham/src/second-brain/AGENTS.md`. Repository-specific instructions
below add to that contract; they do not replace it.

## Required task-start synchronization

Before substantive work or a substantive response in a new task:

1. Run `.codex/bin/repository-preflight` from anywhere inside this repository.
2. If it reports a dirty, detached, untracked, or diverged checkout, preserve
   the existing work and report the exact synchronization blocker. Never reset,
   clean, force, or overwrite work to make the preflight pass.
3. After a successful pull, read the current Second Brain `AGENTS.md`, then this
   file, before acting. Start a new task if pulled instruction changes must be
   loaded by the runtime immediately.

The preflight verifies the global Second Brain link and performs only
fast-forward pulls for clean checkouts with tracking branches.

## Repository-specific instructions

Add this repository's purpose, validation commands, deployment workflow,
privacy boundaries, and source-of-truth rules here as they become known. Keep
cross-project identity, preferences, credentials, and delivery policy in Second
Brain.

## Purpose and contribution workflow

This is a contribution fork of `schmittx/home-assistant-eero`. It owns reusable
integration changes and synthetic regression tests. Household configuration,
credentials, device inventories and operational evidence belong in the private
Home Assistant configuration repository and must never enter this public fork.

- Fetch both remotes before work. `upstream/main` is the contribution base.
- Fork `main` carries this local bootstrap only. Prepare contributions on scoped
  `codex/` branches from current `upstream/main` and submit upstream pull requests.
  Do not include AGENTS.md or `.codex/` scaffolding in those pull requests.
- The original user authorization covers the startup-retry fix and regression
  tests. Migration changes and unrelated contributions require separate approval.
- Do not deploy a contribution to a live Home Assistant instance as part of a
  PR-only request. Public tests use synthetic accounts and isolated HA storage.
- Use Python's unittest runner and real Home Assistant coordinators/config-entry
  lifecycle with mocked provider/platform boundaries. Test minimum supported HA
  2025.2.0 and a current version when practical. Preserve intentionally empty
  network selection and cached-account behavior after a successful update.
- Finish on clean synchronized fork main after pushing the contribution branch.
  On a contribution branch, read this guide with `git show origin/main:AGENTS.md`.
