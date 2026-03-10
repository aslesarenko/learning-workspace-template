---
name: learn-project
description: >
  Systematically learn a new GitHub project through staged exploration: onboard the
  repo into the learning workspace, understand prerequisites, build/test/run, create
  hands-on exercises, and map the ecosystem. Use when the user wants to learn, study,
  onboard, or explore a new open-source GitHub repository or project.
---

# Learn a GitHub Project

Guides the user through learning a new open-source project in five stages.
Each stage produces a section of a learning guide saved to `notes/<project>/`.

**Time budget: ~2 hours total per project.** Size all content accordingly.

## Workspace conventions

- Repos are cloned to `repos/<project>/`
- Notes are written to `notes/<project>/`
- The workspace file is `learning.code-workspace` (add new folder entries there)
- The project index is `.cursor/rules/projects.md` (add a summary block there)

## Stage overview

| # | Stage | Goal | Time |
|---|-------|------|------|
| 1 | Onboard | Clone repo, register in workspace, collect project metadata | ~10 min |
| 2 | Prerequisites & Getting Started | Map dependencies, toolchain, and first-run instructions | ~15 min |
| 3 | Build / Test / Run | Achieve a working build, green tests, and a minimal running instance | ~30 min |
| 4 | Exercises & Experiments | Prepare short hands-on tasks adapted to the user's environment | ~45 min |
| 5 | Ecosystem & Use Cases | Identify the key use case, related projects, and ecosystem position | ~20 min |

## Output structure

Create the following in `notes/<project>/`:

```
notes/<project>/
├── guide.md          # Main learning guide (one section per stage) — self-sufficient
├── metadata.md       # GitHub stats, links, ecosystem info
├── exercises.md      # Hands-on tasks for Stage 4
└── notes.md          # Agent action log (created in agent-driven mode)
```

### guide.md — authoring principles

The guide must be **self-sufficient**. The user learns by reading the guide itself,
not by following links to external docs. Embed the key facts, concepts, and
explanations directly in each section. Links go in a "Further reading" footer per
stage — they are optional enrichment, never required.

**What to put inline:**
- How the project works (architecture, data flow, core abstractions) — distilled,
  not copy-pasted. Write it in your own words based on reading the source.
- Exact commands with expected output snippets.
- Key config options and what they control.
- Conceptual explanations needed before exercises (e.g., "The plugin system works by…").

**What stays as links only:**
- Full API reference, source files, lengthy design docs.

### guide.md template

Use this structure (fill in during each stage):

```markdown
# Learning Guide — <Project Name>

> One-line description of the project.

| Field | Value |
|-------|-------|
| GitHub | `<owner>/<repo>` (★ stars, forks, last commit date) |
| Website | URL or N/A |
| License | ... |
| Language | ... |
| Package manager | npm / pnpm / pip / cargo / ... |
| **Total time** | **~2 hours** |

## Stage 1 — Onboard (~10 min)

### Key facts
- <What this project is, in 2–3 sentences — not just a tagline>
- <Who maintains it (org, key contributors, governance)>
- <Why it exists — the problem it was created to solve>
- <High-level architecture: main components and how they connect>
- <Concepts overview of the key concept in their interaction, enough to understand overall functionality> 

### Actions
1. <Step-by-step actions the user performs to clone, register, verify>

### Further reading
- <Optional links to README, homepage>

---

## Stage 2 — Prerequisites & Getting Started (~15 min)

### Key facts
- <Runtime/language version required and why>
- <Package manager and workspace layout>
- <Key config files: what each one controls>
- <Environment variables needed and what they do>

### Actions
1. <Steps to install prerequisites, configure environment>

### Further reading
- <Optional links to install guides>

---

## Stage 3 — Build / Test / Run (~30 min)

### Key facts
- <Build system: what it does, what artifacts it produces>
- <Test framework and what the test suite covers>
- <Entry point and startup sequence: what happens when you run it>
- <Minimal config: which settings are required vs optional>

### Actions
1. <Exact commands to build, run tests, start the app>
2. <Expected output / success criteria for each command>

### Further reading
- <Optional links to contributing guide, CI config>

---

## Stage 4 — Exercises & Experiments (~45 min)

### Key concepts
- <Explain the 2–3 core concepts the exercises explore, so the user
  understands them BEFORE starting the exercises. Write full paragraphs
  if needed — this is where the learning happens.>

### Exercises
1. <Summary of each exercise — see exercises.md for full details>

### Further reading
- <Optional links to tutorials, examples directory>

---

## Stage 5 — Ecosystem & Use Cases (~20 min)

### Key facts
- <Primary use case: what problem, who benefits, typical deployment>
- <Ecosystem: parent org, sibling projects, how they fit together>
- <Alternatives: 2–3 competing/complementary projects with one-line comparisons>
- <Community: where discussions happen, contribution model>

### Further reading
- <Curated links to blog posts, talks, awesome lists>
```

---

## Time budget

