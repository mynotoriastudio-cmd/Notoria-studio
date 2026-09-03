# Supabase Control Plane

Project ref: `xuvpkhldkeqicdabgvbf` (`aspar Project`).

## Domaines de données

### Production
`content_jobs`, `job_steps`, `assets`, `source_refs`, `deliverables`, `qa_rules`, `qa_results`.

### Design System Graph
`design_systems`, `design_nodes`, `design_tokens`, `design_typography_roles`, `design_components`, `design_layouts`, `design_templates`, `design_references`, `design_rules`, `design_asset_bindings`, versions et approvals.

### Orchestration
`workflow_definitions`, `workflow_steps`, `workflow_step_dependencies`, `workflow_runs`, `workflow_run_steps`, `workflow_checkpoints`, `orchestrator_runtimes`, `orchestrator_commands`, `orchestrator_events`.

### Production stricte
`production_contract_requirements`, `production_contracts`, `production_contract_items`, `production_format_profiles`, `production_preflight_results`, render profiles/runs et QA gate policies.

### Editorial
`editorial_source_snapshots`, `editorial_collections`, `editorial_ideas`, `editorial_roadmap_phases`, `editorial_plan_entries`, `editorial_content_types`, `editorial_strategy_cycles`, `editorial_strategy_slots`, `editorial_performance_reviews`.

## Politique de synchronisation GitHub

GitHub ne contient pas un dump de la base de production. Les migrations SQL versionnées pourront être ajoutées sous `supabase/migrations/`. Les états vivants restent dans Supabase.

## Sécurité

Toutes les tables publiques observées utilisent RLS. Cela ne remplace pas l’audit des RPC `SECURITY DEFINER` ni la vérification des permissions worker. Les credentials ne doivent jamais être commités.