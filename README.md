
# Maya • Karma • Kaya

> The Art of Building Living Software

## Philosophy

```text
Maya  = imagination / possibility / soul
Karma = action / intent / movement
Kaya  = realization / experience / body
```

Maya dreams.
Karma moves.
Kaya becomes visible.

---

# Maya — Composition & Orchestration

Maya is the composition and orchestration layer.

It defines:
- layouts
- slots
- rendering regions
- MFE boundaries
- recursive containers
- orchestration behavior

Every Maya MFE may contain:
- one or more views
- one or more Kaya blocks
- nested MFEs
- recursive slots

Default view:

```text
#mfe/main
```

Additional views:

```text
#mfe/loading
#mfe/form
#mfe/confirmation
#mfe/error
```

The slot remains stable.

Only realization changes.

Maya orchestrates everything dynamic all the time.

---

# Karma — Semantic Runtime Protocol

Karma models business intent.

```text
actor + intent + noun
```

Examples:

```text
client + request + appointment
doctor + approve + refill
manager + publish + feed
```

REST models resources.

GraphQL models data shape.

Karma models business meaning and lifecycle.

See:
- karma-rfc.md

---

# Kaya — Declarative Experience Protocol

Kaya is the realization layer.

Kaya defines reusable declarative building blocks used to render:
- static websites
- operational apps
- Maya MFEs
- workflows
- CRUD systems
- CTAs
- dashboards
- SEO pages

Kaya starts from small reusable primitives and composes upward.

## Element Blocks

```text
input
dropdown
choice
checkbox
radio
date
upload
button
link
text
image
```

## Composite Blocks

```text
form
stepper
modal
accordion
list
grid
spreadsheet
table
carousel
dashboard
```

## Domain Blocks

```text
appointmentRequest
inventoryLotsGrid
reviewCard
jobApplication
invoiceApproval
```

Buttons and links may:
- invoke Karma actions
- trigger CTAs
- switch Maya views
- publish events
- refresh lists
- open modals
- navigate pages

See:
- kaya-rfc.md

---

# Recursive Loop

```text
Maya interaction
        ↓
Karma action
        ↓
Kaya realization
        ↓
Maya view update
```

```text
Maya → Karma → Kaya → Maya
```
