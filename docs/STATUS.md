# ASPAR Agent OS — Status

Snapshot documentaire : 2026-09-03.

## Confirmé

- Supabase `aspar Project` : ACTIVE_HEALTHY.
- 4 marques business ACTIVE : Business, Solutions, Building, Franchise.
- Majdi Garbouj : marque PERSONAL transversale ACTIVE.
- ASPAR Solutions design system : ACTIVE, direction GREEN_ACTIVE, primaire #006B57 APPROVED.
- Business / Building / Franchise design systems : DRAFT, identité primaire UNRESOLVED.
- Production et QA strictes existent dans le schéma Supabase.
- GitHub contient désormais l’ossature ASPAR Agent OS.

## Bloqué / non confirmé

- Renommage GitHub `Notoria-studio` -> `ASPAR-Agent-OS` : fonction non exposée par le connecteur GitHub actuel.
- Canva : routage du connecteur défaillant lors des derniers tests ; ne pas déclarer une création Canva réussie sans résultat réel.
- Runtimes locaux : ne jamais les marquer ACTIVE sans smoke test réel sur le Mac.
- Publication automatique : désactivée par principe pour les premiers tests.

## Priorité d’exécution

1. Terminer ASPAR Solutions bout-en-bout.
2. Sécuriser/authentifier les workers.
3. Obtenir un smoke test réel renderer + LangGraph.
4. Activer uniquement les workflows/profiles réellement prêts.
5. Connecter Canva et valider le flux éditable.
6. Résoudre les design systems Business, Building et Franchise.
7. Migrer/archiver les dernières sources Drive critiques avant toute suppression.