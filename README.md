# Learning Workspace

A Cursor-powered workspace for systematically learning open-source projects.

## How it works

This workspace uses Cursor AI skills to guide you through learning any GitHub project
in about 2 hours. The process is structured into 5 stages: onboard, prerequisites,
build/test/run, hands-on exercises, and ecosystem mapping.

### Directory layout

```
learning/
├── .cursor/
│   ├── rules/
│   │   └── projects.md      # Index of all projects you're learning
│   └── skills/
│       ├── learn-project/    # Skill: structured 5-stage project learning
│       └── get-api-docs/     # Skill: fetch API docs via chub CLI
├── notes/                    # Your learning notes (one dir per project)
├── repos/                    # Cloned repositories
├── learning.code-workspace   # VS Code / Cursor multi-root workspace
└── README.md
```

### Quick start

1. Open `learning.code-workspace` in Cursor
2. Ask Cursor: **"I want to learn `<github-url>`"**
3. The `learn-project` skill kicks in and walks you through 5 stages
4. Notes and exercises appear in `notes/<project>/`
5. The cloned repo lives in `repos/<project>/`

### What the skill produces

For each project you learn, you get:

| File | Contents |
|------|----------|
| `notes/<project>/guide.md` | Self-sufficient learning guide (architecture, commands, concepts) |
| `notes/<project>/metadata.md` | GitHub stats, ecosystem links, related projects |
| `notes/<project>/exercises.md` | 3-4 hands-on exercises (10-15 min each) |
| `notes/<project>/notes.md` | Agent action log (when using agent-driven mode) |

### Prerequisites

- [Cursor](https://cursor.sh/) IDE
- Git
- [GitHub CLI](https://cli.github.com/) (`gh`) — for fetching repo metadata
- Language-specific tools as needed (Node.js, Python, etc.)
- Optional: [chub](https://github.com/andrewyng/context-hub) CLI for fetching API docs

### Tips

- Use **agent-driven mode** ("learn this project for me") to have the AI do the heavy
  lifting — it clones, builds, tests, and writes the guide while you review.
- Use **interactive mode** (default) to go stage by stage with confirmation between each.
- The workspace file auto-registers new repos so they appear in the Cursor sidebar.
- The project index (`.cursor/rules/projects.md`) gives the AI persistent context
  about all your projects across sessions.
