---
title: "Documentation"
weight: 15
hidden: true
---

This section is the source map for the platform's deeper operating material. The public site explains the platform in narrative form; the underlying doctrine, contract, and operating documents live in [platform-docs](https://github.com/zavestudios/platform-docs).

Use this page when you want to go beyond the public overview and inspect how the platform is defined in working documents.

## Platform Documents

The handbook is small enough to read in order. These are listed by precedence: earlier documents constrain later ones.

- [Architectural Doctrine (Tier 0)](https://github.com/zavestudios/platform-docs/blob/main/_platform/ARCHITECTURAL_DOCTRINE_TIER0.md) defines the non-negotiable platform invariants.
- [Control Plane Model](https://github.com/zavestudios/platform-docs/blob/main/_platform/CONTROL_PLANE_MODEL.md) defines the authority layers and where truth lives at each one.
- [Operating Model](https://github.com/zavestudios/platform-docs/blob/main/_platform/OPERATING_MODEL.md) describes how the platform currently works during Formation, including what is implemented and what is still target state.
- [Contract Schema](https://github.com/zavestudios/platform-docs/blob/main/_platform/CONTRACT_SCHEMA.md) defines the workload contract surface field by field.
- [Generator Model](https://github.com/zavestudios/platform-docs/blob/main/_platform/GENERATOR_MODEL.md) covers repository, pipeline, GitOps, and capability generation.

Supporting documents that specialize the above:

- [GitOps Model](https://github.com/zavestudios/platform-docs/blob/main/_platform/GITOPS_MODEL.md) describes how desired state is represented and reconciled.
- [Admission Policy Model](https://github.com/zavestudios/platform-docs/blob/main/_platform/ADMISSION_POLICY_MODEL.md) covers policy authoring and what is enforced versus audited.
- [Observability Model](https://github.com/zavestudios/platform-docs/blob/main/_platform/OBSERVABILITY_MODEL.md) sets ownership and materialization rules for logs, metrics, and traces.
- [Observability Data Flow](https://github.com/zavestudios/platform-docs/blob/main/_platform/observability/OBSERVABILITY_DATA_FLOW.md) shows the runtime shape of that stack: what pushes, what scrapes, where signals are stored.
- [Diagnostic Model](https://github.com/zavestudios/platform-docs/blob/main/_platform/DIAGNOSTIC_MODEL.md) provides the reasoning lens for incidents that cross control-plane boundaries.
- [Repository Taxonomy](https://github.com/zavestudios/platform-docs/blob/main/_platform/REPO_TAXONOMY.md) classifies repositories and their allowed roles.

## Repository Directory

Browse repositories by role in the [Repository Directory](repositories/).

## Working Rule

Use the site to understand the platform quickly. Use [platform-docs](https://github.com/zavestudios/platform-docs) when you need the underlying rule set, contract detail, or governance document itself.
