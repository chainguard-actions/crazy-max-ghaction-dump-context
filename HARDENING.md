<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-dump-context/v2.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-dump-context/v2.2.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The step uses `actions/github-script@v7`, which is pinned to a mutable version tag rather than an immutable 40-character commit SHA. A tag can be silently moved to point at a different (potentially malicious) commit, enabling a supply-chain attack. Pin the reference to a full SHA, e.g. `actions/github-script@60a0d83039c74a4aee543508d2ffcb1c3799cdea # v7`.

Locations:

- `action.yml:12`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/github-script@v7` to its full commit SHA `f28e40c7f34bde8b3046d885e986cb6290c5673b` in hardened/action/action.yml line 12. The original tag is preserved as an inline comment (`# v7`) for readability.

