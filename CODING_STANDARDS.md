# Coding Standards

## Purpose

This document defines development standards for Evnetic OS.

The objective is to maintain:

* readability.
* maintainability.
* scalability.
* consistency.

---

# General Principles

## 1. Prefer simplicity

Code should solve the current problem without unnecessary complexity.

Avoid premature abstraction.

---

## 2. Explicit is better than implicit

Code should communicate intent.

Prefer:

```go
CreateMission()
```

over:

```go
Process()
```

---

## 3. Separation of Responsibilities

Each module must have a clear responsibility.

Avoid:

* business logic inside controllers.
* infrastructure logic inside domain models.
* UI logic inside API clients.

---

# Architecture Rules

Evnetic OS follows:

* Domain Driven Design principles.
* Clean Architecture.
* API First development.

Dependency direction:

```
Interfaces

↓

Application

↓

Domain

↓

Infrastructure
```

---

# Naming

Use meaningful names.

Bad:

```
data.go
manager.go
helper.go
```

Better:

```
mission_repository.go
telemetry_processor.go
device_registry.go
```

---

# Error Handling

Errors must provide context.

Bad:

```
error
```

Better:

```
failed creating mission: robot unavailable
```

---

# Logging

Logs must be structured.

Example:

```json
{
 "event":"mission_created",
 "mission_id":"123",
 "robot_id":"001"
}
```

Avoid:

```
printf("error")
```

---

# Configuration

Configuration must come from environment or configuration files.

Never hardcode:

* URLs.
* credentials.
* tokens.

---

# API Changes

Breaking API changes require:

* documentation update.
* migration strategy.
* ADR when architectural impact exists.

---

# AI Generated Code

AI assistants may be used.

However:

Generated code must:

* follow architecture.
* include tests.
* be reviewed.
* respect security rules.

AI is a development accelerator, not an architectural authority.
