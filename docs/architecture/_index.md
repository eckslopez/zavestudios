---
title: "Architecture"
weight: 30
---

ZaveStudios is built around a baseline path: workloads declare intent, and the platform supplies the secure delivery and runtime mechanics.

The architecture brings DevSecOps, secure data engineering, data pipelines, and operational AI into one governed shape. Shared platform services provide delivery, data-service integration, observability, policy, and model access through consistent interfaces.

## System Context

Who touches the platform, and what it depends on.

```mermaid
C4Context
  title System Context diagram for the ZaveStudios Platform

  Person(dev, "Tenant Developer", "Declares workload intent. Owns application and data behaviour.")
  Person(op, "Platform Operator", "Reviews and merges change. Does not mutate the cluster directly.")

  System_Ext(agent, "Coding Agents", "Automated contributors. Propose change as pull requests, never applied directly.")

  System(platform, "ZaveStudios Platform", "On-prem k3s. Supplies secure delivery, policy, observability, and runtime mechanics to tenant workloads.")

  System_Ext(gh, "GitHub", "Repositories, Actions, and container images. The system of record for desired state.")
  System_Ext(cf, "Cloudflare", "DNS, tunnel, and edge TLS termination. External traffic enters here.")

  Rel(dev, platform, "Declares intent to")
  Rel(op, gh, "Merges change into")
  Rel(agent, gh, "Proposes change to")
  Rel(gh, platform, "Supplies desired state to", "Flux, pull-based")
  Rel(cf, platform, "Routes external traffic to", "HTTPS")

  UpdateLayoutConfig($c4ShapeInRow="3", $c4BoundaryInRow="1")
```

Nobody changes the platform by touching it. Intent is declared, change is
merged, and the cluster pulls what Git says should be true. That is why the
operator and the coding agents point at GitHub rather than at the platform —
only the tenant developer addresses it directly.

Notation follows the [C4 model](https://c4model.com/). This is a Level 1
context diagram, so the platform is deliberately a single box: it shows who
uses it and what it depends on, and nothing about how it is built. The views
below open it up.

## The Four Views

Four layers, from the metal up. Each is opened in its own page.

1. **Substrate and Ingress** — VMs, cluster nodes, network, and how external
   traffic reaches a workload
2. **Inside the Cluster** — the control planes, and what owns state at each
3. **Platform Services** — the shared capabilities tenants consume
4. **Tenant Workloads** — what actually runs, and how it is registered
