<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-dump-context/v2.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-dump-context/v2.2.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple `uses:` references are pinned to mutable tags rather than full 40-character commit SHAs, making the action vulnerable to supply-chain attacks if the tag is moved or overwritten.

- action.yml: `uses: actions/github-script@v7` (tag `v7`)
- .github/workflows/ci.yml: `uses: actions/checkout@v4` (tag `v4`)
- .github/workflows/labels.yml: `uses: actions/checkout@v4` (tag `v4`) and `uses: crazy-max/ghaction-github-labeler@v5` (tag `v5`)

All should be pinned to a full SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `action.yml:12`
- `.github/workflows/ci.yml:23`
- `.github/workflows/labels.yml:21`
- `.github/workflows/labels.yml:24`

### missing-permissions (severity: medium)

Neither workflow file defines a top-level `permissions:` block, and no job in either file defines a job-level `permissions:` block. Without explicit permissions, GitHub Actions defaults to the repository's default token permissions (often `write-all` for older repositories), granting unnecessarily broad access. Each workflow should declare minimal required permissions.

Locations:

- `.github/workflows/ci.yml:1`
- `.github/workflows/labels.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Pinned all four unpinned action references to full 40-character commit SHAs: actions/github-script@v7→f28e40c7f34bde8b3046d885e986cb6290c5673b in action.yml; actions/checkout@v4→11d5960a326750d5838078e36cf38b85af677262 in both workflow files; crazy-max/ghaction-github-labeler@v5→24d110aa46a59976b8a7f35518cb7f14f434c916 in labels.yml. Added top-level permissions blocks: ci.yml gets 'contents: read' (only needs checkout), labels.yml gets 'contents: read' and 'issues: write' (labeler needs to manage labels).

