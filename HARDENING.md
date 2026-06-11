<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-dump-context/v2.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **crazy-max--ghaction-dump-context/v2.1.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action uses `actions/github-script@v6`, which is pinned to a mutable version tag (`@v6`) rather than an immutable 40-character commit SHA. This means the action could be silently updated or compromised without the consuming workflow noticing, creating a supply-chain risk. It should be pinned to a full SHA, e.g. `actions/github-script@60a0d83039c74a4aee543508d2ffcb1c3799cdea # v6`.

Locations:

- `action.yml:12`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/github-script@v6` to its full commit SHA `d7906e4ad0b1822421a7e6a35d5ca353c962f410` in action.yml line 12. The mutable tag `@v6` was replaced with `@d7906e4ad0b1822421a7e6a35d5ca353c962f410 # v6` to prevent supply-chain attacks while preserving readability.

