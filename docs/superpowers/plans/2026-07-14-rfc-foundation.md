# MindHub RFC Foundation Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Publish MindHub's accepted RFC governance process, reusable RFC template, RFC index, and a reviewable RFC-0001 manifesto draft.

**Architecture:** Keep governance, authoring guidance, index state, and product vision in four focused Markdown files under `rfcs/`. Treat `Conception.md` as immutable source material and the approved design specification as the authority for scope and wording.

**Tech Stack:** Markdown, Git, POSIX shell validation commands

## Global Constraints

- The project owner `gittuyn` is the sole final decision-maker.
- RFC states are `Draft`, `Review`, `Accepted`, `Rejected`, and `Superseded`.
- AI Agents participate first; humans retain ultimate control.
- RFC-0001 must not define subjects owned by RFC-0002, RFC-0003, or RFC-0004.
- `Conception.md` remains unchanged.
- RFC prose is Chinese with English terms retained where they are the stable domain vocabulary.
- No database, API, framework, deployment, or user-interface design is introduced.

---

### Task 1: RFC Process and Authoring Template

**Files:**
- Create: `rfcs/0000-rfc-process.md`
- Create: `rfcs/template.md`

**Interfaces:**
- Consumes: `docs/superpowers/specs/2026-07-14-rfc-foundation-design.md`
- Produces: the normative status model, metadata schema, decision rules, and reusable section structure consumed by all later RFCs

- [ ] **Step 1: Create RFC-0000 with complete metadata**

Use this exact metadata and heading structure:

```markdown
# RFC-0000：MindHub RFC 流程

| 字段 | 值 |
| --- | --- |
| RFC | 0000 |
| 标题 | MindHub RFC 流程 |
| 作者 | gittuyn |
| 状态 | Accepted |
| 创建日期 | 2026-07-14 |
| 决策日期 | 2026-07-14 |
| 最终决策者 | gittuyn |
| 依赖 | 无 |

## 摘要
## 适用范围
## 角色与决策权
## 状态模型
## RFC 生命周期
## 编号与文件命名
## 必需元数据
## 必需章节
## 修订规则
## 决策记录
## Git 要求
## 替代方案
## 安全、隐私与治理
## 决策
## 修订历史
```

Define every transition in `Draft → Review → Accepted / Rejected → Superseded`. State that Review requires a deadline; Accepted means design approval rather than implementation; Rejected files remain with rationale; major changes to Accepted RFCs require a superseding RFC. Distinguish editorial corrections from semantic changes. Require explicit dependencies and a revision-history entry for material Review changes.

- [ ] **Step 2: Create the reusable template**

Use a metadata table with example tokens enclosed in angle brackets and these sections:

```markdown
# RFC-<编号>：<标题>

| 字段 | 值 |
| --- | --- |
| RFC | <四位编号> |
| 标题 | <标题> |
| 作者 | <作者> |
| 状态 | Draft |
| 创建日期 | <YYYY-MM-DD> |
| 评审截止日期 | 不适用（Draft） |
| 最终决策者 | gittuyn |
| 依赖 | <RFC 编号或“无”> |

## 摘要
## 动机
## 目标
## 非目标
## 术语
## 详细设计
## 考虑过的替代方案
## 安全、隐私与治理
## 兼容性
## 风险与开放问题
## 决策
## 修订历史
```

Add short authoring guidance below each heading. Ensure the guidance says open questions must be concrete and bounded rather than vague.

- [ ] **Step 3: Validate Task 1**

Run:

```bash
test -f rfcs/0000-rfc-process.md
test -f rfcs/template.md
for state in Draft Review Accepted Rejected Superseded; do rg -q "$state" rfcs/0000-rfc-process.md; done
rg -q 'gittuyn' rfcs/0000-rfc-process.md rfcs/template.md
git diff --check
```

Expected: every command exits `0`; the final command prints no errors.

- [ ] **Step 4: Commit Task 1**

```bash
git add rfcs/0000-rfc-process.md rfcs/template.md
git commit -m "docs: define the MindHub RFC process"
```

Expected: one commit containing only the process and template.

### Task 2: RFC-0001 MindHub Manifesto

**Files:**
- Create: `rfcs/0001-mindhub-manifesto.md`

**Interfaces:**
- Consumes: RFC-0000 metadata and process, `Conception.md`, and the approved RFC foundation design
- Produces: the product boundary and principles that constrain RFC-0002, RFC-0003, RFC-0004, and all implementation RFCs

- [ ] **Step 1: Create RFC-0001 metadata and sections**

Use this exact metadata:

```markdown
# RFC-0001：MindHub Manifesto

| 字段 | 值 |
| --- | --- |
| RFC | 0001 |
| 标题 | MindHub Manifesto |
| 作者 | gittuyn |
| 状态 | Draft |
| 创建日期 | 2026-07-14 |
| 评审截止日期 | 不适用（Draft） |
| 最终决策者 | gittuyn |
| 依赖 | RFC-0000 |
```

Use these sections:

