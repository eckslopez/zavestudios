---
title: "Infrastructure"
weight: 20
hidden: true
---

Infrastructure is the substrate the platform stands on: Kubernetes, GitOps, ingress, isolation controls, and the environment discipline required to run shared capabilities safely. The point of this layer is to give the platform a stable place to enforce runtime policy, tenant isolation, routing, and service integration while workload owners stay focused on application and data intent.

## What Infrastructure Owns

Infrastructure ownership in ZaveStudios is deliberately narrow and important:

- Kubernetes runtime environments
- GitOps-managed desired state
- namespace, network, and access boundaries
- ingress and shared routing patterns
- the host layer for platform services

This is how the platform keeps delivery and runtime behavior predictable without asking each workload to make infrastructure design decisions.

## Core Layers

**Kubernetes** is the execution layer for workloads and shared services. It provides the place where namespace isolation, policy enforcement, resource controls, ingress, and service connectivity can be applied consistently.

Supporting repository: [kubernetes-platform-infrastructure](https://github.com/zavestudios/kubernetes-platform-infrastructure)

This layer should remain platform-owned. Workloads should not carry cluster-shaping logic in their own repositories.

**GitOps** represents the runtime state the platform intends to exist. That includes workload registration, service integration, routing, and platform capability materialization. It is the reviewable bridge between validated intent and live runtime behavior.

Supporting repository: [gitops](https://github.com/zavestudios/gitops)

GitOps matters here because runtime change should be legible, reviewable, and reproducible rather than hidden in manual operations.

**Environment Automation** work still lives below the GitOps layer: provisioning, host preparation, and environment automation. That work exists to support the platform substrate, not to become an alternate path for application delivery.

Supporting repository: [ansible](https://github.com/zavestudios/ansible)

## Isolation Model

Infrastructure is where isolation becomes real.

- Namespace isolation: workloads run in bounded namespaces with enforced access controls
- Network isolation: communication boundaries are governed through platform-owned policy rather than ad hoc workload rules
- Data isolation: workloads consume data services through approved access paths and tenant-aware controls. The data service itself is a platform capability; the isolation guarantee depends on the infrastructure layer enforcing the boundary consistently

## Portability Constraint

Infrastructure should be replaceable without forcing workload redesign.

That does not mean every environment is identical. It means workloads declare intent at the platform surface, and the infrastructure layer satisfies that intent without leaking environment-specific mechanics back into workload repositories.

This is one of the main reasons the infrastructure boundary has to stay narrow: once environment-specific behavior leaks upward, the platform stops being portable and starts becoming a collection of special cases.

## Why This Matters

Platform services and tenant workloads only stay predictable if the underlying infrastructure remains disciplined.

- Workloads should not invent their own runtime topology.
- Platform services should not rely on hidden manual environment setup.
- GitOps should remain the visible runtime authority.
- The substrate should support the baseline DevSecOps path before any workload-specific specialization is added.

Infrastructure is therefore not a separate concern from the platform story. It is the part that makes the rest of the platform credible.

## Related Sections

- [Architecture](../architecture/) - Where infrastructure sits in the control model
- [Platform Services](../platform-services/) - Shared capabilities that depend on this substrate
- [Operations](../operations/) - Critical path and operating model
