# MindHub RFC 草案（Draft v0.1）

## 项目名称

**MindHub**

> An Open Knowledge Operating System for AI Agents.

---

# 一、项目背景

随着 Claude Code、Codex、Hermes、Cursor、OpenHands 等 AI Agent 的普及，一个新的问题开始出现：

AI Agent 会不断产生知识，但这些知识无法长期积累、共享、治理和演化。

目前主流方案包括：

* AgentMemory
* Mem0
* Graphiti
* Zep
* Letta
* Obsidian Second Brain

它们分别解决了：

* 长期记忆
* RAG
* 知识图谱
* Agent Memory
* 第二大脑

但没有一个项目真正解决：

> 多 Agent 与人共同产生知识后的生命周期管理（Knowledge Lifecycle）。

MindHub 的目标就是填补这一空白。

---

# 二、MindHub 的定位

MindHub 不是：

* Vector Database
* RAG
* Memory Database
* 第二大脑
* MCP Server

MindHub 是：

> 一个面向 AI Agent 的 Knowledge Operating System（知识操作系统）。

一句话定义：

> MindHub 是一个开源的远端共享知识中枢，为 AI Agent 提供可治理、可演化、可审计、可版本化的长期知识系统。

---

# 三、MindHub 管理什么？

MindHub 管理的是：

> Knowledge（知识）

而不是单纯 Memory。

Memory 只是 Knowledge 的来源之一。

Knowledge 来源包括：

* 用户聊天
* Agent 对话
* Tool 调用结果
* Git Commit
* 日志
* 文档
* MCP Tool
* API 返回
* 外部系统

统一抽象为：

Observation。

---

# 四、Knowledge Evolution Model

MindHub 不采用传统 Memory Model。

采用：

Observation

↓

Information

↓

Knowledge

↓

Wisdom

对应：

DIKW 模型。

进一步演化：

Observation

↓

Finding

↓

Fact

↓

Decision

↓

Experience

↓

Relationship

↓

Knowledge Graph

↓

Knowledge Evolution

---

# 五、MindHub 与 AgentMemory 的关系

AgentMemory：

类似海马体（Hippo）。

负责：

* Working Memory
* 执行上下文
* Coding Context
* 最近任务

MindHub：

类似大脑新皮层（Neocortex）。

负责：

* 长期知识
* 知识治理
* 知识连接
* 知识演化
* Knowledge Cortex

因此：

AgentMemory 与 MindHub 并不是替代关系，而是互补关系。

---

# 六、Knowledge Governance

核心原则：

AI 自动治理为主。

尽量减少人工参与。

治理流程：

Rule Engine

↓

AI Governance Agent

↓

Human Review（仅高风险）

用户不是审核每一条 Memory。

而是审核：

Knowledge 的变化。

例如：

* 新增 Fact
* Preference 更新
* Knowledge Conflict
* Scope 变化

AI 自动完成：

* 聚类
* 抽象
* 总结
* 建立连接
* 去重
* 冲突发现
* 合并
* 压缩

用户查看：

AI Governance Report。

支持：

* 定期报告
* 主动推送
* 按需查询

---

# 七、Knowledge Version

MindHub 更接近 Git，而不是数据库。

采用：

Event Sourcing

而不是：

覆盖更新。

原则：

Current Knowledge

*

Knowledge Events

*

Snapshots

保留：

* 来源
* 历史
* 演化过程

支持：

Time Travel。

同时：

Embedding 不需要每个版本保存。

历史采用：

冷热分层。

---

# 八、Knowledge Scope

Scope 层级：

Global

↓

Organization

↓

Project

↓

User

↓

Agent

↓

Session

支持：

继承。

例如：

Project Fact

可自动被 Agent 使用。

---

# 九、知识连接

参考：

Zettelkasten。

知识不是列表。

而是：

Knowledge Network。

连接强度采用：

Hebbian Learning。

Together Fired

↓

Together Wired

共同出现越多：

连接越强。

未来：

Knowledge Retrieval：

不仅依赖 Embedding。

还依赖：

Knowledge Connection Weight。

---

# 十、知识成长

MindHub 的核心思想：

Knowledge 会成长。

每天：

Replay

↓

Summarize

↓

Compress

↓

Reconnect

↓

Merge

↓

Abstract

对应：

Memory Consolidation。

不是：

Store Once。

而是：

