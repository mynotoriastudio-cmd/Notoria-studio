# ASPAR Knowledge OS — Design

Date: 2026-09-11
Status: APPROVED DIRECTION / DESIGN SPEC
Repository: `mynotoriastudio-cmd/Notoria-studio` (content dedicated to ASPAR Agent OS; repository rename to ASPAR remains an external GitHub settings action)

## 1. Goal

Create a durable, versioned ASPAR knowledge layer so ChatGPT, Claude Code and future agents stop rebuilding context from scattered chats.

The system must preserve decisions, strategy, definitions, current context, assumptions and deprecations without turning GitHub into a duplicate operational database.

## 2. Canonical source hierarchy

This hierarchy is mandatory:

```text
GitHub knowledge/ = décisions, stratégie, définitions, contexte durable
Supabase          = état runtime / données opérationnelles structurées
Drive             = preuves, documents, archives
Notion            = vues / travail humain lorsque pertinent
Chats             = réflexion temporaire, jamais source canonique
```

### Non-duplication rule

If Supabase already owns a live/dynamic value, `knowledge/` must not copy it as an independently maintained value.

GitHub may document:
- the meaning of the field;
- the business rule;
- the decision that created it;
- where the authoritative runtime value lives.

GitHub must not become a second operational database.

## 3. Responsibilities by system

### GitHub `knowledge/`
Owns durable human- and agent-readable context:
- strategic decisions;
- brand definitions;
- offer definitions;
- business rules;
- architectural principles;
- current priorities;
- assumptions;
- deprecated decisions;
- open questions;
- handoff instructions.

### Supabase
Owns dynamic structured state:
- editorial runtime state;
- production states;
- workflows;
- operational records;
- status fields;
- structured execution data;
- runtime configuration where already canonical.

### Google Drive
Owns evidence and file artifacts:
- historical documents;
- source documents;
- contracts and proofs;
- exported deliverables;
- archives still in migration;
- visual and media assets where Drive is the canonical file store.

### Notion
Used only where it adds a useful human working surface:
- views;
- manual working pages;
- knowledge exploration;
- temporary project workspaces.

Notion is not allowed to silently become a competing source of truth for decisions already canonical in GitHub or runtime state canonical in Supabase.

### Chats
Chats are thinking surfaces only.

Any durable outcome from ChatGPT, Claude, Codex or another agent must be extracted into the appropriate canonical system before it is considered retained.

## 4. Information classes

Every durable knowledge item must be classified as one of:

- `FACT` — verified information.
- `DECISION` — explicit active decision.
- `ASSUMPTION` — proposition not yet validated.
- `IDEA` — exploratory concept not approved.
- `TODO` — actionable task.
- `DEPRECATED` — old information or decision no longer active.

### Required metadata for DECISION

Each important decision must include:

```yaml
id: DEC-YYYY-MMDD-NNN
status: ACTIVE | SUPERSEDED | DEPRECATED
area: GROUP | MAJDI | BUSINESS | SOLUTIONS | BUILDING | FRANCHISE | AGENT | GTM | CONTENT | TECH | DATA
created: YYYY-MM-DD
supersedes: optional decision id
source: chat | github | drive | notion | meeting | other
```

A decision is never silently deleted when replaced. It becomes `SUPERSEDED` and points to the replacement decision.

## 5. File architecture

Create the following knowledge layer:

```text
knowledge/
├── 00_INDEX.md
├── 01_GOVERNANCE.md
├── 02_ASPAR_GROUP.md
├── 03_MAJDI_PERSONAL_BRAND.md
├── 10_ASPAR_BUSINESS.md
├── 11_ASPAR_SOLUTIONS.md
├── 12_ASPAR_BUILDING.md
├── 13_ASPAR_FRANCHISE.md
├── 14_ASPAR_AGENT.md
├── 20_OFFERS_AND_MONETIZATION.md
├── 21_GTM_AND_CONTENT.md
├── 30_SYSTEM_ARCHITECTURE.md
├── 40_DECISIONS.md
├── 41_ASSUMPTIONS.md
├── 42_DEPRECATED.md
├── 43_OPEN_QUESTIONS.md
├── 90_CURRENT_STATE.md
├── 91_SESSION_HANDOFF_TEMPLATE.md
└── 99_CHANGELOG.md
```

Root-level `CLAUDE.md` is added as a small routing file, not as a monolithic memory dump.

## 6. Agent reading protocol

### Minimum boot context

Any coding or reasoning agent working on ASPAR must first read:

1. `knowledge/00_INDEX.md`
2. `knowledge/90_CURRENT_STATE.md`
3. the relevant domain file for the task