```markdown
## 摘要
## 动机
## 定位
## 目标
## 非目标
## 核心原则
## AI Agent 优先，人类最终掌控
## 系统边界
## 对后续 RFC 的约束
## 成功标准
## 考虑过的替代方案
## 安全、隐私与治理
## 兼容性
## 风险与开放问题
## 决策
## 修订历史
```

- [ ] **Step 2: Write the normative product position**

Include this normative definition:

```text
MindHub 是一个 AI Agent 优先参与、由人类最终掌控的开放共享知识中枢，用于沉淀、治理、演化和交换具有来源、范围及历史的长期知识。
```

Define “Knowledge Operating System” as a responsibility boundary and governance layer, not a claim that MindHub replaces an operating system, database, model, or transport. Describe AI-default ingestion and low-risk governance together with configurable authority, escalation, revocation, auditability, rollback, correction, and final human deletion authority.

- [ ] **Step 3: Make exclusions and dependencies explicit**

State that Agent Memory, RAG, vector databases, note-taking systems, and MCP are complementary components or integrations rather than MindHub itself. Assign Knowledge entities and identity to RFC-0002, lifecycle and deletion semantics to RFC-0003, and OpenMemory interfaces and transport semantics to RFC-0004. Treat DIKW and brain-region analogies only as non-normative inspiration.

- [ ] **Step 4: Add reviewable success criteria**

Include criteria for responsibility classification, provenance and actor traceability, multi-Agent scope enforcement, risk escalation, implementation replaceability, and final human intervention. Keep RFC-0001 in Draft and leave the Decision section explicitly stating that acceptance awaits the owner's review rather than using an unresolved placeholder.

- [ ] **Step 5: Validate Task 2**

Run:

```bash
rg -q '状态.*Draft' rfcs/0001-mindhub-manifesto.md
rg -q 'AI Agent 优先参与、由人类最终掌控' rfcs/0001-mindhub-manifesto.md
for rfc in RFC-0000 RFC-0002 RFC-0003 RFC-0004; do rg -q "$rfc" rfcs/0001-mindhub-manifesto.md; done
! rg -n 'PostgreSQL|FastAPI|数据库表|API endpoint' rfcs/0001-mindhub-manifesto.md
git diff --check
```

Expected: every command exits `0`; no concrete storage or API design appears.

- [ ] **Step 6: Commit Task 2**

```bash
git add rfcs/0001-mindhub-manifesto.md
git commit -m "docs: draft the MindHub manifesto"
```

Expected: one commit containing only RFC-0001.

### Task 3: RFC Index and Cross-Document Validation

**Files:**
- Create: `rfcs/README.md`
- Verify: `rfcs/0000-rfc-process.md`
- Verify: `rfcs/template.md`
- Verify: `rfcs/0001-mindhub-manifesto.md`
- Verify unchanged: `Conception.md`

**Interfaces:**
- Consumes: RFC metadata from Tasks 1 and 2
- Produces: the repository entry point for RFC discovery and a consistent initial RFC set

- [ ] **Step 1: Create the RFC index**

Include a short explanation of the RFC directory, a link to RFC-0000, and this table:

```markdown
| RFC | 标题 | 状态 | 依赖 |
| --- | --- | --- | --- |
| [0000](0000-rfc-process.md) | MindHub RFC 流程 | Accepted | 无 |
| [0001](0001-mindhub-manifesto.md) | MindHub Manifesto | Draft | RFC-0000 |
```

Link `template.md` and explain that only the final decision-maker changes an RFC to Accepted or Rejected.

- [ ] **Step 2: Run the complete validation suite**

Capture the original source hash from Git and compare it with the working tree:

```bash
test "$(git show 54036f2:Conception.md | sha256sum | cut -d' ' -f1)" = "$(sha256sum Conception.md | cut -d' ' -f1)"
for file in rfcs/README.md rfcs/0000-rfc-process.md rfcs/template.md rfcs/0001-mindhub-manifesto.md; do test -s "$file"; done
for link in 0000-rfc-process.md 0001-mindhub-manifesto.md template.md; do rg -q "$link" rfcs/README.md; done
rg -q '^## 术语$' rfcs/0001-mindhub-manifesto.md
rg -q '^## 详细设计$' rfcs/0001-mindhub-manifesto.md
test -z "$(rg -n 'T''BD|T''ODO|XXXX|PLACEHOLDER' rfcs || true)"
git diff --check
```

Expected: every command exits `0`; `Conception.md` matches commit `54036f2` byte-for-byte; all RFC files are non-empty; index links resolve by filename; no unfinished markers exist.

- [ ] **Step 3: Inspect the final diff**

Run:

```bash
git diff --stat 54036f2..HEAD
git diff -- rfcs/README.md
git status --short --branch
```

Expected before the final commit: only `rfcs/README.md` is untracked or unstaged, while Tasks 1 and 2 are already committed.

- [ ] **Step 4: Commit and push the RFC foundation**

```bash
git add rfcs/README.md
git commit -m "docs: add the MindHub RFC index"
git push origin main
git status --short --branch
git ls-remote origin refs/heads/main
```

Expected: the working tree is clean, `main` is aligned with `origin/main`, and the remote hash matches `git rev-parse HEAD`.