The entire learning session targets **~2 hours** of the user's time. The agent prepares
most of the material upfront; the user reads and executes. Budget breakdown:

| Stage | User time | Agent prep focus |
|-------|-----------|-----------------|
| 1 — Onboard | ~10 min | Clone, register, write summary the user just reads |
| 2 — Prerequisites | ~15 min | Check env, list only what's missing; user installs |
| 3 — Build / Test / Run | ~30 min | Verify commands work first; user re-runs them to see output |
| 4 — Exercises | ~45 min | 3–4 exercises, 10–15 min each; this is the core learning time |
| 5 — Ecosystem | ~20 min | Curated reading list; user skims, no hands-on work |

**Sizing rules:**
- "Key facts" sections: rich enough to learn from without leaving the guide. Use full
  sentences and short paragraphs where needed. Target 5–15 lines per stage.
- "Actions" sections: numbered steps, each one a single concrete action.
- Stage 4 "Key concepts": this is the deepest section — explain core abstractions in
  enough detail that the exercises make sense. Can be 10–20 lines.
- Exercises: 3–4 total (not more), each achievable in 10–15 minutes.
- "Further reading": 2–4 optional links per stage. These are NOT required reading.
- The entire `guide.md` should be **under 400 lines** of markdown.

## Detailed stage instructions

### Stage 1 — Onboard (~10 min user time)

1. **Clone** the repo into `repos/<project>`:
   ```bash
   cd repos
   git clone <url> <project>
   ```
2. **Add to workspace** — append a folder entry in `learning.code-workspace`.
3. **Add to project index** — append a block in `.cursor/rules/projects.md` following the existing format (What it is, Language/Runtime, Key commands, Upstream remote, Notes).
4. **Collect metadata** by fetching from GitHub (use `gh` CLI or web):
   - Stars, forks, open issues, last commit date, contributors count
   - Website / homepage URL
   - License
   - Topics / tags
   - Whether it belongs to an org/ecosystem
   - Related / sibling repos in the same org
   Save to `notes/<project>/metadata.md`.
5. **Read** the repo's README, CONTRIBUTING, and any ARCHITECTURE / docs files to build context for later stages.
6. **Write** Stage 1 section of `guide.md`. Distill what the project is, why it exists, and its high-level architecture directly into the "Key facts" section. The user should learn this from the guide itself, not from the README.

### Stage 2 — Prerequisites & Getting Started (~15 min user time)

1. **Identify toolchain**: language runtime version, package manager, system dependencies.
2. **Check the user's environment** — run version checks (`node -v`, `python --version`, etc.) and note gaps. Only list what needs action; skip already-satisfied requirements.
3. **List key config files** the user should be aware of (`.env.example`, `config/`, `docker-compose.yml`, etc.).
4. **Document install steps** adapted to macOS (the user's OS). Use `brew install` where possible.
5. **Write** Stage 2 section of `guide.md`. If everything is already installed, this section should be very short ("All prerequisites met — proceed to Stage 3").

### Stage 3 — Build / Test / Run (~30 min user time)

1. **Build** — run the project's build command; capture and document the exact command and expected output.
2. **Test** — run the test suite; document command, expected pass count, any known failures.
3. **Run** — start the project with the simplest or recommended minimal configuration. Document the command, any required env vars, and how to verify it's running (e.g., curl a health endpoint).
4. **Troubleshoot** — if any step fails, diagnose, fix, and document the fix in the guide so the user doesn't hit the same issue.
5. **Write** Stage 3 section of `guide.md`. Include copy-pasteable commands with expected output snippets. Explain what the build produces, what the tests cover, and what the running app does — inline in "Key facts", not via links.

### Stage 4 — Exercises & Experiments (~45 min user time)

Create **3–4** short, self-contained exercises in `notes/<project>/exercises.md`.
This is the most valuable stage — it gets the largest time share.

Each exercise should:
- Have a clear goal (one sentence)
- Take 10–15 minutes
- Include exact commands or code snippets adapted to the user's environment
- Include expected output or success criteria
- Progress from simple to more complex
- **Be runnable from the `notes/<project>/` directory** — the user works from
  where the exercise files live. Use `uv run --project <relative-path-to-repo-package>`
  or equivalent techniques so the user doesn't have to `cd` into the repo and use
  ugly relative paths back to the exercise files.

Good exercise types:
- Modify a config and observe the effect
- Call a key API or CLI command with different arguments
- Write a small script that uses the project's library
- Trace a request through the codebase
- Add a minimal feature or fix a TODO

Write Stage 4 section of `guide.md` with a summary and pointer to `exercises.md`.

### Stage 5 — Ecosystem & Use Cases (~20 min user time)

This is a reading-only stage — no hands-on work. Keep it concise.

1. **Key use case** — one paragraph on the primary problem and who benefits.
2. **Ecosystem position** — is it part of a larger org/framework? What are sibling projects?
3. **Alternatives** — list 2–3 competing or complementary projects (one line each).
4. **Related reading** — curate 3–5 links (blog posts, talks, awesome lists).
5. **Write** Stage 5 section of `guide.md` and update `metadata.md` with ecosystem info.

---

## Workflow

When the user asks to learn a project, follow this process:

```
Task Progress (~2h total):
- [ ] Stage 1: Onboard — clone, register, collect metadata (~10 min)
- [ ] Stage 2: Prerequisites — toolchain, environment check (~15 min)
- [ ] Stage 3: Build / Test / Run — working build and minimal run (~30 min)
- [ ] Stage 4: Exercises — prepare hands-on tasks (~45 min)
- [ ] Stage 5: Ecosystem — use cases, related projects (~20 min)
- [ ] Final: Review guide.md for completeness and size (target <400 lines)
```

**Interactive mode (default):** Work through each stage sequentially. After each stage:
1. Write the corresponding section in `guide.md`
2. Update the checklist
3. Confirm with the user before moving to the next stage

**Agent-driven mode:** Run all stages without pausing. Produce both `guide.md` and
`notes.md`. See "Agent-driven mode" section below for details.

If the user provides a GitHub URL, extract `<owner>/<repo>` and use it as the project identifier. Use the repo name (lowercased, hyphenated) as the `<project>` directory name.

**Pacing:** The agent does the heavy lifting (cloning, building, researching, writing). The user's 2 hours are spent reading the guide and doing the exercises, not waiting for the agent. If a stage would require more user time than budgeted, cut scope rather than exceed the budget.

## Agent-driven mode

When the user asks the agent to "do it all", "run through all stages", "do the actions
yourself", or similar — the agent executes every action itself (clone, install, build,
test, run, exercises) and logs everything to `notes/<project>/notes.md`.
Agent should stop after each stage letting the user to review what has been done.

