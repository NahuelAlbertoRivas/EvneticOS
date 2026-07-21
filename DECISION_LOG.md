# Architecture Decision Log

This document records important architectural decisions.

Format:

* Context.
* Decision.
* Consequences.

---

# ADR-0001

## Title

Evnetic OS Repository Strategy

## Status

Accepted

## Context

Evnetic OS requires a structure that supports:

* rapid MCP development.
* long-term scalability.
* multiple technical domains.

## Decision

Use a hybrid monorepo architecture.

Main domains:

* cloud.
* kairo.
* edge.
* clients.
* sdk.
* packages.

## Consequences

Positive:

* shared contracts.
* easier coordination.
* consistent versioning.

Negative:

* requires strong repository boundaries.

---

# ADR-0002

## Title

Capability-Based Architecture

## Status

Accepted

## Context

Different autonomous machines must share the same platform.

Hardware-specific design would limit scalability.

## Decision

Machines are represented through capabilities.

Example:

```
navigation
vision
audio
manipulation
```

---

## Consequences

Positive:

* hardware independence.
* easier extensions.
* flexible AI reasoning.

---

# ADR-0003

## Title

Kairo as Independent Intelligence Layer

## Status

Accepted

## Context

AI should evolve independently from cloud and hardware.

## Decision

Kairo becomes a first-class domain.

It contains:

* reasoning.
* memory.
* tools.
* providers.
* policies.

---

# ADR-0004

## Title

AI Provider Independence

## Status

Accepted

## Context

External AI providers evolve rapidly.

## Decision

Use provider adapters.

Kairo communicates through an abstraction layer.

---

# ADR-0005

## Title

Cloud-Edge Separation

## Status

Accepted

## Context

Autonomous systems require reliability despite connectivity limitations.

## Decision

Cloud decides objectives.

Edge executes actions.

---

## Consequences

Cloud:

* planning.
* coordination.
* intelligence expansion.

Edge:

* safety.
* execution.
* immediate response.
