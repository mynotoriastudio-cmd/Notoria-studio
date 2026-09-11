# HANDOFF.md

Use this file only for concise continuation context between substantial sessions or agents. Replace the active handoff when a newer one supersedes it; durable strategy belongs elsewhere.

## ACTIVE HANDOFF

**Date:** 2026-09-11
**From:** ChatGPT
**To:** Claude Code / next ASPAR agent

### Objective
Continue from the shared-memory architecture without asking Majdi to repeat the ASPAR context.

### Read first
1. `ASPAR_CONTEXT.md`
2. `CURRENT_STATE.md`
3. `WORKBOARD.md`
4. Relevant file under `domains/`
5. Relevant ADR under `decisions/` only if the reason/history matters

### Current work
Build and adopt the GitHub Markdown shared memory as the common context layer between ChatGPT and Claude Code.

### Decisions already active
- GitHub Markdown is the durable shared AI/business-context memory.
- Odoo is the intended operational business system.
- Notion is outside ASPAR core infrastructure.
- Supabase is optional technical backend, not mandatory architecture for all work.
- Brand Factory/proprietary concepts remain R&D until validated.
- Monetization and execution take priority over new broad R&D.

### Do not redo
- Do not create another knowledge application or duplicate source of truth.
- Do not rebuild Canva, Odoo or Drive functions in a new system without a concrete unmet requirement.
- Do not turn the shared memory into hundreds of uncontrolled Markdown files.

### Next exact actions
1. Read the shared-memory files and preserve their source-of-truth boundaries.
2. If local/cloud sync is implemented, sync this repository rather than creating a new memory store.
3. Continue commercial execution from the three NOW priorities in `WORKBOARD.md`.

## HANDOFF TEMPLATE

```markdown
**Date:** YYYY-MM-DD
**From:** agent/session
**To:** agent/session

### Objective

### What changed

### Decisions made

### Files changed

### Blockers

### Next exact action
```
