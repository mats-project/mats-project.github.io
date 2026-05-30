# masterjess — Subagent Handoff Files

**Purpose:** These files capture the complete work context for each subagent role in the masterjess project. When re-spawning a subagent in any session (webchat, Telegram, etc.), read the corresponding handoff file first to restore full context.

---

## File Index

| File | Role | Status | Description |
|------|------|--------|-------------|
| `01-research-specialist.md` | Research Specialist | ✅ Complete | Initial research brief, market analysis, SEO keywords, positioning |
| `02-research-copywriter.md` | Research & Copywriter | ✅ Complete | Competitive analysis (7 competitors), emotional triggers, conversion copy |
| `03-webmaster-build.md` | Webmaster (Build) | ✅ Complete | Landing page build (HTML/CSS), design system, 25 improvements list |
| `04-webmaster-general.md` | Webmaster (General) | ✅ Complete | Ongoing maintenance role definition and handoff |

---

## Workflow

These subagents were spawned in dependency order:

```
#01 Research Specialist
    ↓
#02 Research & Copywriter (uses #01 output)
    ↓
#03 Webmaster Build (uses #01 + #02 output)
    ↓
#04 Webmaster General (ongoing, uses #03 output)
```

---

## How to Re-Spawn a Subagent

1. Read the corresponding handoff file for full context
2. Use the "How to Re-Spawn" section's task description as the prompt
3. Spawn via `sessions_spawn` with `taskName` matching the original
4. The subagent will read existing output files and continue from where it left off

### Example (Webmaster Build)
```
sessions_spawn({
  task: "<paste the 'How to Re-Spawn' task description from 03-webmaster-build.md>",
  taskName: "masterjess_webmaster_build",
  label: "masterjess-webmaster-build",
  model: "openrouter/owl-alpha"
})
```

---

## Key Source Files (All Sessions)

| File | Purpose |
|------|---------|
| `index.html` | Landing page (455 lines, 11 sections) |
| `styles.css` | Full stylesheet (1195 lines, mobile-first) |
| `RESEARCH_AND_COPY.md` | Research + competitive analysis + all copy (~500 lines) |
| `PROJECT_STATUS.md` | Current project phase and next steps |

---

## Project Context

- **Project:** masterjess.com — Professional organizing service (residential + commercial)
- **Hosting:** GitHub Pages (static only)
- **Git repo:** mats-project/mats-project.github.io (main branch)
- **Workspace:** `/home/mastercontrol2/.openclaw/workspace/mats/website/masterjess/`
- **Model:** openrouter/owl-alpha
- **Last Updated:** 2026-05-30
