# my-agents-md

[English](README.md) | 中文

我的个人 [AGENTS.md](AGENTS.md)，包括文档规范的 skills。

## 特性

AGENTS.md 特性：（默认前提）

- skills 即知识库：要求 agent 对不懂的概念 grep skills 的全量 .md 文件
- skill 优先：读完 skill 先总结其覆盖范围，在其内按它执行，避免自行探索
- 数值约束：强调按字面执行，不多不少，比如列出几个，说多少字
- 文档规范：按引用层级组织——区分概念、草稿和文档；每个事实单一权威来源；为持久性而写
- 禁止不可逆行为：如 `git reset --hard`、`push -f`、杀进程等，除非用户明确确认

附带 skills 特性：（犯错后强调）

- 遵守 skills 规范：根据 SKILL.md 链接可达性，区分 Skill 与 Notes，子文档渐进披露
- 命名灵感：对于命名和路径的确定，要求必须提议多个方案并推荐，需要用户确认
- 阶段门禁：引导 agent 自己划分任务阶段，一次一个阶段，各阶段独立权限。附带明确的前置任务提示词

## Skills

- [skill-authoring](skills/skill-authoring/SKILL.md) — Skill 与 Notes 的区分，SKILL.md 为入口渐进披露
- [conversation-flow](skills/conversation-flow/SKILL.md) — 对话流程：阶段门禁、反馈循环、前置任务 stack push

## License

[MIT](LICENSE)
