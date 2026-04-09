# Active Workset

## Goal

这份文件只维护当前热工作集。

不要把所有仓库都列在这里。  
这里只放：

- 当前活跃任务
- 当前活跃仓库
- 当前需要持续保温的判断

## Active Tasks

- Task:
  - Stabilize memory workflow around the two primary repos
  - Packet:
    - tasks/2026-04-09-bootstrap-owner-memory.md
  - Priority:
    - high
  - Current focus:
    - use engineering-memory as the control plane for AI-Study-Warehouse and flashinfer-bench-tma-thrust

## Active Repos

- Repo:
  - engineering-memory
  - Why active:
    - control plane being initialized
  - Current branch:
    - main
  - Current handoff:
    - handoffs/2026-04-09-memory-bootstrap.md

- Repo:
  - AI-Study-Warehouse
  - Why active:
    - one of the two primary working repositories
  - Current branch:
    - main
  - Current handoff:
    - handoffs/2026-04-09-AI-Study-Warehouse.md

- Repo:
  - flashinfer-bench-tma-thrust
  - Why active:
    - one of the two primary working repositories
  - Current branch:
    - main
  - Current handoff:
    - handoffs/2026-04-09-flashinfer-bench-tma-thrust.md

## Current Hypotheses

- Hypothesis:
  - A small external memory repo can replace many long-lived repo-specific AI sessions
  - Related repos:
    - engineering-memory
    - AI-Study-Warehouse
    - flashinfer-bench-tma-thrust
  - Evidence:
    - current cost of terminal switching across many repos, even after narrowing primary focus to two hot repos
  - Next validation:
    - continue using repo cards, task packets, and handoffs during real switching between the two primary repos
