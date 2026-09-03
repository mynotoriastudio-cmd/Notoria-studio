# ASPAR Agent OS

Monorepo de référence pour l’écosystème ASPAR.

## Périmètre

Le dépôt couvre les quatre entreprises actives :

- **ASPAR Business** — conception, structuration, modélisation, CAPEX/OPEX, sourcing, exécution, lancement et pilotage de projets business de A à Z.
- **ASPAR Solutions** — plateforme All-in-One business-first avec POS/ERP, automatisation et ASPAR Agent.
- **ASPAR Building** — conception et exécution de projets physiques : architecture, zoning, 2D/3D, sourcing, équipements, travaux, smart building et ouverture.
- **ASPAR Franchise** — audit, modèle économique, DIP/contrats, SOP, formation, CAPEX/OPEX, redevances, développement réseau et gouvernance.

Le personal branding de Majdi Garbouj reste une identité transversale, pas une cinquième entreprise.

## Source de vérité

- **Supabase** = control plane canonique : marques, workflows, design systems, assets, QA, calendrier éditorial, production, runtimes et décisions.
- **Google Drive** = documents historiques, sources, preuves et archives encore en migration.
- **GitHub** = code, architecture, documentation technique et versioning.
- **Canva** = destination de création/édition lorsque le connecteur est opérationnel.

Principe : **ce qui n’est pas défini dans Supabase ne doit pas être improvisé en production.**

## État live au 2026-09-03

Supabase contient 5 marques actives (4 business + Majdi), 15 workflows, 4 runtimes d’orchestration, 5 design systems, 75 idées éditoriales et un cycle éditorial de 8 semaines. ASPAR Solutions est actuellement le seul design system actif ; Business, Building et Franchise restent en DRAFT. Les runtimes de production critiques ne doivent pas être considérés comme prêts sans smoke test réel.

## Structure

```text
brands/
  aspar-business/
  aspar-solutions/
  aspar-building/
  aspar-franchise/
platform/
supabase/
content-factory/
runtime/
security/
docs/
```

## Règle de production

```text
REQUEST
  -> SUPABASE SOURCE LOCK
  -> PREFLIGHT
  -> PRODUCTION
  -> QA
  -> HUMAN APPROVAL
  -> CANVA / DELIVERY
```

Tout gate critique non prêt doit arrêter la production.

> Le dépôt GitHub porte encore techniquement le nom `Notoria-studio` car le connecteur actuel ne permet pas de renommer un repository. Le contenu de ce dépôt est désormais dédié à **ASPAR Agent OS**.