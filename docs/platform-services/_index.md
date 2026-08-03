---
title: "Platform Services"
weight: 30
---

Platform services are the reusable capabilities that make ZaveStudios more than a collection of workload repositories.

They define what the platform provides to workload owners: secure delivery, runtime state management, data services, observability and policy controls, and shared model access for operational AI.

## Capability Areas

### Shared CI/CD and Image Builds

Workloads should not carry full custom delivery logic. They should consume shared workflows and base image patterns so build, validation, and security behavior stay consistent.

**Supporting repositories:**

- [platform-pipelines](https://github.com/zavestudios/platform-pipelines) - shared GitHub Actions workflows for build, validation, and delivery behavior
- [image-factory](https://github.com/zavestudios/image-factory) - base image and supply-chain primitives for workload runtimes

### GitOps-Managed Runtime State

The platform should represent desired runtime state through Git rather than through unmanaged manual changes. GitOps gives workload adoption a reviewable and reproducible path from declared intent to running system.

**Supporting repository:**

- [gitops](https://github.com/zavestudios/gitops) - desired runtime state and reconciliation surface

### Data Services and Tenant Isolation

Secure data engineering needs more than a database connection. Workloads need governed persistence, isolation, orchestration, and access patterns that can be reused without rebuilding data infrastructure each time.

**Supporting repositories:**

- [pg](https://github.com/zavestudios/pg) - PostgreSQL data capability
- [airflow](https://github.com/zavestudios/airflow) - shared data orchestration capability

### Observability, Policy, and Security Controls

Workloads should inherit telemetry, policy, identity, and security expectations from the platform path. These controls are part of the baseline, not optional add-ons.

**Capability examples:**

- logs, metrics, and traces
- identity and access boundaries
- policy enforcement
- runtime security posture
- evidence that controls apply consistently

### Shared Model Access for Operational AI

Operational AI needs a shared model-access path so provider routing, model profiles, secrets, and future self-hosted inference do not become per-workload decisions.

**Supporting repository:**

- [llm-platform](https://github.com/zavestudios/llm-platform) - shared model-access capability

## Service Consumption Model

Platform services should be consumed through workload contracts, shared workflow bindings, GitOps state, or platform-owned configuration.

The important test is predictability: workload owners should know which capabilities exist and how to adopt them without negotiating custom infrastructure each time.

## Related Sections

- [Architecture](../architecture/overview/) - How capability areas fit into the control-plane model
- [Tenant Applications](../applications/) - Reference workloads that consume platform services
- [Proofs of Concept](../experiments/) - POCs for possible future capabilities
