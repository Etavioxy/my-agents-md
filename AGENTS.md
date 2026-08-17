# Global agent instructions

- Do not proactively enter plan mode.
- Default to normal execution flow unless I explicitly ask for plan mode or clearly ask for planning first.
- If a task seems to benefit from planning, ask briefly before entering plan mode instead of entering automatically.
- When locating git repositories with Glob, do not rely on `**/.git` alone. Prefer `**/.git/HEAD` or `**/.git/description`, then confirm with `git -C <dir> rev-parse --show-toplevel`.
- When the user gives a specific numeric constraint (e.g. "加一句", "改一行", "删一个文件"), obey it exactly — add, modify, or delete only that count, no more, no less. Do not silently rewrite or remove other content alongside the requested change.
- Do not use shell commands to modify file content (e.g. `echo >`, `sed -i`, `awk -i`, `Set-Content`, `Out-File`, output redirection overwriting files). Use the Write/Edit tools instead — they are visible, reversible, and subject to permission control.
- When the user mentions a skill by name, invoke it proactively.
- When a term, concept, or path is unfamiliar, grep the skills directory (`.md` files only) for it before proceeding — a relevant skill may already cover it.
- Do not use the AskUserQuestion tool — confirm in natural language instead.
- Prefer pnpm, TypeScript, Rust, Python, Vite, LSP, JSONL, CLI. Avoid npm, ORM, GDB, REPL, JavaScript/Lua (untyped), sh, OpenGL.
- Prefer popular, well-maintained third-party libraries over obscure or low-adoption ones.
- Name things semantically — prefer descriptive, multi-word names over single abstract words or sequential labels (foo1, foo2). A good name tells you what it is without looking it up.

## Communication
用户的心智是稀缺资源，推迟确认与返工是最贵的浪费。遵循此原则自行判断：
- 大型逻辑用 ASCII 图，胜过长篇文字。
- 该确认的当下推完、记录共识，不说"等遇到问题再说"。
- 能自己查清的不问，不可逆或影响方向的必须问。
- 被 Cron 中断询问时，重新深入思考，选择最有利且符合规范的方法，不将错就错。
- 指令存在多种合理解释时，先指出歧义点让用户确认，不要直接猜一个实现就交付。

## Code of conduct
- 以暗猜接口为耻，以认真查阅为荣
- 以模糊执行为耻，以寻求确认为荣
- 以盲想业务为耻，以人类确认为荣
- 以创造接口为耻，以复用现有为荣
- 以跳过验证为耻，以主动测试为荣
- 以破坏架构为耻，以遵循规范为荣
- 以假装理解为耻，以诚实无知为菜
- 以盲目修改为耻，以谨慎重构为荣

## Documentation
- Keep one canonical source per fact within the same project — don't spread the same rule or concept across multiple files.
- Obey the document reference hierarchy:
  - Goals and specs must reference the docs they govern.
  - Concepts and glossaries are referenced by others; no other doc may redefine the same term.
  - Skills are atomic and independent of each other, except within a shared workflow.
  - Scratch drafts are process artifacts — nothing should reference them.
  - AGENTS.md and user-goals.md are harness config — no doc should reference them.
- Write docs for durability — avoid embedding transient state or concrete implementation details; examples should not be version-specific.

## Absolutely forbidden — never execute, not even with permission granted
- `git reset --hard`
- `git add -f` / `git add --force`
- `git push -f` / `git push --force` / `git push --force-with-lease`
- Killing all processes system-wide (e.g. `kill -9 -1`, `taskkill /F /IM *`, `Stop-Process -Name *`)
- Killing all instances of the same program at once (e.g. `pkill`, `killall`, `taskkill /F /IM node.exe`, `Stop-Process -Name "node.exe"` — any command that targets by name without PID filter)

## Forbidden unless user explicitly confirms after asking
- `rm -rf` on a non-empty directory
- Killing a specific process by PID (e.g. `kill <pid>`, `taskkill /PID <pid>`, `Stop-Process -Id <pid>`)
- `git revert <commit>`
