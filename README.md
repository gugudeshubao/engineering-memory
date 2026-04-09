# Engineering Memory Repo

这个仓库不是代码仓库，而是一个独立的上下文控制面。

它的目标是管理：

- 跨仓库系统地图
- 单仓库上下文卡片
- 跨仓库任务包
- handoff 和决策记录
- 多 AI 工具共享的外部记忆

核心原则：

- 代码仓库管代码
- 记忆仓库管上下文
- 会话只是缓存，不是记忆本体
- AI 工具只是执行器，不是上下文真源

## 目录说明

```text
engineering-memory/
  README.md
  .gitignore
  system/
    system-map.md
    repos.yaml
    active-workset.md
  repos/
    INDEX.md
    REPO_CARD_TEMPLATE.md
  tasks/
    TASK_TEMPLATE.md
  handoffs/
    HANDOFF_TEMPLATE.md
  decisions/
    DECISION_TEMPLATE.md
  interfaces/
    INTERFACE_TEMPLATE.md
```

## 推荐工作方式

### 1. 全局层先维护这三个文件

- `system/system-map.md`
- `system/repos.yaml`
- `system/active-workset.md`

它们分别解决：

- 系统主链路是什么
- 每个 repo 的角色和依赖是什么
- 当前热工作集是什么

### 2. 每个仓库建一张 repo card

从 `repos/REPO_CARD_TEMPLATE.md` 复制一份，命名为 `<repo-name>.md`。

repo card 只记录稳定上下文：

- 这个 repo 干什么
- 边界是什么
- build/test/debug 怎么跑
- 关键目录在哪里
- 最常踩的坑是什么

### 3. 每个跨仓库问题单独建 task packet

不要把跨仓库问题拆散记在多个 repo 里。

从 `tasks/TASK_TEMPLATE.md` 复制一份，命名为：

- `YYYY-MM-DD-<short-task-name>.md`

task packet 负责记录：

- 现象
- 目标
- 涉及仓库
- 当前事实
- 当前怀疑链路
- 已验证内容
- 下一步计划

### 4. 每次切走前更新 handoff

每次离开一个仓库或一个任务前，从 `handoffs/HANDOFF_TEMPLATE.md` 复制一份或更新现有文件。

最少写清：

- 当前分支或 commit
- 刚做了什么
- 下一步做什么
- 当前阻塞
- 相关 repo

### 5. 多 AI 工具通过这套外部记忆接力

不要让 Codex、Claude、Cursor 直接接力聊天记录。

推荐做法：

- 总控 AI 先读 `system-map.md`、`repos.yaml` 和当前 task packet
- 仓库执行 AI 只读对应 repo card + 当前 handoff + 当前 task packet
- 整理型 AI 把执行结果回填到 task packet、handoff 和 decisions

这意味着：

- 不同 AI 不共享内存
- 但它们共享同一套外部上下文对象

## 推荐命名约定

- repo card: `repos/<repo-name>.md`
- task packet: `tasks/YYYY-MM-DD-<task-name>.md`
- handoff: `handoffs/YYYY-MM-DD-<repo-or-task>.md`
- decision: `decisions/YYYY-MM-DD-<decision-name>.md`
- interface: `interfaces/<interface-name>.md`

## 不建议放进来的内容

- 业务仓库大段源码
- 敏感密钥、证书、token
- 大量原始日志
- 整段复制的外部正式文档

更合适的是只放：

- 路径
- commit hash
- 摘要
- 自己的判断
- 相关文件入口

## 起步顺序

如果今天开始用，建议先做这四步：

1. 先补 `system/system-map.md`
2. 再补 `system/repos.yaml`
3. 给当前最常碰的 3 到 5 个仓库建立 repo card
4. 给当前正在做的跨仓库问题建 1 个 task packet

做到这一步，你就已经把“会话记忆”转成“外部可恢复记忆”了。
