<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-dump-context/v2.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-dump-context/v2.1.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action uses `actions/github-script@v6`, which is pinned to a mutable version tag rather than an immutable full-length commit SHA (40 hex characters). If the tag is moved (e.g. by a supply-chain compromise of the upstream repository), the action will silently execute different code. Pin to a specific commit SHA instead, e.g. `actions/github-script@60a0d83039c74a4aee543508d2ffcb1c3799cdea # v6`.

Locations:

- `action.yml:12`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/github-script@v6` to its full commit SHA `d7906e4ad0b1822421a7e6a35d5ca353c962f410` in hardened/action/action.yml (line 12). The original tag is preserved as a comment: `# v6`.

