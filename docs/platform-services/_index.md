---
title: "Platform Services"
weight: 30
---

Platform services are reusable capabilities available to tenants through governed interfaces.

They provide secure delivery, runtime state management, data services, observability and policy controls, shared model access, and agent runtimes.

## Shared Delivery and Image Builds

Shared delivery validates workload contracts, builds artifacts, and applies consistent security and quality controls. Shared workflows and base images give workloads a predictable route from source to deployable artifact.

## GitOps Runtime Management

GitOps represents desired runtime state and reconciles it into the platform environment. Workload registration, routing, configuration, and service integration remain reviewable and reproducible from declared intent through runtime.

## Data Services and Orchestration

Data services provide governed persistence, isolation, orchestration, and access patterns. Tenants attach these capabilities through platform interfaces and receive consistent provisioning, credentials, policy, and lifecycle behavior.

## Observability, Policy, and Security

Baseline controls provide logs, metrics, traces, identity boundaries, policy enforcement, and runtime security signals. These controls travel with the supported workload path and give tenants and operators a consistent view of health and compliance.

## Shared Model Access

Shared model access centralizes provider connectivity, model profiles, credentials, routing policy, quotas, and tracing. AI-enabled workloads and agent services consume models through one governed platform interface.

## Agent Runtime Services

Agent runtime services support two operating models. [Engineering Agent](https://github.com/zavestudios/engineering-agent) provides operator-directed software engineering. [Autonomous Agent](https://github.com/zavestudios/autonomous-agent) provides persistent, goal-directed, scheduled, and event-directed work.

Both services use shared model access and participate in the same platform-governed delivery and runtime paths as other shared capabilities.

## Consuming a Service

Tenants consume platform services through workload contracts, shared workflow bindings, GitOps state, and platform-owned configuration. Each interface keeps the request focused on the capability while the platform supplies provisioning, integration, governance, and lifecycle mechanics.

## Implementation References

The source repositories implement the services described above:

- [platform-pipelines](https://github.com/zavestudios/platform-pipelines) - shared delivery workflows
- [image-factory](https://github.com/zavestudios/image-factory) - base images and supply-chain primitives
- [gitops](https://github.com/zavestudios/gitops) - desired runtime state and reconciliation
- [pg](https://github.com/zavestudios/pg) - PostgreSQL data service
- [airflow](https://github.com/zavestudios/airflow) - data orchestration service
- [llm-platform](https://github.com/zavestudios/llm-platform) - shared model access
- [engineering-agent](https://github.com/zavestudios/engineering-agent) - operator-directed engineering service
- [autonomous-agent](https://github.com/zavestudios/autonomous-agent) - autonomous agent service

## Related Sections

- [Architecture](../architecture/) - How capability areas fit into the control-plane model
- [Tenant Guide](../tenant-guide/) - How tenants consume platform capabilities
- [Workloads](../workloads/) - Reference workloads that consume platform services
