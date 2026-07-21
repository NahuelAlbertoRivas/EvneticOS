# Evnetic OS SDK Guide

## Overview

The Evnetic SDK provides official interfaces to build applications, capabilities and extensions.

The goal is to allow developers to build capabilities, applications and integrations without modifying the operating system core.

---

# SDK Goals

The SDK provides:

- consistency
- security
- compatibility
- version management


---

# SDK Components


## Robot SDK

For hardware manufacturers.


Provides:

- device registration
- communication
- capability declaration


---

## Capability SDK

For creating new capabilities.


Example:

```python

class VisionCapability:

    def detect(self,image):
        pass

```

---

## Extension SDK

For third-party developers.

Allows:

* skills
* agents
* integrations

---

## API SDK

For external applications.

Supports:

* Web
* Mobile
* Enterprise systems

---

# SDK Design Principles

## Stable Interfaces

Internal implementation may change.

Public contracts remain stable.

---

## Version Compatibility

SDK versions follow:

Major.Minor.Patch

Breaking changes require major versions.

---

## Security First

All SDK operations require:

* authentication
* authorization
* auditing

---

# Developer Experience

A developer should be able to:

1. Install SDK.

2. Create extension.

3. Declare capabilities.

4. Test locally.

5. Deploy to Evnetic OS.

---

# Long Term Vision

The SDK transforms Evnetic OS from a product into a platform.

The objective is not only to build autonomous machines.

The objective is to create the operating layer where autonomous machines evolve.