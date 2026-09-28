<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-dump-context/v2.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-dump-context/v2.3.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references `actions/github-script@v7`, which is a mutable tag rather than a pinned 40-character commit SHA. An attacker who compromises the upstream action repository could push malicious code to this tag, causing it to execute in all workflows that use this action. The reference should be pinned to a full SHA, e.g. `actions/github-script@60a0d83039c74a4aee543508d2ffcb1c3799cdea # v7`.

Locations:

- `action.yml:12`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/github-script@v7` to its full commit SHA `actions/github-script@f28e40c7f34bde8b3046d885e986cb6290c5673b # v7` in hardened/action/action.yml line 12. The SHA was resolved via lookup_action_sha and the original tag is preserved as a comment for readability.

