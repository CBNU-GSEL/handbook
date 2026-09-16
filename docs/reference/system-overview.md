---
icon: lucide/network
---

# Public system overview

GSEL research computing is built from a small set of components. This page
describes their roles at a level safe to publish; it omits node names,
network addresses, and other operational detail.

```mermaid
graph LR
  Researcher --> Coder
  Coder --> Kubernetes
  Kubernetes --> Storage["Shared research storage"]
```

## Components

- **Researcher** — a GSEL member or approved collaborator, signed in through
  the laboratory's Authentik identity (see [GSEL
  sign-in](../onboarding/gsel-sign-in.md)).
- **Coder** — provisions browser- and SSH-accessible development workspaces
  for interactive work. See the [Coder](../coder/create-workspace.md) pages.
- **Kubernetes** — the cluster orchestration platform that runs Coder
  workspaces.
- **Shared research storage** — read-only access to shared research
  datasets from approved Coder workspaces, separate from your private
  workspace storage.
- **GSEL Compute** — a GSEL service for research computing workloads. Not
  yet available for user access; use a Coder workspace for interactive work
  in the meantime.
