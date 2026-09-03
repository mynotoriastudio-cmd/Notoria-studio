# Architecture — ASPAR Agent OS

## 1. Principe

ASPAR Agent OS sépare la vérité métier, l’orchestration et l’exécution.

```text
USER / CHATGPT / CLAUDE
        |
        v
SUPABASE CONTROL PLANE
        |
        +--> SOURCE LOCK / BRANDS / DESIGN / EDITORIAL
        +--> WORKFLOWS / QA / PREFLIGHT / APPROVALS
        |
        v
LANGGRAPH / ORCHESTRATION
        |
        v
LOCAL WORKERS + CONNECTORS
        |
        +--> RENDER
        +--> CANVA
        +--> ODOO
        +--> CHANNELS
```

## 2. Domaines

Les quatre entreprises sont isolées comme domaines mais partagent le même socle technique.

```text
ASPAR Business  ----\
ASPAR Solutions -----+--> ASPAR Agent OS
ASPAR Building  -----+
ASPAR Franchise ----/
```

Majdi Garbouj est une identité personnelle transversale et non une cinquième entreprise.

## 3. Supabase

État observé au 2026-09-03 :
- projet `aspar Project` ACTIVE_HEALTHY ;
- 5 marques ACTIVE ;
- 5 design systems ;
- 15 workflow definitions ;
- 4 orchestrator runtimes ;
- control plane de production avec contracts, preflight, QA, render et approvals ;
- couche éditoriale avec collections, idées, roadmap, plan, stratégie 8 semaines et performance reviews.

Supabase reste la source canonique pour les états dynamiques. GitHub documente les contrats et contient le code, mais ne duplique pas les données métier vivantes.

## 4. Production stricte

```text
SOURCE LOCK
 -> BRIEF
 -> PREFLIGHT
 -> COPY/STORYBOARD
 -> ASSET ROUTING
 -> GENERATIVE BASE (si autorisée)
 -> DETERMINISTIC COMPOSITION
 -> QA
 -> HUMAN APPROVAL
 -> CANVA/DELIVERY
```

Conditions STOP : workflow non ACTIVE, production profile non ACTIVE, runtime requis non ACTIVE, asset canonique absent, typographie requise non résolue ou QA blocker.

## 5. Sécurité

- aucun secret ou clé API dans Git ;
- `.env` ignoré ;
- service-role Supabase interdit dans le client ;
- workers avec permissions minimales ;
- aucune publication automatique par défaut ;
- validation humaine finale conservée ;
- localhost non exposé publiquement sans architecture explicitement approuvée.

## 6. Priorité

ASPAR Solutions est la verticale à terminer bout-en-bout en premier. Les autres design systems restent DRAFT tant que leurs décisions canoniques ne sont pas résolues.