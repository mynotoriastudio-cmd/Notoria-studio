# CLAUDE.md — ASPAR shared memory router

This repository contains the durable shared context for ASPAR.

## Mandatory reading order
Before substantial work:
1. Read `ASPAR_CONTEXT.md`.
2. Read `CURRENT_STATE.md`.
3. Read `WORKBOARD.md`.
4. Read only the relevant `domains/*.md` file(s).
5. Read ADRs in `decisions/` only when a decision or historical conflict matters.
6. For any brand/design/content task, resolve the relevant brand SOURCE LOCK before execution.

Do not load every file by default.

## Mandatory personal-brand preflight
For any task involving Majdi Garbouj personal branding, first read:
`brands/majdi-personal-brand/SOURCE_LOCK.md`

Do not ask the user to resend the visual identity if the canonical sources listed there are accessible and non-conflicting. External visual references may influence composition, hierarchy and rhythm only; they must never override the canonical Majdi palette, typography, signature, logo or approved assets.

## Source-of-truth rules
- GitHub Markdown = durable strategy, definitions, decisions, architecture and shared AI context.
- Odoo = business operations: CRM, projects, commercial activity, accounting/finance, sales, POS, stock and related operational records.
- Drive = heavy files, evidence, source documents and archives.
- Canva = design production.
- Blender = 3D production.
- Supabase = optional technical backend only when a concrete application/runtime need justifies it.
- Notion = legacy/reference/demo/client-use; not ASPAR core infrastructure.
- Chats = temporary reasoning surfaces, never canonical by themselves.

## Write-back protocol
After substantial work:
- update only the files whose durable truth changed;
- record important architecture/business decisions as a new ADR in `decisions/`;
- update `CURRENT_STATE.md` only for current state, not history;
- update `WORKBOARD.md` when execution priority changes;
- write a concise handoff in `HANDOFF.md` when another agent or session must continue.

## Safety and hygiene
Never commit passwords, API keys, tokens, private client credentials, identity documents or sensitive personal/client data.
Never invent missing ASPAR facts. Mark uncertainty explicitly.
Never silently delete an old decision: supersede it with a newer ADR.
