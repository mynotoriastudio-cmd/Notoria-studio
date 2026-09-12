# HANDOFF.md

Use this file only for concise continuation context between substantial sessions or agents. Replace the active handoff when a newer one supersedes it; durable strategy belongs elsewhere.

## ACTIVE HANDOFF

**Date:** 2026-09-12
**From:** ChatGPT
**To:** Claude Code / next ASPAR agent

### Objective
Use the verified LangGraph + LangChain pre-execution gate as the mandatory entry point for local Claude Code/MCP and downstream Canva/image/social execution.

### Read first
1. `ASPAR_CONTEXT.md`
2. `CURRENT_STATE.md`
3. `WORKBOARD.md`
4. `docs/superpowers/specs/2026-09-12-langgraph-langchain-preexecution-gate-design.md`
5. Relevant brand `SOURCE_LOCK.md`

### What changed
- Added executable package under `src/aspar_agent/`.
- Added LangChain tools for brand resolution and SOURCE_LOCK evaluation.
- Added LangGraph conditional PASS/STOP orchestration.
- Added in-memory checkpointing and optional PostgreSQL checkpoint support.
- Added `langgraph.json` and LangGraph CLI development dependency.
- Added automated tests and smoke runner.
- Added GitHub Actions verification workflow.

### Verification evidence
GitHub Actions on Python 3.12 completed successfully:
- `7 passed in 0.37s`;
- smoke result: `{"pass_path": "PASS", "status": "ok", "stop_path": "STOP"}`;
- LangChain, LangGraph, LangGraph CLI/in-memory runtime and Postgres checkpoint packages installed successfully in CI.

### Decisions made
- Pre-execution safety/routing is deterministic and does not require an LLM.
- The graph flow is `intake -> classify -> resolve_role -> resolve_brand -> source_router -> retrieve_context -> validate -> SOURCE_LOCK PASS/STOP -> plan -> execute(preflight) -> QA -> writeback`.
- STOP bypasses plan/execute.
- `execute` is intentionally `preflight_only`; actual Canva/image/social side effects stay downstream.
- Majdi visual tasks require canonical Canva + Drive source records or STOP.
- Factual/stat/KPI claims require verified evidence or STOP.
- PostgreSQL persistence is optional; tests/local smoke use in-memory checkpointing.

### Blockers
- No blocker for the core gate itself.
- Local Mac/Claude Code/MCP caller wiring is not verified from this cloud session.

### Next exact action
On the local ASPAR repository after syncing `aspar-shared-memory`:
1. Install dependencies: `python -m pip install -e ".[dev,postgres]"`.
2. Preserve any existing secret `.env`; use `.env.example` only as a schema/reference.
3. Run `python -m pytest -q`.
4. Run `python -m aspar_agent.smoke`.
5. Start local LangGraph development server with `langgraph dev --no-browser`.
6. Make Claude Code/MCP/downstream executors call this gate before Canva/image/social actions.
7. Do not bypass SOURCE_LOCK for visual or factual-claim tasks.

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
