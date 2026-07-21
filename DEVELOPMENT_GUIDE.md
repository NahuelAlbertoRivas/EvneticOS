# Development Guide

## Evnetic OS

Operating System for Autonomous Machines

---

# 1. Purpose

This document defines the development principles, workflows and engineering practices used to build Evnetic OS.

Evnetic OS is not developed as a single robot application.

It is developed as a modular operating system for autonomous machines, where:

* hardware is replaceable,
* intelligence is distributed,
* capabilities are discoverable,
* applications can evolve independently,
* new devices can integrate without redesigning the platform.

Every technical decision must preserve this vision.

---

# 2. Core Development Principles

## 2.1 Design for evolution

The first implementation must not optimize only for the current prototype.

Every component should consider future scenarios:

* multiple robot types,
* multiple users,
* multiple organizations,
* third-party extensions,
* commercial deployment,
* cloud and offline operation.

The question behind every design decision should be:

"Will this still make sense when Evnetic OS manages thousands of autonomous machines?"

---

# 2.2 Separation of responsibilities

Each layer has a defined responsibility.

## Kairo

Responsible for:

* reasoning,
* planning,
* interaction,
* memory,
* decision support.

Kairo does not directly control hardware.

---

## Cloud Control Plane

Responsible for:

* identity,
* fleet management,
* missions,
* configuration,
* synchronization,
* data management.

---

## Edge Runtime

Responsible for:

* local execution,
* hardware interaction,
* safety enforcement,
* offline operation,
* real-time decisions.

---

## Hardware

Responsible for:

* physical actuation,
* sensors,
* low-level control.

---

# 3. Repository Organization Rules

The repository follows domain ownership principles.

Each top-level directory represents a bounded responsibility.

Example:

```
cloud/

Backend platform services


kairo/

AI agent system


edge/

Physical execution environment


clients/

Human interfaces


sdk/

External ecosystem


packages/

Shared contracts
```

A component should live in the domain that owns its responsibility.

---

# 4. Domain Ownership

Each domain owns:

* its business logic,
* its internal implementation,
* its tests,
* its documentation.

A domain should expose functionality through:

* APIs,
* events,
* SDK contracts.

Internal implementation details should not leak.

---

Example:

Correct:

```
Mission Service

creates mission

↓

Event

↓

Robot Scheduler
```

Incorrect:

```
Mission Service

directly modifies

Robot Database
```

---

# 5. API First Development

All communication between systems must begin with a contract.

The expected workflow:

```
Requirement

↓

API/Event definition

↓

Implementation

↓

Testing

↓

Deployment
```

Contracts are stored in:

```
packages/

├── api-contracts
├── protobuf
├── schemas
└── events
```

---

# 6. Event Driven Communication

Services should communicate asynchronously whenever possible.

Preferred:

```
Service A

creates event

↓

Event Bus

↓

Service B reacts
```

Example:

```
MissionCreated

RobotAssigned

MissionStarted

MissionCompleted
```

This reduces coupling and improves scalability.

---

# 7. Coding Standards

## General rules

All code must prioritize:

* readability,
* maintainability,
* explicit behavior,
* automated testing.

Avoid:

* premature optimization,
* unnecessary abstraction,
* duplicated logic.

---

# 8. Backend Development

Backend services follow Clean Architecture principles.

Structure:

```
service/

├── domain/

├── application/

├── infrastructure/

└── interfaces/
```

Responsibilities:

## Domain

Contains:

* business rules,
* entities,
* value objects.

Should not depend on external systems.

---

## Application

Contains:

* use cases,
* workflows,
* orchestration.

---

## Infrastructure

Contains:

* databases,
* external APIs,
* messaging systems.

---

## Interfaces

Contains:

* REST handlers,
* gRPC endpoints,
* event consumers.

---

# 9. AI Development Principles

Kairo must remain provider independent.

Never:

```
Application

↓

OpenAI API
```

Always:

```
Application

↓

Kairo Provider Interface

↓

AI Provider
```

Possible providers:

* OpenAI,
* OpenRouter,
* Anthropic,
* local models.

---

# 10. Robotics Development Principles

Hardware-specific logic must remain isolated.

Incorrect:

```
Mission Logic

↓

Motor Controller
```

Correct:

```
Mission

↓

Capability

↓

Skill

↓

ROS

↓

Driver

↓

Hardware
```

---

# 11. Capability Based Design

Evnetic OS reasons about capabilities.

Not:

```
Rover Model X
```

But:

```
Capabilities:

navigation

vision

audio

manipulation
```

New hardware should expose capabilities instead of requiring platform modifications.

---

# 12. Testing Requirements

Every component must include appropriate testing.

## Backend

Required:

* unit tests,
* integration tests,
* API tests.

---

## Frontend

Required:

* component tests,
* integration tests.

---

## Mobile

Required:

* unit tests,
* UI tests.

---

## Edge

Required:

* simulation tests,
* hardware validation tests.

---

# 13. Documentation Requirement

Documentation is part of the product.

Every important change must update:

* architecture documentation,
* API documentation,
* decision records.

Architectural changes require an ADR.

Location:

```
docs/decisions/
```

---

# 14. Development Workflow

Standard workflow:

```
Issue

↓

Design discussion

↓

Implementation branch

↓

Pull Request

↓

Review

↓

CI validation

↓

Merge
```

---

# 15. Branch Strategy

Recommended:

```
main

develop

feature/*

fix/*
```

Production releases are generated from stable versions.

---

# 16. Pull Request Requirements

Every Pull Request must include:

* purpose,
* affected components,
* testing performed,
* documentation updates.

---

# 17. AI Assisted Development

AI assistants are considered development tools.

They must follow:

* project architecture,
* coding standards,
* security rules,
* repository conventions.

AI-generated code requires human validation.

---

# 18. Security Principles

Security is mandatory from the beginning.

Requirements:

* secrets never committed,
* authentication everywhere,
* encrypted communication,
* minimum required permissions.

---

# 19. Quality Definition

A feature is complete when:

* code exists,
* tests exist,
* documentation exists,
* deployment process exists,
* monitoring exists.

---

# 20. Final Principle

Evnetic OS is built as infrastructure for autonomous machines.

The goal is not only to make a robot work.

The goal is to create the operating layer that allows many autonomous systems to exist, communicate and evolve.