The agent must not load the entire repository by default.

### Domain routing

Examples:
- ASPAR Business task -> `10_ASPAR_BUSINESS.md`
- ASPAR Agent task -> `14_ASPAR_AGENT.md`
- content task -> `21_GTM_AND_CONTENT.md`
- data architecture task -> `30_SYSTEM_ARCHITECTURE.md`
- unclear historical conflict -> `40_DECISIONS.md` + `42_DEPRECATED.md`

## 7. Write-back protocol

At the end of any substantial reasoning session, the agent produces a `CONTEXT DELTA` containing only changes:

```text
NEW FACTS
NEW DECISIONS
MODIFIED DECISIONS
DEPRECATED ITEMS
NEW ASSUMPTIONS
OPEN QUESTIONS
ACTIONS
```

Only affected canonical files are updated.

No full-memory rewrite is allowed unless explicitly requested.

## 8. Conflict resolution

When two sources disagree:

1. active explicit decision in GitHub wins for durable strategy/definition;
2. Supabase wins for dynamic runtime/operational state;
3. source evidence in Drive is consulted to resolve factual disputes;
4. Notion does not override canonical GitHub/Supabase unless a newer explicit decision says so;
5. chat content never overrides a canonical source automatically.

If a conflict cannot be resolved, record it in `43_OPEN_QUESTIONS.md` instead of guessing.

## 9. Current ASPAR business architecture to capture

The first knowledge snapshot must encode these active principles:

- ASPAR Group is the umbrella.
- Majdi Garbouj is a transversal personal brand and acquisition/authority channel, not a fifth operating company.
- ASPAR Business = project/investment design, study, structuring and development.
- ASPAR Building = physical design and execution.
- ASPAR Solutions = Odoo/POS/ERP/CRM/automation/AI operational layer.
- ASPAR Franchise = network structuring and expansion.
- ASPAR Agent = shared intelligence/action layer, not a fifth company.
- Client-facing ASPAR Agent and internal ASPAR delivery/orchestration engine must not be represented as identical capabilities.
- Proprietary concepts/Brand Factory remain R&D until sufficiently validated.
- Immediate commercial priority is monetization before additional broad R&D.
- Personal-brand services can generate cash through business systems/AI/Odoo/architecture expertise while ASPAR continues to mature.

## 10. Current commercial priority to capture

The current state file must make the following explicit:

- near-term revenue target: build enough sellable work to reach a sustainable monthly income;
- prioritize offers that can be sold and delivered now;
- avoid building new systems without a direct sales/delivery reason;
- content is an acquisition mechanism, not a separate full-time production empire;
- one real proof/case can be adapted across multiple ASPAR vertical angles;
- proprietary café/brand concepts are not positioned as proven franchises until real operating proof exists.

## 11. Relationship with existing repository docs

Existing `docs/` remains the technical documentation layer.

Existing files such as:
- `docs/ARCHITECTURE.md`
- `docs/STATUS.md`
- `docs/SUPABASE_CONTROL_PLANE.md`

must not be replaced by business-memory documents.

`knowledge/` references technical docs when needed and keeps only durable business meaning/context.

## 12. Security and privacy

Never commit:
- passwords;
- API secrets;
- tokens;
- personal identity documents;
- private client credentials;
- sensitive client data that belongs in an authorized operational system.

Knowledge files may contain high-level client/project context only when appropriate and authorized.

## 13. Migration strategy

Historical chat/Notion/Drive material is migrated progressively.

Pipeline:

```text
OLD SOURCE
  -> extract candidate items
  -> classify FACT / DECISION / ASSUMPTION / IDEA / TODO / DEPRECATED
  -> deduplicate
  -> check conflict
  -> write only canonical durable outcome
```

Do not bulk-copy raw chat histories into GitHub.

## 14. Success criteria

The Knowledge OS is successful when:

1. a fresh Claude Code or ChatGPT session can understand the current ASPAR state by reading the index, current state and one domain file;
2. active and deprecated decisions are distinguishable;
3. a user does not need to repeat the same strategic explanation across sessions;
4. dynamic runtime data is not duplicated from Supabase;
5. old contradictory ideas cannot silently become current again;
6. session handoff is deterministic and short;
7. changes are versioned through Git.

## 15. Explicit non-goals

The first implementation will not:
- replace Supabase;
- migrate every historical chat;
- replace Drive;
- replace Notion everywhere;
- build a new vector database;
- build a UI dashboard;
- automate every write-back flow;
- create another repository.

The first implementation is intentionally Markdown-first, versioned, modular and simple.
