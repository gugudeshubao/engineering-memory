# Repo Card: flashinfer-bench-tma-thrust

## Identity

- Path: /home/wangyang/project/github/owner/flashinfer-bench-tma-thrust
- Role: FlashInfer-related kernel optimization, benchmark, and contest repo
- Owner: wangyang
- Upstream repos: none
- Downstream repos: none

## Boundary

- This repo is responsible for:
  - GDN kernel implementations
  - DSA and MoE solution work
  - benchmark scripts and performance docs
  - local CUDA build for selected kernels
- This repo is not responsible for:
  - production serving stack
  - global model deployment orchestration
- Strongest coupling points:
  - benchmarks/ <-> kernels/
  - docs/ <-> measured performance
  - modal scripts <-> local build assumptions

## Common Commands

- Build: `mkdir -p build && cd build && cmake .. && make -j`
- Test: `modal run gdn/tests/test_correctness.py`
- Run: `modal run gdn/benchmarks/bench_modal.py --kernel decode`
- Debug: inspect `gdn/`, `dsa/`, `moe/`, and `CMakeLists.txt`

## Key Entrypoints

- Key dirs:
  - gdn/
  - dsa/
  - moe/
  - scripts/
  - src/
- Key files:
  - README.md
  - CMakeLists.txt
  - gdn/gdn_kernels.cu
  - moe/config.toml
- Key functions or binaries:
  - `gdn/benchmarks/bench_modal.py`
  - `gdn/tests/test_correctness.py`

## Important Interfaces

- Interface:
  - benchmark to kernel implementation
  - Related repo:
    - none
  - Contract:
    - performance claims must trace back to a concrete kernel/config path
  - Failure mode:
    - benchmark number survives but kernel context is lost

- Interface:
  - local CUDA build to modal benchmark path
  - Related repo:
    - none
  - Contract:
    - local build and remote benchmark should remain comparable
  - Failure mode:
    - local build succeeds but modal result is not reproducible

## Risks And Constraints

- Hard constraint:
  - architecture assumptions are Blackwell-heavy (`CMAKE_CUDA_ARCHITECTURES 100`)
- Typical risk:
  - performance facts become stale across hardware, branches, or configs
- Version sensitivity:
  - high for CUDA toolkit, architecture, and benchmark scripts

## Hotspots

- Area:
  - gdn/
  - Why it matters:
    - main production-ready operator path in repo
  - What usually breaks:
    - benchmark correctness/performance linkage

- Area:
  - moe/
  - Why it matters:
    - active in-progress optimization and config-heavy experimentation
  - What usually breaks:
    - script/config/solution divergence

- Area:
  - CMakeLists.txt
  - Why it matters:
    - local CUDA build assumptions live here
  - What usually breaks:
    - architecture mismatch or build environment drift

## Current Status

- Current branch: main
- Current focus: bootstrap example repo card for memory system
- Current blockers: benchmark context currently split across docs, modal scripts, and local build
- Related handoff: handoffs/2026-04-09-memory-bootstrap.md
