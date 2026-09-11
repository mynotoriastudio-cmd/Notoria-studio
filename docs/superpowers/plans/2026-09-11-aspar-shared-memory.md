# ASPAR Shared Memory Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a small, versioned Markdown memory that both Claude Code and ChatGPT can read to share ASPAR context without duplicating operational systems.

**Architecture:** Keep five root control files, five domain files, and ADR-style decision records. GitHub stores durable context and decisions; Odoo remains the operational business system; Drive stores heavy evidence/assets; Canva and Blender remain specialist production tools; Notion is outside the core stack.

**Tech Stack:** GitHub, Markdown, Git, Claude Code, ChatGPT.

**Spec:** `docs/superpowers/specs/2026-09-11-aspar-knowledge-os-design.md`

## Global Constraints

- Keep the first implementation intentionally small.
- Do not add a database, dashboard, vector store, or new app.
- Do not duplicate live operational data into Markdown.
- Never commit secrets, passwords, tokens, private client credentials, or sensitive personal data.
- Old decisions are superseded, not silently deleted.
- `WORKBOARD.md` uses only NOW / NEXT / LATER / BLOCKED, with at most three items in NOW.
- Chat history is not canonical until its durable outcome is written to GitHub.

---

### Task 1: Root control files

**Files:**
- Create: `CLAUDE.md`
- Create: `ASPAR_CONTEXT.md`
- Create: `CURRENT_STATE.md`
- Create: `WORKBOARD.md`
- Create: `HANDOFF.md`

**Interfaces:**
- Consumes: current ASPAR strategy and repository documentation.
- Produces: the minimum shared context used by Claude Code and ChatGPT.

- [ ] Create `CLAUDE.md` with the required reading order and write-back rules.
- [ ] Create `ASPAR_CONTEXT.md` with stable group architecture and source-of-truth boundaries.
- [ ] Create `CURRENT_STATE.md` with the current commercial and stack status.
- [ ] Create `WORKBOARD.md` with NOW / NEXT / LATER / BLOCKED and a three-item NOW limit.
- [ ] Create `HANDOFF.md` with a deterministic session handoff template.
- [ ] Verify all five files exist and cross-reference the same architecture.

### Task 2: Domain files

**Files:**
- Create: `domains/business.md`
- Create: `domains/solutions.md`
- Create: `domains/building.md`
- Create: `domains/franchise.md`
- Create: `domains/agent.md`

**Interfaces:**
- Consumes: `ASPAR_CONTEXT.md` and current strategic decisions.
- Produces: focused context loaded only when a task concerns that domain.

- [ ] Create the five domain files with purpose, current offer, status, active constraints, and what is explicitly not claimed.
- [ ] Ensure Business keeps proprietary concepts/Brand Factory in R&D until validated.
- [ ] Ensure Agent distinguishes internal delivery/orchestration from client-facing pilot capabilities.
- [ ] Verify no domain file invents pricing or unvalidated proof.

### Task 3: ADR decision records

**Files:**
- Create: `decisions/0001-notion-out-of-core.md`
- Create: `decisions/0002-github-shared-memory.md`

**Interfaces:**
- Consumes: current architecture decisions.
- Produces: immutable rationale for future agents.

- [ ] Create ADR 0001 recording Notion as legacy/demo/client-use rather than ASPAR core infrastructure.
- [ ] Create ADR 0002 recording GitHub Markdown as the shared durable memory for ChatGPT and Claude Code.
- [ ] Use sections: Status, Context, Decision, Consequences, Supersedes.
- [ ] Verify both ADRs are consistent with `CURRENT_STATE.md`.

### Task 4: Repository verification

**Files:**
- Verify all files above on the default branch.

**Interfaces:**
- Consumes: implemented files.
- Produces: evidence that the structure exists and is internally consistent.

- [ ] Fetch the root directory and both subdirectories.
- [ ] Fetch `CLAUDE.md`, `CURRENT_STATE.md`, one domain file, and both ADRs.
- [ ] Check that no file contains secrets or placeholder text.
- [ ] Check that Notion is outside core, GitHub is shared memory, Odoo is the operational system, and Supabase is optional/technical rather than a mandatory business control plane.
