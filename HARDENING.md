<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-dump-context/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-dump-context/v3.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml file references `actions/github-script@v8`, which uses a mutable version tag (`@v8`) rather than a pinned 40-character commit SHA. This means the action could silently pull in a different (potentially malicious) version of the dependency if the tag is moved, creating a supply-chain risk. It should be pinned to a full SHA, e.g. `actions/github-script@60a0d83039c74a4aee543508d2ffcb1c3799cdea # v7` (or the equivalent SHA for v8).

Locations:

- `action.yml:12`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/github-script@v8` to its full commit SHA `ed597411d8f924073f98dfc5c65a23a2325f34cd` in hardened/action/action.yml (line 12), preserving the `# v8` tag as a comment for readability.

