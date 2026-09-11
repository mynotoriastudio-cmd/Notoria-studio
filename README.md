# ASPAR Agent OS

Repository de référence pour l’écosystème ASPAR.

> Le repository porte encore techniquement le nom `Notoria-studio`. Son contenu est dédié à ASPAR ; le renommage du repository se fait dans les paramètres GitHub.

## Start here

Pour comprendre l’état actuel d’ASPAR, ne reconstruisez pas le contexte depuis les anciens chats ou snapshots techniques.

Lire dans cet ordre :

1. `ASPAR_CONTEXT.md` — architecture et définitions stables.
2. `CURRENT_STATE.md` — état stratégique/commercial actuel.
3. `WORKBOARD.md` — priorités NOW / NEXT / LATER / BLOCKED.
4. `domains/*.md` — contexte du domaine concerné seulement.
5. `decisions/*.md` — ADR expliquant les décisions importantes.
6. `HANDOFF.md` — continuation entre agents/sessions.

Claude Code doit également respecter `CLAUDE.md`.

## ASPAR

- **ASPAR Business** — étude, conception, structuration et développement de projets business/investissement.
- **ASPAR Solutions** — Odoo/POS/ERP/CRM, automatisation, IA et opérations digitales.
- **ASPAR Building** — conception et exécution de projets physiques, zoning, 2D/3D, sourcing, travaux et ouverture.
- **ASPAR Franchise** — structuration, gouvernance et développement de réseaux.
- **ASPAR Agent** — couche d’intelligence/action partagée, pas une cinquième société.
- **Majdi Garbouj** — personal brand transversal et canal d’autorité/acquisition, pas une cinquième entreprise opérationnelle.

## Sources de vérité actuelles

- **GitHub Markdown** = stratégie durable, définitions, décisions, architecture et contexte partagé entre IA.
- **Odoo** = opérations business : CRM, projets, commercial, finance/comptabilité, ventes, POS, stock et autres données opérationnelles pertinentes.
- **Google Drive** = preuves, sources, documents, archives et assets lourds.
- **Canva** = production design.
- **Blender** = production 3D.
- **Supabase** = backend technique optionnel lorsqu’un besoin concret d’application/runtime le justifie.
- **Notion** = legacy/référence/démonstration/missions clients ; hors du core ASPAR.
- **Chats** = surfaces de réflexion temporaires, jamais source canonique à elles seules.

## Documentation technique historique

Le dossier `docs/` contient l’architecture technique et des snapshots construits à différentes étapes du projet. Certains documents peuvent décrire une architecture antérieure centrée sur Supabase.

En cas de conflit sur l’état ou la stratégie actuels, la priorité est :

1. ADR actif dans `decisions/` pour une décision durable ;
2. `CURRENT_STATE.md` pour l’état stratégique courant ;
3. système opérationnel réellement concerné pour les données vivantes ;
4. anciens snapshots `docs/` comme historique/contexte technique.

## Principe

Une fonction doit avoir un propriétaire clair. Ne pas créer un nouvel outil, une nouvelle base ou une nouvelle mémoire si une fonction existante couvre déjà correctement le besoin.

Aucun secret, token, mot de passe ou credential client ne doit être commité dans Git.
