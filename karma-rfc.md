# Karma Protocol RFC v0.1

## Semantic Runtime Protocol for Declarative Business Systems

> Karma models business intent.

---

## 1. Purpose

Karma Protocol defines business actions using reusable semantic primitives.

Core grammar:

```text
actor + intent + noun
```

Example:

```text
client + request + appointment
```

Karma is not a replacement for REST, GraphQL, queues, or events.

Karma defines business meaning.

REST, GraphQL, queues, and events move or expose that meaning.

---

## 2. Core Concepts

### 2.1 Actor

The generic entity performing the action.

Examples:

```text
anonymous
client
user
system
agent
service
device
integration
```

Actor should stay generic.

Do not use `admin` as actor.

Admin is a role/class/privilege level.

---

### 2.2 Role

Business function of the actor.

Examples:

```text
client
staff
doctor
manager
owner
operator
service
support
billing
candidate
```

---

### 2.3 Class

Privilege, tier, trust, or access level.

Examples:

```text
guest
registered
restricted
trusted
privileged
admin
system
```

Classes can also represent future tiers:

```text
free
standard
premium
enterprise
vip
```

---

### 2.4 Intent

The action being performed.

Examples:

```text
request
view
list
create
update
delete
share
apply
approve
publish
schedule
cancel
complete
archive
```

---

### 2.5 Noun

The thing being acted on.

Examples:

```text
appointment
client
record
review
story
feed
job
application
inventory
invoice
payment
task
```

---

### 2.6 State

Lifecycle position of a noun.

Examples:

```text
draft
submitted
reviewing
approved
scheduled
ready
completed
cancelled
published
archived
closed
rejected
```

---

## 3. Runtime Model

Runtime context usually comes from:

- HTTPS request
- JWT claims
- headers
- request body
- tenant configuration
- karma.json

Example JWT claims:

```json
{
  "tenantId": "caminoalto",
  "actor": "client",
  "userId": "user_123",
  "role": "client",
  "class": "registered"
}
```

Runtime checks:

```text
1. Validate tenant
2. Resolve actor, role, class
3. Resolve intent and noun
4. Check ACL
5. Validate schema
6. Execute handler
7. Persist state
8. Run effects
```

---

## 4. karma.json Structure

```json
{
  "version": "0.1",
  "tenantId": "caminoalto",
  "industry": "veterinary",

  "vocabulary": {
    "actors": ["anonymous", "client", "user", "system", "agent"],
    "roles": ["client", "staff", "doctor", "manager", "service"],
    "classes": ["guest", "registered", "restricted", "privileged", "admin"],
    "intents": ["request", "view", "list", "create", "update", "delete", "share", "apply", "approve", "publish", "schedule", "cancel", "complete", "archive"],
    "states": ["draft", "submitted", "reviewing", "approved", "scheduled", "ready", "completed", "cancelled", "published", "archived", "closed", "rejected"]
  },

  "schemas": {
    "appointment": {
      "type": "object",
      "required": ["client", "reason", "preferredDate"],
      "properties": {
        "client": { "type": "object" },
        "pet": { "type": "object" },
        "reason": { "type": "string" },
        "preferredDate": { "type": "string", "format": "date" },
        "timeOfDay": {
          "type": "string",
          "enum": ["morning", "afternoon", "anytime"]
        }
      }
    }
  },

  "nouns": {
    "appointment": {
      "schema": "appointment",
      "states": ["draft", "submitted", "reviewing", "scheduled", "completed", "cancelled"],
      "ownership": true,
      "visibility": "private"
    }
  },

  "karma": {
    "request.appointment": {
      "intent": "request",
      "noun": "appointment",
      "handler": "appointment.request",
      "fromState": [null, "draft"],
      "toState": "submitted",
      "effects": ["notify.staff", "confirm.client", "create.task"]
    }
  },

  "acl": {
    "request.appointment": [
      {
        "actor": "anonymous",
        "roles": ["client"],
        "classes": ["guest"]
      },
      {
        "actor": "client",
        "roles": ["client"],
        "classes": ["registered", "privileged"]
      }
    ]
  },

  "effects": {
    "notify.staff": {
      "type": "email",
      "to": "role:staff"
    },
    "confirm.client": {
      "type": "email",
      "to": "actor.email"
    },
    "create.task": {
      "type": "create",
      "noun": "task"
    }
  }
}
```

---

## 5. ACL Model

ACL is based on:

```text
actor + role + class + condition
```

Example:

```json
{
  "view.record": [
    {
      "actor": "client",
      "roles": ["client"],
      "classes": ["registered", "privileged"],
      "condition": "ownerOnly"
    },
    {
      "actor": "user",
      "roles": ["staff", "doctor"],
      "classes": ["restricted", "privileged", "admin"],
      "condition": "sameTenant"
    }
  ]
}
```

Do not store full ACL on every record.

Each record should store:

```json
{
  "tenantId": "caminoalto",
  "ownerId": "user_123",
  "state": "submitted",
  "visibility": "private",
  "createdBy": "user_123",
  "updatedBy": "user_456"
}
```

Policy lives in `karma.json`.

Ownership and visibility live on the record.

---

## 6. Workflow Model

Each noun defines allowed states.

Each Karma action defines allowed transitions.

Example:

```json
{
  "request.appointment": {
    "fromState": [null, "draft"],
    "toState": "submitted"
  },
  "schedule.appointment": {
    "fromState": ["submitted", "reviewing"],
    "toState": "scheduled"
  },
  "complete.appointment": {
    "fromState": ["scheduled"],
    "toState": "completed"
  }
}
```

This creates a generic workflow engine.

---

## 7. Transport Mapping

Karma can run over:

- REST
- GraphQL
- queues
- events
- internal function calls
- AI-agent actions

Example REST mapping:

```http
POST /karma/request/appointment
Authorization: Bearer <jwt>
```

Example event mapping:

```json
{
  "type": "karma.requested",
  "karma": "request.appointment",
  "tenantId": "caminoalto"
}
```

---

## 8. Appendix A — Suggested Intents

### Interaction

```text
request
share
message
notify
subscribe
unsubscribe
contact
invite
```

### Read

```text
view
list
search
filter
export
download
```

### Mutation

```text
create
update
delete
archive
restore
upload
import
sync
```

### Workflow

```text
approve
reject
assign
schedule
cancel
complete
publish
unpublish
review
submit
```

### Commerce

```text
order
pay
refund
quote
purchase
reserve
release
invoice
```

### Inventory

```text
allocate
transfer
receive
ship
return
restock
consume
scan
adjust
```

---

## 9. Appendix B — Suggested Nouns

### Core

```text
client
user
profile
account
record
document
message
notification
task
workflow
event
session
```

### Veterinary

```text
appointment
pet
record
refill
pickup
story
review
service
team
feed
job
application
```

### Commerce

```text
order
payment
invoice
quote
product
catalog
cart
subscription
refund
```

### Operations

```text
project
task
ticket
approval
report
dashboard
policy
queue
timeline
```

### Inventory

```text
inventory
item
stock
lot
warehouse
location
supplier
shipment
reservation
transfer
```

---

## 10. Appendix C — Suggested States

```text
draft
submitted
reviewing
approved
rejected
scheduled
ready
active
inactive
completed
cancelled
published
unpublished
archived
closed
failed
pending
processing
received
shipped
returned
allocated
released
```

---

## 11. Closing

```text
REST tells the system where.
GraphQL tells the system what data.
Karma tells the system why and what happens next.
```

Karma defines meaning.

Kaya renders experience.

Maya composes the container.