### How it works

1. The agent works through all 5 stages WITH or WITHOUT waiting for user confirmation between stages depending on how the mode is requested (i.e. "do it all without waiting"). The default mode it WITH WAITING.
2. For each stage, the agent **performs every action** listed in the "Actions" / "What to do"
   section of the guide — running commands, checking output, troubleshooting failures.
3. All actions and results are logged to `notes.md` with a section per stage.
4. The `guide.md` is still produced as normal — the user reads it afterward.
5. At the end, the agent summarizes what succeeded, what failed, and what needs the user's
   attention.
6. If any error/mistake found during execution, and agent learns the fix, the agent should fix the guide so it reflects the reality (e.g. actual commands).

### notes.md format

```markdown
# Action Log — <Project Name>

> Generated by agent on <date>

## Stage 1 — Onboard

- [x] Cloned `<url>` into `repos/<project>/`
- [x] Added to `learning.code-workspace`
- [x] Added to `.cursor/rules/projects.md`
- [x] Collected metadata → `metadata.md`

## Stage 2 — Prerequisites

- [x] Checked Node.js: v20.11.0 ✓
- [x] Checked pnpm: v8.15.0 ✓
- [ ] Missing: Redis — install with `brew install redis`

## Stage 3 — Build / Test / Run

- [x] `pnpm install` — success (142 packages)
- [x] `pnpm build` — success (built in 12s)
- [x] `pnpm test` — 87 passed, 2 skipped, 0 failed
- [x] `pnpm start` — server running on :3000, health check OK
- **Issue encountered:** Port 3000 was in use; killed stale process first.

## Stage 4 — Exercises

- [x] Exercise 1: <title> — completed successfully
  - Output: <key output snippet>
- [x] Exercise 2: <title> — completed successfully
- [ ] Exercise 3: <title> — skipped (requires API key)
  - **User action needed:** Set `OPENAI_API_KEY` in `.env` and retry

## Stage 5 — Ecosystem

- [x] Researched ecosystem, wrote guide section
- [x] Updated `metadata.md`

## Summary

**Completed:** 4/5 stages fully, 1 partially
**User action needed:**
1. Install Redis: `brew install redis`
2. Set `OPENAI_API_KEY` for Exercise 3
```

### Detecting agent-driven mode

Trigger agent-driven mode when the user says any of:
- "do it yourself" / "do it all" / "run all stages"
- "prepare everything" / "set it all up"
- "learn <project> for me" / "go through it yourself"
- Any phrasing that asks the agent to perform the actions rather than write a guide for the user to follow

In this mode, still produce `guide.md` (for the user to read later) but additionally
produce `notes.md` with the full action log.

## Tips

- Prefer `gh repo view <owner>/<repo> --json ...` to fetch GitHub metadata efficiently.
- Use `gh api repos/<owner>/<repo>` for detailed stats.
- When checking prerequisites, actually run the version commands — don't assume.
- Keep guide sections concise: the user wants to read and act, not wade through prose.
- All file paths in the guide should be relative to the workspace root.
- If the project has a Docker setup, mention it but prefer native local setup for learning.
