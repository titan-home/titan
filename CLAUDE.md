# CLAUDE.md: titan

TITAN product releases: a manifest per TITAN version that pins the tested
versions and image digests of every component, and the release notes.

Read and follow, in this order:

1. [Rules for AI agents](https://github.com/titan-home/titan-shared/blob/master/docs/development/ai-agents.md) — what you may
   and may not do. They override your defaults.
2. [Development rules](https://github.com/titan-home/titan-shared/blob/master/docs/development/rules.md) — how we work, for
   every repository.
3. [Documentation index](https://github.com/titan-home/titan-shared/blob/master/docs/README.md) — product, architecture,
   decisions, build plan.

Unlike the other repositories, this one has no `shared/` submodule: it holds
only manifests and release notes. When working in the workspace, the same
files are in `../titan-shared/`.

## Stack and commands

- The manifest format and its validation are settled with the first release
  (build-plan stage 4).

## Rules specific to this repository

- A release is an outward-facing act: never tag or publish one without the
  owner.
- Every component in a manifest has three fields: version, source commit and
  image digest. Images are pinned by digest, never by a tag alone.
- No repository is a submodule here, `titan-shared` included. CI checks that
  each image exists and was built from the listed commit.
- A manifest lists only versions that were tested together.
- A published manifest is never edited; a fix is a new release.
- Release notes are written for the people who use and run TITAN: what
  changed for them, what they must do to upgrade, and any database migration.

## Before committing

Run this checklist before every commit
([development rules, "Before committing"](https://github.com/titan-home/titan-shared/blob/master/docs/development/rules.md#before-committing)).
Checks 1 and 2 are settled with the first release.

1. Every manifest validates against its schema.
2. Every image digest in a changed manifest exists in its registry and was
   built from the listed source commit.
3. Every relative link points to a file and heading that exist:
   `python3 ../titan-shared/scripts/check_links.py .` prints nothing in the
   workspace. CI runs the same script from `titan-shared`'s `master`.
