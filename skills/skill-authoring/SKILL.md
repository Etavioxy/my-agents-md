---
name: skill-authoring
description: Skill 编写规范。Skill 与 Notes 的区别、命名方式。触发词：skill 编写、skill 规范。
---

# Skill 编写规范

## Skill vs Notes

| | Skill | Notes |
|------|-------|-------|
| **是什么** | 给其他调用 agent 使用的信息 | 编写过程中的记录，比如 user-goals |
| **范围** | SKILL.md + 通过其链接可达的全部文档，更精简 | 目录内不被链接的其余文件，更细节 |
| **是否被编辑 skill 的 agent 使用** | 是 | 是 |
| **是否被调用 skill 的 agent 使用** | 是 | 否 |

```
<skill-name>/          ← git 仓库
  ├── SKILL.md      ← 入口，被调用 agent 读取，里面可含有 link
  │   ├── <linkA>.md  ← 可选，通过链接可达 → Skill 的一部分
  │   └── <linkB>.md
  ├── drafts/       ← 可选，未被链接 → Notes
  │   └── YYYY-MM-DD-<topic>.md  ← 按需多个
  ├── spec.md       ← 可选，文档规范
  └── user-goals.md ← 可选，按需启用
```

子文档不是必须的。内容少时仅 SKILL.md 即可：

```
<skill-name>/            ← git 仓库
  ├── SKILL.md        ← 唯一文件
  └── (user-goals.md) ← 可选，只有用户要求才启用
```

### Skill

Skill 是给调用 agent 使用的信息。以 SKILL.md 为入口，通过链接组织关联文档，达到渐进披露的效果。不应有多余信息进入。并且应该减少文本量。

Skill 内的场景和结论都经过验证，不经用户确认的内容不得进入。

引用其他 skill 用 wiki 链接格式 **`[[skill-name]]`**，并附上说明 **`请 invoke [[skill-name]]`**

### Notes

Notes 是制造过程。Skill 目录内不被 SKILL.md 链接的文件——约束记录、草稿、讨论内容、格式规范。

- `drafts/`：每次任务的叙事性主记录，记录 grilling 的全过程（尤其保留用户原话、犯错原因）、sandbox 踩坑过程、阶段总结和原理归纳，仅 append 修改，无需提供给调用 agent
- `spec.md`：记录文档规范，skill 内容的写法约定，仅辅助编辑 skill 内容，无需提供给调用 agent

如果需要了解 user-goals 请 invoke [[goals-gate-approver]]

## SKILL 命名

目录名小写、连字符分隔。名称应包含场景和语义。结合现有 skills 命名规则。

## SKILL.md

记录经验的 delta，不重复官方文档。Skill 的价值在文档之外——源码结论、实际测试结果、绕过方案、未文档化的限制。善于使用链接来减少文本量。

作为入口索引，不透露关联文档的具体内容。

SKILL.md 必须以 YAML frontmatter（`---` 包裹的 `name` + `description`）开头。

**description：** 触发词仅放明确的，不含模糊词。

**放：** 触发词、已验证的类型/场景清单、关联文档的文件名列表。

**不放：** 未经用户确认的场景。具体项目名、仓库名、路径等指向特定项目的信息。涉及隐私的信息。

**最佳实践：**
- 必经内容不放入子文件：阅读 SKILL.md 时必须经过的核心判断标准、规则本身，应保留在 SKILL.md 内，不因篇幅考虑外移。
- 索引原则：篇幅过长（约大于15行）的技术细节（语法、限制、方案）放入被链接的文档，不在 SKILL.md 展开。
- 通用化：优先从原始经验中提炼可复用的通用结论，而非照搬。经过验证的具体发现可以入，同时标注适用前提。
- 配置值：避免在可配置字段上硬编码确切数值（如超时时间、端口号），代以占位符或说明。

每次修改后，审查 SKILL.md 与所有 Notes 文件的结论是否有不一致性，需要提炼并满足在 Agent 视角的信息可靠性。

通用性 SKILL 的场景来源不绑定单一框架，以用户对 SKILL 的定位为准。

## git 仓库

每个 Skill 的 git 仓库在 SKILL.md 所在文件夹，如果是链接需要先定位链接的位置。

提交信息格式：`type: 中文描述`。描述应包含改变内容，有必要时再加当前状态。
