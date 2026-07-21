# Identity Domain

## 1. Overview

The Identity Domain is responsible for managing who interacts with Evnetic OS and what actions each entity is allowed to perform.

Identity is a foundational capability of the platform because Evnetic OS is designed as a multi-user, multi-organization and multi-device ecosystem.

The system must support:

* individual users.
* organizations.
* teams.
* roles.
* permissions.
* authentication.
* authorization.
* service identities.
* device identities.

The Identity Domain does not define business operations. It only establishes:

> Who is requesting an action and whether that entity is allowed to perform it.

---

# 2. Core Concepts

## User

A human identity interacting with Evnetic OS.

Examples:

* operator.
* administrator.
* developer.
* owner.

Example:

```yaml
user:
  id: usr_001
  email: user@example.com
  organization: org_001
```

---

## Organization

The main isolation boundary inside Evnetic OS.

All commercial usage belongs to an organization.

Example:

```
Organization A

├── Users
│
├── Robots
│
├── Applications
│
└── Data
```

This allows future support for:

* companies.
* research institutions.
* individual users.
* enterprise customers.

---

## Role

Defines a group of permissions.

Examples:

```
Owner

Administrator

Operator

Viewer

Developer
```

---

## Permission

The smallest authorization unit.

Examples:

```
robot.read

robot.control

mission.create

mission.cancel

configuration.update
```

Permissions should be explicit and granular.

---

# 3. Authentication

Authentication establishes identity.

Recommended initial implementation:

```
Client

↓

OAuth2 / OpenID Connect

↓

Identity Provider

↓

Access Token

↓

Evnetic APIs
```

Technology:

* Keycloak.
* OAuth2.
* OpenID Connect.
* JWT.

---

# 4. Authorization Model

Evnetic OS uses Role Based Access Control (RBAC).

Example:

```
Operator

Allowed:

✓ View robots
✓ Create missions

Denied:

✗ Modify firmware
✗ Change security policies
```

---

# 5. Device Identity

Machines are first-class identities.

A robot is not only hardware.

It has:

* identity.
* credentials.
* capabilities.
* ownership.
* permissions.

Example:

```yaml
device:
  id: rover_001
  organization: org_001
  certificate: x509
```

---

# 6. Service Boundaries

Identity Domain owns:

✓ users
✓ organizations
✓ roles
✓ permissions
✓ authentication
✓ authorization

Identity Domain does not own:

✗ missions
✗ telemetry
✗ robot behavior
✗ AI decisions

---

# 7. Future Evolution

The Identity Domain should support:

* enterprise SSO.
* external identity providers.
* API keys.
* service accounts.
* delegated permissions.
* marketplace applications.
