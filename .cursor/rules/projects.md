# Learning Workspace — Project Context

This workspace is used to study, experiment with, and contribute to open-source projects.
All repos live under `repos/`. Notes live under `notes/`.

---

<!-- Add new project blocks below using the format:

## <project-name> (`repos/<project-name>`)

**What it is:** <1-2 sentence description>

**Language/Runtime:** <language, runtime version, package manager>

**Key commands:**
```bash
cd repos/<project-name>
<install command>
<build command>
<test command>
```

**Upstream remote:** `<git URL>`

**Notes:** `notes/<project-name>/`

---
-->

## PR Workflow

1. Fork the upstream on GitHub under your account
2. Add your fork as `origin`: `git remote add origin git@github.com:<you>/<repo>.git`
3. Keep upstream as `upstream` (already set by clone)
4. Branch off `upstream/main`: `git checkout -b feat/my-change upstream/main`
5. Push to your fork: `git push -u origin feat/my-change`
6. Open PR against the upstream repo via `gh pr create`

## Git Worktrees (parallel work on same repo)

To work on two branches of the same repo simultaneously without switching:
```bash
cd repos/<project>
git worktree add ../<project>-pr2 -b fix/other-thing
```
The worktree appears as `repos/<project>-pr2/` and is fully independent.
