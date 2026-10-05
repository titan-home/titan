# titan

TITAN product releases. Each TITAN version is a release here: one manifest
that pins the tested versions of every component, and the release notes for
the people who use and run TITAN.

Part of TITAN, a self-hosted personal AI assistant, planner and tracker. The
product, architecture and rules shared by every TITAN repository are in
[titan-shared](https://github.com/titan-home/titan-shared).

## Why a separate repository

The components release on their own: the backend (`titan-backend`), the web UI
(`titan-web`), the node controller (`titan-node`), and stock images such as
PostgreSQL, nginx and the embedding server. This repository answers the
one question none of them can answer alone: which versions work together.

## Contents

- **Release manifests**: for every TITAN version, each component that was
  tested together, described by three fields: its version, the commit of its
  source, and the digest of its image. The node controller updates a node to
  a manifest as a whole and rolls back to the previous one if the update
  fails.
- **Release notes**: what changed for users and for whoever runs a node,
  including upgrade steps and database migrations.
- **Compatibility**: which UI, API and controller versions work together.

## Status

Not started; the first release comes with the node controller (build-plan
stage 4). See the [build plan](https://github.com/titan-home/titan-shared/blob/master/docs/roadmap/plan.md).

## Getting the code

```sh
git clone https://github.com/titan-home/titan.git
```

## Licence

Released into the public domain under [the Unlicense](LICENSE).
