<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-dump-context/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-dump-context/v3.0.0** was hardened automatically. 3 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references `actions/github-script@v8` using a mutable version tag instead of a pinned 40-character commit SHA. This exposes the action to supply-chain attacks if the tag is moved to a malicious commit.

Locations:

- `action.yml:12`

### unpinned-uses (severity: high)

.github/workflows/ci.yml references `actions/checkout@v6` using a mutable version tag instead of a pinned 40-character commit SHA.

Locations:

- `.github/workflows/ci.yml:33`

### unpinned-uses (severity: high)

.github/workflows/labels.yml references `actions/checkout@v6` and `crazy-max/ghaction-github-labeler@v6` using mutable version tags instead of pinned 40-character commit SHAs.

Locations:

- `.github/workflows/labels.yml:28`
- `.github/workflows/labels.yml:31`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all mutable action version tags to full 40-character commit SHAs:
- action.yml: actions/github-script@v8 → @ed597411d8f924073f98dfc5c65a23a2325f34cd # v8
- .github/workflows/ci.yml: actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803 # v6
- .github/workflows/labels.yml: actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803 # v6
- .github/workflows/labels.yml: crazy-max/ghaction-github-labeler@v6 → @548a7c3603594ec17c819e1239f281a3b801ab4d # v6
All SHAs were resolved via lookup_action_sha; original tags preserved as inline comments.

