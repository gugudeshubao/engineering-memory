# Task Packet: bootstrap-owner-memory

## Identity

- Date: 2026-04-09
- Priority: high
- Owner: wangyang
- Goal: create one runnable engineering-memory example using real nearby repos
- Done definition:
  - system map updated
  - repos.yaml contains real repo entries
  - at least two real repo cards created
  - one handoff exists

## Symptom Or Need

- Current symptom:
  - many repos exist, and repo-local AI sessions are expensive to keep warm
- Why this matters:
  - context switching time grows with repo count and tool count

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
    - first real repo card example for notes/code/experiments style repo
  - Key file or module:
    - README.md, codes/, docs/, scripts/

- Repo:
  - flashinfer-bench-tma-thrust
  - Why involved:
    - second real repo card example for kernel benchmark style repo
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

## Next Step

- Immediate next step:
  - use this memory repo on the next real cross-repo task and keep handoffs updated
- Required repo:
  - engineering-memory
- Required command or artifact:
  - new task packet plus repo-specific handoff

## Open Questions

- Question:
  - which 5 to 10 repos should be added next after these bootstrap examples
  - Blocked by:
    - actual current high-frequency workset
