# API Guidelines

## Purpose

Evnetic OS follows an API First development approach.

Interfaces are contracts between components.

---

# API Principles

## 1. Contract First

The process:

```
Define API

↓

Review contract

↓

Generate models

↓

Implement service
```

---

# External APIs

External clients communicate through REST APIs.

Examples:

```
/api/v1/users

/api/v1/devices

/api/v1/missions
```

---

# Internal Communication

Internal services use:

* gRPC.
* Event messaging.

Example:

```
Mission Service

↓

Mission Created Event

↓

Fleet Service
```

---

# Versioning

APIs must support evolution.

Recommended:

```
/api/v1/
```

Breaking changes require:

```
/api/v2/
```

---

# Events

Events represent facts.

Good:

```
MissionCreated
RobotConnected
TelemetryReceived
```

Avoid commands disguised as events.

Bad:

```
ExecuteRobot
```

---

# Event Design

Events must contain:

* identifier.
* timestamp.
* source.
* version.

Example:

```json
{
"type":"MissionCreated",
"version":"1",
"source":"mission-service",
"timestamp":"2026-01-01"
}
```

---

# API Ownership

Every API must have:

* owner domain.
* documentation.
* schema definition.
* tests.

---

# Shared Contracts

Shared models live in:

```
packages/
```

Never duplicate contracts across projects.
