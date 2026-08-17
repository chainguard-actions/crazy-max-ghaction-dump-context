<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-dump-context/v2.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-dump-context/v2.3.0** was hardened automatically. 5 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml uses `actions/github-script@v7` — this is a mutable tag reference, not a pinned SHA. Supply-chain attacks can silently replace the tag. Pin to a full 40-character commit SHA (e.g. `actions/github-script@60a0d83039c74a4aee543508d2ffcb1c3799cdea # v7`).

Locations:

- `action.yml:12`

### unpinned-uses (severity: high)

ci.yml uses `actions/checkout@v4` — mutable tag reference, not a pinned SHA. Pin to a full 40-character commit SHA.

Locations:

- `.github/workflows/ci.yml:26`

### unpinned-uses (severity: high)

labels.yml uses `actions/checkout@v4` and `crazy-max/ghaction-github-labeler@v5` — both are mutable tag references, not pinned SHAs. Pin each to a full 40-character commit SHA.

Locations:

- `.github/workflows/labels.yml:22`
- `.github/workflows/labels.yml:25`

### missing-permissions (severity: medium)

ci.yml has no top-level `permissions:` key and no job-level `permissions:` key on any job. Without explicit permissions the workflow inherits the repository default (often `write-all`), granting excessive access. Add a minimal top-level `permissions:` block (e.g. `permissions: read-all` or specific scopes).

Locations:

- `.github/workflows/ci.yml:1`

### missing-permissions (severity: medium)

labels.yml has no top-level `permissions:` key and no job-level `permissions:` key on any job. Without explicit permissions the workflow inherits the repository default (often `write-all`), granting excessive access. Add a minimal top-level `permissions:` block with only the scopes required (e.g. `issues: write` for label management).

Locations:

- `.github/workflows/labels.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 5 findings: (1) Pinned actions/github-script@v7 → @f28e40c7f34bde8b3046d885e986cb6290c5673b in action.yml. (2) Pinned actions/checkout@v4 → @11d5960a326750d5838078e36cf38b85af677262 in ci.yml and labels.yml. (3) Pinned crazy-max/ghaction-github-labeler@v5 → @24d110aa46a59976b8a7f35518cb7f14f434c916 in labels.yml. (4) Added top-level `permissions: contents: read` to ci.yml. (5) Added top-level permissions block (contents: read, issues: write, pull-requests: write) to labels.yml to support label management operations.

