# System Map

## Purpose

这份文件只描述系统主链路，不写仓库内部细节。

它应该帮助你快速回答：

- 当前系统由哪些主链路组成
- 哪些链路跨多个 repo
- 哪些地方是强耦合点
- 一个问题大概率应该从哪条链路切入

## Current Bootstrap Scope

当前这份 system map 先不追求覆盖你所有真实仓库。  
它先聚焦当前已经确认的主力范围：

- `engineering-memory`
- `AI-Study-Warehouse`
- `flashinfer-bench-tma-thrust`

这三个对象分别代表：

- 上下文控制面
- 个人学习与实验知识仓
- 高性能 kernel / benchmark / contest 仓

这里不是“示例仓库列表”，而是当前真实热工作集。

## Main Chains

### Context Control Chain

- Inputs:
- Active tasks, repo cards, handoffs
- Key repos:
  - engineering-memory
- Key interfaces:
  - task packet -> repo card -> handoff
- Main risks:
  - Context objects not updated when switching repos
  - Cross-repo tasks fragmented into repo-local notes

### Knowledge And Experiment Chain

- Inputs:
  - Notes, experiments, code snippets, scripts
- Key repos:
  - AI-Study-Warehouse
- Key interfaces:
  - docs/ <-> codes/ <-> experiments/
- Main risks:
  - Notes and runnable code diverge
  - Build and experiment context stays only in terminal history

### Kernel Benchmark And Optimization Chain

- Inputs:
  - CUDA kernels, Triton kernels, modal benchmark scripts
- Key repos:
  - flashinfer-bench-tma-thrust
- Key interfaces:
  - benchmarks/ <-> kernels/ <-> docs/
- Main risks:
  - Performance facts become stale across branches or hardware
  - Correctness and benchmark context drift apart

## Strong Coupling Points

- Point:
  - engineering-memory <-> any active repo
  - Related repos:
    - engineering-memory
    - AI-Study-Warehouse
    - flashinfer-bench-tma-thrust
  - Why coupling is strong:
    - Every repo switch depends on up-to-date repo cards and handoffs
  - Typical failure mode:
    - Repo context stays only in session memory and becomes stale

- Point:
  - AI-Study-Warehouse docs <-> code snippets
  - Related repos:
    - AI-Study-Warehouse
  - Why coupling is strong:
    - Learning notes are only useful when backed by runnable examples
  - Typical failure mode:
    - Notes remain but code path or run command is forgotten

- Point:
  - flashinfer-bench-tma-thrust benchmarks <-> kernel implementations
  - Related repos:
    - flashinfer-bench-tma-thrust
  - Why coupling is strong:
    - Performance claims depend on exact kernels, configs, and test paths
  - Typical failure mode:
    - Benchmark context is lost and later performance numbers cannot be trusted

## Current Top Risks

- Risk:
  - Repo switching overhead hides missing external context
  - Chain:
    - Context Control Chain
  - Evidence:
    - Previously relied on one terminal per repo to hold local context
  - Owner:
    - wangyang

- Risk:
  - Benchmark and experiment history is easy to lose across many repos and tools
  - Chain:
    - Knowledge And Experiment Chain
    - Kernel Benchmark And Optimization Chain
  - Evidence:
    - Multi-tool AI usage and frequent switching between the two primary repos
  - Owner:
    - wangyang
