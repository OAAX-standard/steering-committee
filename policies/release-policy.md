# OAAX Release Policy

**Status: proposed.** Applies from OAAX 2.0, pending ratification by the TSC (next meeting, moved back from 2026-11-03, date to be confirmed).
Drafted with AI assistance (Claude) at the request of the TSC liaison; review it like any other change.

Scope: the specification, the reference implementation, the examples, the vendor runtimes and conversion
toolchains, and the OAAX tools (`oaax-manager`, `oaax-conformance`).

## 1. Versioning

- Every deliverable uses [SemVer](https://semver.org) `MAJOR.MINOR.PATCH`, kept in the repo's `VERSION` file (the Python
  tools keep it in `pyproject.toml`; the specification and examples repositories have no `VERSION` file, their tag is the version).
- The specification is versioned `MAJOR.MINOR`. A minor release only adds; within a major version the `interface.h`
  names, signatures and enum values are never changed or renumbered. A breaking change waits for the next major.
- `MAJOR.MINOR` of an official runtime or toolchain is the spec version it implements. `PATCH` is for fixes.

## 2. Immutability

- A published version is never modified or deleted: its tag, its release page and its artifacts in the bucket.
- A fix is a new patch version (`2.0.0` -> `2.0.1`). The only moving pointer is `latest/`.
- A version with a security or legal problem may be withdrawn: the release page says so and names the replacement.
  It is never silently overwritten (proxies and users' pinned checksums would serve a mix of both).

## 3. Tags and releases

A release is a lightweight tag `vX.Y.Z` on a commit of `main` where:

- CI is green and `VERSION` equals the tag (where the repo has one);
- `CHANGELOG.md` has a dated `## [X.Y.Z]` section (where the repo has one).

One GitHub release per tag, created as a draft, reviewed by a maintainer, then published. The release is titled
`OAAX <name> v<version>`: `OAAX CPU v2.0.0`, `OAAX NVIDIA v2.0.0`, `OAAX Specification v2.0.0`, `OAAX Examples v2.0.0`.
Its page has:

| Item | Content |
| ---- | ------- |
| Notes | The CHANGELOG section |
| Artifacts | Table of bucket URL, sha256 and size for every runtime and toolchain of the version |
| Commit | The commit that produced the artifacts (it must be the tagged one) |
| Conformance | Link to the `oaax-conformance` report for each artifact (sha256 of the tested file), once the suite is stable (see section 7) |
| Attached files | `SHA256SUMS` only |

Binaries stay in the bucket and are not attached to the release: toolchain images reach 10 GB and GitHub allows 2 GiB
per file. The sha256 on the release page is what users verify; `oaax-manager` does it automatically.

Release notes written with an AI assistant end with the line `Release notes drafted with AI assistance (Claude).`

## 3.1 Artifact keys

Layout is unchanged: `runtimes/<version>/<VENDOR>/<arch>/<os>/...` and `conversion-toolchain/<version>/<VENDOR>/...`.
A key under a version is written once; the second write is a CI error, not an overwrite. Only `latest/` and branch/PR keys
may be overwritten. The vendor CI enforces it:

| Event | Writes |
| ----- | ------ |
| `vX.Y.Z` tag on a commit of `main`, equal to `VERSION` | `<VERSION>/` (write once) and `latest/` |
| Pull request (same repository, with secrets) | `<branch>/`, overwritten on each run, removed when the PR closes; never `latest/` |
| Push to `main`, fork or Dependabot PR | nothing |

A branch name that looks like a version (`latest`, a leading digit, `v<digit>`) is refused, so a PR cannot replace a release.

## 4. `oaax-manager`

It pins the sha256 of every artifact. A release that adds or changes artifacts regenerates the index
(`tools/gen_index.py` in the `oaax-manager` repository, checked with `--check`) and ships a new `oaax-manager` version.

## 5. Patch releases

1. Fix on `main` through a PR (DCO sign-off, CI green).
2. Bump `VERSION` and `CHANGELOG.md`.
3. Tag `vX.Y.(Z+1)`, publish the draft, regenerate the `oaax-manager` index.

## 6. Not decided here (TSC)

Support window and end of life, branch model for maintenance releases, deprecation period, and which vendors may
claim "OAAX 2.x compatible" (the proposal is: a passing conformance report for that exact artifact).

## 7. Transition for 2.0

The `2.0.0` artifacts were uploaded by `main` builds before this policy existed: until the 2.0 release, every push to
`main` re-uploaded `<VERSION>/`. During the 2.0 release the vendor CI moved to the table in section 3.1, so a `main` push no
longer changes a published file.

- For 2.0.0 each implementation tag points at the commit whose `main` build produced the artifacts (checked from the CI
  run), and the release notes say so. Those tags predate the tag-triggered upload, so the 2.0.0 files were not written by
  a tag build; the first tag build runs with 2.0.1.
- The specification and examples releases (`OAAX Specification v2.0.0`, `OAAX Examples v2.0.0`) are lightweight tags on
  `main` with no artifacts.
- The 2.0.0 releases attach no files and carry no conformance report: `oaax-conformance` is 0.x and the reference CPU
  runtime has known findings (reference-implementation issues #45 to #49). The conformance link becomes required in
  the release page when the TSC declares the suite stable.
- `oaax-manager` 0.1.0 pins the 2.0.0 checksums but its index is stale for Hailo; 0.1.1 corrects it.
- The `oaax-manager` and `oaax-conformance` 0.1.0 releases are titled `v0.1.0`; the title convention applies from their next
  release.
