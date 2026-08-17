<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-dump-context/v2.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-dump-context/v2.1.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple `uses:` references are pinned to mutable tags rather than full 40-character commit SHAs, making the action vulnerable to supply-chain attacks if the tag is moved or overwritten.

- `action.yml`: `uses: actions/github-script@v6` (tag `v6`)
- `.github/workflows/ci.yml`: `uses: actions/checkout@v3` (tag `v3`)
- `.github/workflows/labels.yml`: `uses: actions/checkout@v3` (tag `v3`) and `uses: crazy-max/ghaction-github-labeler@v4` (tag `v4`)

All of these should be pinned to their full SHA digest, e.g. `actions/github-script@60a0d83039c74a4aee543508d2ffcb1c3799cdea # v6`.

Locations:

- `action.yml:13`
- `.github/workflows/ci.yml:22`
- `.github/workflows/labels.yml:16`
- `.github/workflows/labels.yml:20`

### missing-permissions (severity: medium)

Neither `ci.yml` nor `labels.yml` declares a top-level `permissions:` key, and no job in either file has its own `permissions:` block. Without explicit permissions, the GITHUB_TOKEN is granted its default (potentially broad) permissions. Each workflow should declare the minimal set of permissions required (e.g. `permissions: read-all` or specific scopes).

Locations:

- `.github/workflows/ci.yml:1`
- `.github/workflows/labels.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Pinned all four unpinned action references to full 40-character commit SHAs: actions/github-script@v6→d7906e4ad0b1822421a7e6a35d5ca353c962f410 in action.yml; actions/checkout@v3→f43a0e5ff2bd294095638e18286ca9a3d1956744 in both ci.yml and labels.yml; crazy-max/ghaction-github-labeler@v4→f4f6b96e7e747b5416cd470f3cfecf26abaa811e in labels.yml. Added top-level permissions blocks: ci.yml gets 'contents: read' (sufficient for checkout); labels.yml gets 'contents: read' and 'issues: write' (needed for the labeler action to manage labels). The only remaining unpinned reference is in README.md which is documentation only.

