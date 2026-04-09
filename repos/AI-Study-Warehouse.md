# Repo Card: AI-Study-Warehouse

## Identity

- Path: /home/wangyang/project/github/owner/AI-Study-Warehouse
- Role: personal AI learning, notes, experiments, and runnable code snippets warehouse
- Owner: wangyang
- Upstream repos: none
- Downstream repos: none

## Boundary

- This repo is responsible for:
  - learning notes
  - code snippets and demos
  - experiment records
  - helper scripts
- This repo is not responsible for:
  - production deployment
  - shared runtime or system integration
- Strongest coupling points:
  - docs/ <-> codes/
  - experiments/ <-> scripts/

## Common Commands

- Build: `cd codes/flash-attn-handwritten && mkdir -p build && cd build && cmake .. && make -j`
- Test: `cd codes/flash-attn-handwritten/build && ctest --output-on-failure`
- Run: read `README.md`, then enter `docs/`, `codes/`, or `experiments/`
- Debug: inspect `codes/flash-attn-handwritten/tests/` and related source dirs

## Key Entrypoints

- Key dirs:
  - docs/
  - codes/
  - experiments/
  - scripts/
- Key files:
  - README.md
  - codes/flash-attn-handwritten/CMakeLists.txt
  - scripts/modal_run_git_repo.py
- Key functions or binaries:
  - flash-attn handwritten examples and tests under `codes/flash-attn-handwritten`

## Important Interfaces

- Interface:
  - docs to runnable code
  - Related repo:
    - none
  - Contract:
    - notes should have a reproducible code or experiment path
  - Failure mode:
    - note remains but command path is forgotten

- Interface:
  - scripts to experiments
  - Related repo:
    - none
  - Contract:
    - helper scripts should map clearly to experiment artifacts
  - Failure mode:
    - script intent is unclear and experiment state is unrecoverable

## Risks And Constraints

- Hard constraint:
  - keep notes and runnable examples aligned
- Typical risk:
  - build or experiment context only exists in old terminal history
- Version sensitivity:
  - medium; examples and scripts can drift over time

## Hotspots

- Area:
  - codes/flash-attn-handwritten
  - Why it matters:
    - contains real C++/CUDA learning and benchmark code with tests
  - What usually breaks:
    - build path, test command, or architecture-specific assumptions

- Area:
  - docs/
  - Why it matters:
    - long-term knowledge retrieval starts here
  - What usually breaks:
    - docs stop reflecting what is actually runnable

## Current Status

- Current branch: main
- Current focus: bootstrap example repo card for memory system
- Current blockers: README quick start is still incomplete
- Related handoff: handoffs/2026-04-09-memory-bootstrap.md