Continuous Evolution。

---

# 十一、知识再巩固

参考：

Reconsolidation Theory。

不是：

Update。

而是：

Recall

↓

Re-evaluate

↓

Reconnect

↓

Save

所有 Knowledge：

都可以：

重新理解。

---

# 十二、PARA

Scope 与 PARA 对应：

Project

Area

Resource

Archive

MindHub 内部：

Knowledge 自动归类。

AI 自动维护 PARA。

用户无需手工整理。

---

# 十三、与 Obsidian 的关系

MindHub 不取代 Obsidian。

Obsidian：

面向人。

MindHub：

面向 Agent + 人。

未来：

支持：

Obsidian Import

Obsidian Export

Markdown Sync

Knowledge Sync。

定位：

MindHub 是 Second Brain 的 AI Cortex。

---

# 十四、MCP 定位

MindHub 不等于 MCP。

MCP：

只是接入协议。

MindHub 提供：

* MCP
* REST API
* SDK
* Webhook

统一：

Knowledge API。

---

# 十五、MindHub Architecture

AI Agents

* Codex
* Claude Code
* Hermes
* Cursor
* OpenHands

↓

MCP / REST / SDK

↓

MindHub

↓

Knowledge Governance

Knowledge Retrieval

Knowledge Version

Knowledge Graph

Knowledge Evolution

↓

Storage

* PostgreSQL
* pgvector
* Object Storage
* 可扩展其他向量数据库

---

# 十六、MindHub 与 RAG

MindHub：

不是 RAG。

MindHub：

包含：

Knowledge Retrieval。

Retrieval：

只是整个 Knowledge Operating System 的一个模块。

---

# 十七、核心设计原则

1. Knowledge First，而不是 Memory First。
2. AI Governance First，而不是 Human Governance First。
3. Event Sourcing，而不是覆盖更新。
4. Knowledge Evolution，而不是静态存储。
5. Knowledge Network，而不是 Memory List。
6. Human Review Governance，而不是 Review Memory。
7. Agent Collaboration，而不是 Single Agent Memory。
8. 开放协议、开放存储、开放生态。

---

# 十八、认知科学理论基础

MindHub 将设计建立在认知科学基础之上。

包括：

* DIKW
* PARA
* Zettelkasten
* Hebbian Learning（赫布定律）
* Memory Consolidation（记忆巩固）
* Memory Reconsolidation（记忆再巩固）
* Hippocampus–Neocortex Interaction（海马体—新皮层互作）
* Semantic Network（语义网络）
* Chunking（组块化）

要求：

每一个核心设计：

必须同时回答：

1. 工程原因。
2. 对应认知科学依据。

---

# 十九、RFC 路线图

RFC-0001

MindHub Manifesto（愿景、原则、边界）

RFC-0002

Knowledge Model

RFC-0003

Knowledge Lifecycle

RFC-0004

Governance Engine

RFC-0005

Storage & Event Sourcing

RFC-0006

Knowledge Retrieval

RFC-0007

OpenMemory Protocol

RFC-0008

MCP Integration

RFC-0009

Plugin / Provider Framework

---

# 二十、当前仍待深入验证的问题

## P1（最高优先级）

Knowledge Model 如何定义？

需要明确：

* Observation
* Fact
* Preference
* Decision
* Experience
* Relationship

之间的边界与转换规则。

---

## P2

Knowledge Governance 的 AI 自动治理策略。

需要定义：

* 何时自动接受。
* 何时进入审核。
* 何时需要人工。

目标：

95% 以上治理自动完成。

---

## P3

Knowledge Evolution Engine。

如何利用：

Replay

Consolidation

Reconsolidation

真正实现：

Knowledge Growth。

这是 MindHub 最大创新点。

---

## P4

OpenMemory Protocol。

定义统一的：

Knowledge API。

让所有 Agent：

共享：

Knowledge。

---

# 二十一、项目愿景

MindHub 不希望成为：

"又一个 Memory 项目"。

MindHub 希望成为：

> AI Agent 时代的开放知识操作系统（Knowledge Operating System）。

未来：

人类负责创造价值。

AI Agent 持续产生 Observation。

MindHub 自动治理、连接、成长、演化知识。

最终形成：

一个不断成长的 Digital Cortex（数字新皮层）。

Knowledge 不再只是被保存。

而是能够持续学习、持续演化、持续成长。

