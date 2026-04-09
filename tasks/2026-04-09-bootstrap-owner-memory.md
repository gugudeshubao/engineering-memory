# Task Packet: bootstrap-owner-memory

## Identity

- Date: 2026-04-09
- Priority: high
- Owner: wangyang
- Goal: create one runnable engineering-memory example using real nearby repos
- Goal: establish the first usable control plane for the two primary repos
- Done definition:
  - system map updated
  - repos.yaml contains real repo entries
  - at least two real repo cards created
  - repo-specific handoffs exist for the two primary repos

## Symptom Or Need

- Current symptom:
  - many repos exist, and repo-local AI sessions are expensive to keep warm
- Why this matters:
  - even after narrowing day-to-day work to two primary repos, switching cost is still noticeable without external memory

## Related Repos

- Repo:
  - engineering-memory
  - Why involved:
    - control plane for external context
  - Key file or module:
    - system/, repos/, tasks/, handoffs/

- Repo:
  - AI-Study-Warehouse
  - Why involved:
    - one of the two current primary repositories
  - Key file or module:
    - README.md, codes/, docs/, scripts/

- Repo:
  - flashinfer-bench-tma-thrust
  - Why involved:
    - one of the two current primary repositories
  - Key file or module:
    - README.md, CMakeLists.txt, gdn/, dsa/, moe/

## Current Facts

- Fact:
  - engineering-memory is already a separate git repo and has been pushed to GitHub
  - Source:
    - local git status and remote setup
  - Confidence:
    - high

- Fact:
  - AI-Study-Warehouse branch is `main` at `3620efe`
  - Source:
    - local git metadata
  - Confidence:
    - high

- Fact:
  - flashinfer-bench-tma-thrust branch is `main` at `6852ac0`
  - Source:
    - local git metadata
  - Confidence:
    - high

## Current Hypotheses

- Hypothesis:
  - a small external memory repo can replace many long-lived repo-specific AI sessions
  - Why plausible:
    - repo cards plus task packets reduce rehydration cost
  - How to validate:
    - use this setup on real multi-repo work in following days

## Already Verified

- Verified item:
  - base memory repo structure exists
  - Result:
    - done
  - Evidence:
    - README and template files already committed

- Verified item:
  - the two primary repos are now explicitly defined
  - Result:
    - done
  - Evidence:
    - user confirmed AI-Study-Warehouse and flashinfer-bench-tma-thrust as current main repositories

## Next Step

- Immediate next step:
  - use this memory repo on the next real task that switches between AI-Study-Warehouse and flashinfer-bench-tma-thrust
- Required repo:
  - engineering-memory
- Required command or artifact:
  - new task packet plus repo-specific handoff

## Open Questions

- Question:
  - what the first real cross-repo task between the two primary repos will be
  - Blocked by:
    - upcoming concrete work
