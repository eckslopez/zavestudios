---
title: "Operations Guide"
weight: 20
---

Operations describes the platform's critical path from declared intent to running workload.

This is not a private runbook. It is the public operating model: how the platform is maintained, where authority lives, and how tenant intent moves through governed delivery and runtime paths.

## Tenant / Workload Onboarding

Onboarding starts with a workload boundary and a small contract surface. The platform should make the supported path obvious before a tenant has to reason about infrastructure.

The goal is a predictable adoption path: create or update a workload contract, bind the repository to shared workflows, register desired state, and attach required platform services through governed interfaces.

## Contract Validation

Contracts are the first authority boundary. They define what the workload is asking the platform to provide.

Validation should catch unsupported runtime values, exposure modes, delivery strategies, capability declarations, and configuration shapes before runtime state is proposed.

## Shared Workflow Binding

Shared workflows keep delivery behavior platform-owned. Tenants should not carry full custom CI/CD logic for standard workload paths.

The workflow layer validates intent, builds artifacts, and prepares changes for the GitOps path. It is a proposal layer, not the final runtime authority.

## GitOps Registration

GitOps represents desired runtime state. Workload registration, service integration, routing, environment configuration, and platform capability materialization should be reviewable and reproducible through Git-managed state.

This keeps the live system anchored to declared intent rather than unmanaged manual changes.

## Platform Service Attachment

Platform services are attached through contracts, workflow bindings, GitOps state, or platform-owned configuration.

The platform owns service mechanics: provisioning, wiring, policy, credentials, observability, and lifecycle behavior. Tenants consume the capability through the supported interface.

## Health and Drift

Runtime health is evaluated by comparing contract intent, GitOps desired state, and live runtime state.

When those layers disagree, operators should inspect the boundary where the mismatch appears: contract validation, workflow output, GitOps reconciliation, runtime objects, or observability signals.

## Platform Evolution

The platform evolves by stabilizing repeated patterns and turning them into reusable capabilities.

Contract changes, new platform services, delivery strategy changes, and runtime capability expansion should move through reviewable change paths with clear compatibility expectations.

## Source References

The canonical rules and implementation references live in source repositories:

- [platform-docs](https://github.com/zavestudios/platform-docs) - governance, contracts, lifecycle, and operating model
- [gitops](https://github.com/zavestudios/gitops) - desired runtime state and reconciliation surface
- [kubernetes-platform-infrastructure](https://github.com/zavestudios/kubernetes-platform-infrastructure) - cluster substrate and shared platform configuration
- [platform-pipelines](https://github.com/zavestudios/platform-pipelines) - shared workflow mechanics
