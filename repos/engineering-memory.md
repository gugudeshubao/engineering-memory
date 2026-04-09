# Repo Card: engineering-memory

## Identity

- Path: /home/wangyang/project/github/owner/story/ai_work/engineering-memory
- Role: private control plane for cross-repo context, task packets, repo cards, and handoffs
- Owner: wangyang
- Upstream repos: none
- Downstream repos:
  - AI-Study-Warehouse
  - flashinfer-bench-tma-thrust

## Boundary

- This repo is responsible for:
  - cross-repo memory objects
  - repo index and active workset
  - task packets and handoffs
- This repo is not responsible for:
  - product code
  - benchmark implementations
  - model or kernel source of business repos
- Strongest coupling points:
  - task packet -> repo card -> handoff

## Common Commands

- Build: N/A
- Test: N/A
- Run: read `README.md`, current task packet, and relevant repo card
- Debug: `git diff`, `rg`, and markdown review

## Key Entrypoints

- Key dirs:
  - system/
  - repos/
  - tasks/
  - handoffs/
- Key files:
  - system/system-map.md
  - system/repos.yaml
  - system/active-workset.md
- Key functions or binaries:
  - N/A

## Important Interfaces

- Interface:
  - repo-card
  - Related repo:
    - all tracked repos
  - Contract:
    - stable repo-level memory for fast rehydration
  - Failure mode:
    - repo switch depends on stale or missing summary

- Interface:
  - task-packet
  - Related repo:
    - all cross-repo tasks
  - Contract:
    - one packet per cross-repo problem
  - Failure mode:
    - task context splits across multiple repos and chat sessions

## Risks And Constraints

- Hard constraint:
  - do not copy large chunks of business source code into this repo
- Typical risk:
  - handoffs and active workset stop being updated
- Version sensitivity:
  - high for task packets and branch-sensitive notes

## Hotspots

- Area:
  - system/
  - Why it matters:
    - global index and active workset live here
  - What usually breaks:
    - system map and repos index become too generic

- Area:
  - tasks/
  - Why it matters:
    - this is the bridge across repos and AI tools
  - What usually breaks:
    - tasks degrade into vague notes instead of executable packets

## Current Status

- Current branch: main
- Current focus: bootstrap real examples from nearby repos
- Current blockers: none
- Related handoff: handoffs/2026-04-09-memory-bootstrap.md
