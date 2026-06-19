# Fork Development Branch — aspnmy/qwen-code

**Parent:** main | **Upstream:** QwenLM/qwen-code:main
**Purpose:** Fork-specific capabilities. NOT for upstream PR.

## Capability Inventory

### Fixes (submitted for upstream PR)

| Capability                                     | Issue             |  PR   |  Status   |
| ---------------------------------------------- | ----------------- | :---: | :-------: |
| SSE Stream Idle Watchdog (90s)                 | #4177             | #5394 | submitted |
| P0+P1: Dup threshold 6-to-4 + API 400 recovery | #5019             | #5394 | submitted |
| P2: Sub-agent token budget warn                | #5180             | #5394 | submitted |
| UI flicker fixes                               | #4561 #3838 #2928 | #5396 | submitted |

### Fork-Specific (NOT for upstream)

| Capability                               | Type  | Detail                |
| ---------------------------------------- | ----- | --------------------- |
| Removed upstream CI workflows (15 files) | infra | Avoid CI on fork push |
| Node.js 24 (.nvmrc)                      | infra | Build env requirement |

## Fork vs Upstream Comparison

| Dimension             | Upstream | Fork                       |
| --------------------- | -------- | -------------------------- |
| Version               | v0.18.3  | v0.18.3-aspnmy-agent-cli.1 |
| Node.js               | default  | 24                         |
| CI workflows          | 15       | 0                          |
| Stream idle detection | no       | yes (90s)                  |
| Tool dup threshold    | 6        | 4                          |
| API 400 recovery      | no       | yes                        |
| Sub-agent budget warn | no       | 200K/300K                  |
| UI stream throttle    | 60ms     | 100ms                      |
| Compact toggle        | sync     | startTransition            |
| Sub-agent events      | per-part | per-chunk                  |

## Build

node --version # >= v24.0.0
npm ci && npm run build
npm run test:ci

## Tag

v0.18.3-aspnmy-agent-cli.1

## Dev branch rules

- New features NOT for upstream live here
- Sync from upstream/main regularly
