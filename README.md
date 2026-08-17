# my-agents-md

English | [中文](README.zh.md)

[![skills.sh](https://img.shields.io/badge/skills.sh-my--agents--md-8A2BE2)](https://www.skills.sh/skills/etavioxy/my-agents-md)

My personal AGENTS.md, including skills for documentation conventions.

## Features

AGENTS.md conventions (defaults):

- Skills as knowledge base: grep the full set of .md files in the skills directory for any unfamiliar concept.
- Numeric constraints: obey literally — list exactly that many, write exactly that many words, no more no less.
- Documentation conventions: organized by a reference hierarchy — concepts/glossaries are referenced, never redefined; drafts are process artifacts, referenced by nothing; one canonical source per fact; written for durability.
- Forbid irreversible actions: e.g. `git reset --hard`, `push -f`, killing processes — unless the user explicitly confirms.

Skill conventions (emphasized after mistakes):

- Follow skill conventions: distinguish Skill vs Notes by SKILL.md link reachability; sub-documents disclose progressively.
- Naming inspiration: for naming and path decisions, always propose multiple options with a recommendation, and require user confirmation.
- Stage gates: guide the agent to divide the task into stages itself — one stage at a time, each with independent permissions, plus explicit pre-task prompts.

## Skills

- [skill-authoring](skills/skill-authoring/SKILL.md) — Skill vs Notes distinction, SKILL.md as entry with progressive disclosure
- [conversation-flow](skills/conversation-flow/SKILL.md) — dialogue stage gates, feedback loop, pre-task stack push

## License

[MIT](LICENSE)
