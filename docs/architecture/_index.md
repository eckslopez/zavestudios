---
title: "Architecture"
weight: 30
---

ZaveStudios is built around a baseline path: workloads declare intent, and the platform supplies the secure delivery and runtime mechanics.

The architecture brings DevSecOps, secure data engineering, data pipelines, and operational AI into one governed shape. Shared platform services provide delivery, data-service integration, observability, policy, and model access through consistent interfaces.

## The Platform at a Glance

Four layers, from the metal up. Each is opened in its own view.

```mermaid
flowchart TB
  dev["<b>Tenant Developer</b><br/><i>[Person]</i>"]
  op["<b>Platform Operator</b><br/><i>[Person]</i>"]
  agent["<b>Coding Agents</b><br/><i>[Person]</i>"]

  subgraph zave["ZaveStudios Platform &nbsp; [Software System]"]
    t4["<b>Tenant Workloads</b>"]
    t3["<b>Platform Services</b>"]
    t2["<b>2 · Inside the Cluster</b><br/>k3s control plane, Flux reconciliation, admission policy"]
    t1["<b>Infrastructure and Ingress</b><br/>libvirt VMs, cluster nodes, network, Istio gateway"]
    t4 --- t3
    t3 --- t2
    t2 --- t1
  end

  gh["<b>GitHub</b><br/><i>[External]</i><br/>repos, Actions, images"]
  cf["<b>Cloudflare</b><br/><i>[External]</i><br/>DNS, tunnel, edge TLS"]

  dev   -- "declares intent" --> t4
  op    -- "merges change" --> gh
  agent -- "proposes change" --> gh
  gh -- "supplies desired state to" --> t2
  cf -- "routes traffic to" --> t1

  classDef person   fill:#ffffff,stroke:#052e56,color:#fff
  classDef layer    fill:#ffffff,stroke:#0b4884,color:#fff
  classDef external fill:#ffffff,stroke:#6b6b6b,color:#fff
  class dev,op,agent person
  class t1,t2,t3,t4 layer
  class gh,cf external
  style zave fill:#f4f8fc,stroke:#1168bd,stroke-width:2px,color:#0b4884
```

Nobody changes the platform by touching it. Intent is declared, change is
merged, and the cluster pulls what Git says should be true.

Notation follows the [C4 model](https://c4model.com/): people, the system in
scope, and external systems, with each relationship labelled by what it does.

## The Four Views

1. **Substrate and Ingress** — VMs, cluster nodes, network, and how external
   traffic reaches a workload
2. **Inside the Cluster** — the control planes, and what owns state at each
3. **Platform Services** — the shared capabilities tenants consume
4. **Tenant Workloads** — what actually runs, and how it is registered
