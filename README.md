# g-oss-governance · Lineage & observability (OpenLineage/Marquez)

**Audience:** O&G CIOs/CTOs and data governance leads  
**Goal:** Establish end‑to‑end lineage and run visibility without expensive catalogs.

---

## Executive summary
- **What it is:** **Marquez** is an OpenLineage server that receives lineage events from Airflow/dbt/Trino. It records job runs, datasets, and links between them.  
- **What it replaces:** Heavyweight lineage add‑ons in commercial catalogs.  
- **Outcomes:** Practical lineage that leadership can trust: “what produced this table, when, with which inputs, and did it meet SLOs?”

## Where it fits
```
Airflow/dbt/Trino ----(OpenLineage events)----> Marquez UI/API
```

## What’s included
- Marquez server + Postgres DB.  
- Works with `openlineage-airflow` and dbt’s OpenLineage plugin.

## Pilot SLOs
- **Lineage coverage:** > 80% of scheduled jobs emit lineage.  
- **Run traceability:** every failure links to upstream datasets.

## Security & compliance
- Deploy behind SSO (Keycloak) and network boundaries.  
- Retain lineage history per your data retention policy.

## Cost model
- Light VM footprint; main cost is engineering to wire emitters.

## KPIs for leadership
- % jobs with lineage, mean time to identify bad upstreams, # of RCA reports generated from lineage.

## Quick start
```bash
cp .env.example .env
docker compose up -d
# Marquez: http://localhost:5000
```
