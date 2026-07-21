# SDK Guide

## Overview

The Evnetic SDK provides tools and interfaces for extending Evnetic OS.

The goal is to allow developers to build capabilities, applications and integrations without modifying the operating system core.

---

# SDK Components

## Robot SDK

For hardware integrations.

Allows:

* device registration.
* capability exposure.
* communication.

---

## Capability SDK

For creating new capabilities.

Example:

```
Navigation Capability

Vision Capability
```

---

## Extension SDK

For third-party modules.

Allows:

* skills.
* applications.
* agents.

---

## API SDK

For external integrations.

Provides:

* authentication.
* API clients.
* event handling.

---

# SDK Principles

## Stable Interfaces

Public interfaces must evolve carefully.

---

## Versioning

All SDK components require semantic versioning.

Example:

```
1.0.0
```

---

## Documentation

Every SDK component requires:

* examples.
* API reference.
* migration guides.

---

# Developer Experience Goal

The final ecosystem should allow:

```
Developer

↓

Evnetic SDK

↓

Extension

↓

Evnetic OS

↓

Autonomous Machine
```
