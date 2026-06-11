<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-dump-context/v2.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **crazy-max--ghaction-dump-context/v2.2.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action uses `actions/github-script@v7`, which is pinned to a mutable version tag rather than an immutable 40-character commit SHA. This means the referenced action could be silently replaced with a different (potentially malicious) version without any change to this file, creating a supply-chain risk.

Locations:

- `action.yml:13`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced `actions/github-script@v7` with `actions/github-script@f28e40c7f34bde8b3046d885e986cb6290c5673b # v7` in action.yml line 13. The full commit SHA was resolved via lookup_action_sha and the original tag is preserved as a comment for readability.

