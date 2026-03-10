# Learning Workspace

A workspace for systematically learning open-source projects. Repos are cloned
into `repos/`, notes are written to `notes/`.

## Workspace layout

```
.cursor/rules/projects.md   — Index of all projects (context for every session)
.cursor/skills/              — Reusable agent skills (see below)
notes/<project>/             — Learning notes per project
repos/<project>/             — Cloned repositories
learning.code-workspace      — VS Code / Cursor multi-root workspace
```

## Project index

The file `.cursor/rules/projects.md` tracks every project in the workspace:
what it is, key commands, upstream remote, and where the notes live. Read it
at the start of any session. Update it when onboarding a new project.

## Skills

Skills are structured workflows the agent follows for specific tasks.
Read the full skill file before acting — don't summarize or skip steps.

| Skill | File | When to use |
|-------|------|-------------|
| **Learn a project** | `.cursor/skills/learn-project/SKILL.md` | User wants to learn, study, onboard, or explore a GitHub project |

### Learn a project (summary)

Five-stage guided learning (~2h total): onboard → prerequisites → build/test/run
→ exercises → ecosystem. Produces `guide.md`, `metadata.md`, `exercises.md` in
`notes/<project>/`. Full instructions in the skill file — always read it first.
