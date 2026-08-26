---
title: "Workloads"
weight: 40
aliases:
  - /applications/
---

Workloads put the platform path to use. Each one consumes the same baseline platform controls while adding secure data engineering, data pipeline, or operational AI concerns on top.

## Tenant Workloads

**[Listings-Ingest](https://github.com/zavestudios/listings-ingest)** demonstrates a non-HTTP data workload: batch ingestion, validation, load stages, and Airflow-style orchestration. It proves that the platform is not limited to web services.

Platform proof point: secure data engineering and data pipeline workloads can run through the same contract, CI/CD, and GitOps path as interactive applications.

**[Panchito](https://github.com/zavestudios/panchito)** demonstrates service-style ETL with API surfaces, asynchronous task processing, and broker/cache pressure through Redis. It helps prove that data workloads often need more than a database.

Platform proof point: shared data-plane capabilities such as Redis should be platform-supported rather than rebuilt per workload.

**[Oracle](https://github.com/zavestudios/oracle)** demonstrates a non-public analytical workload that combines data processing with AI-assisted workflow patterns.

Platform proof point: analytical and AI-assisted workloads can inherit the DevSecOps baseline without requiring public ingress.

## Supporting Examples

**[Rigoberta](https://github.com/zavestudios/rigoberta)** is a compact Rails reference workload. It helps validate contract-backed deployment, PostgreSQL, metrics, and runtime dependency patterns for a conventional web service.

**[TheHouseGuy](https://github.com/zavestudios/thehouseguy)** is a data-backed application that consumes listing data and demonstrates the downstream side of the data pipeline story.

## What These Workloads Prove

Together, the roster exercises several platform expectations:

- every workload enters through the DevSecOps baseline
- data workloads can be batch, service-style, analytical, or downstream consumer apps
- shared services should be adopted through platform paths, not one-off integrations
- the platform should support multiple workload shapes without multiplying delivery mechanics
