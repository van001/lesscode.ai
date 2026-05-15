# Kaya Experience Protocol RFC v0.1

## Declarative Experience Rendering Protocol

> Kaya makes semantic meaning visible.

---

## 1. Purpose

Kaya defines how semantic meaning becomes user experience.

Kaya does **not** mandate one fixed JSON structure. It defines principles, vocabulary, constraints, and examples for describing renderable experiences using reusable building blocks.

A Kaya implementation may use JSON, YAML, database records, generated schemas, or another declarative format, as long as the implementation preserves the core principles.

---

## 2. Core Principle

Kaya experiences should be built from reusable declarative blocks.

A block may describe:

- an element
- a composite UI unit
- a form
- a list
- a grid
- a spreadsheet
- a workflow step
- a page section
- a full page
- a Maya MFE view

Kaya should allow the same semantic meaning to render differently across:

- static websites
- dynamic applications
- mobile views
- admin tools
- customer-facing flows
- AI-readable pages

---

## 3. Relationship to Karma and Maya

Karma defines meaning.

Maya defines placement and orchestration.

Kaya defines realization.

```text
Karma = what action means
Kaya  = how it is experienced
Maya  = where it lives and how it changes
```

Example:

```text
request.appointment
```

Karma defines the backend meaning.

Kaya defines the form, steps, buttons, labels, success state, and rendering behavior.

Maya decides whether that experience appears in a homepage CTA, modal, app slot, or MFE view.

---

## 4. Building Block Guidelines

A Kaya implementation SHOULD support small reusable blocks.

### 4.1 Element Blocks

Element blocks are low-level user interaction units.

Examples:

```text
input
textarea
dropdown
choice
checkbox
radio
date
time
upload
button
link
image
text
richText
```

### 4.2 Composite Blocks

Composite blocks combine elements into larger reusable experiences.

Examples:

```text
form
stepper
modal
accordion
card
list
grid
table
spreadsheet
carousel
gallery
detail
editorial
dashboard
```

### 4.3 Domain Blocks

Domain blocks are reusable blocks specialized for an industry or business domain.

Examples:

```text
appointmentRequest
refillRequest
reviewCard
inventoryLotsGrid
jobApplication
invoiceApproval
```

Domain blocks SHOULD still be composed from generic element and composite blocks whenever possible.

---

## 5. Actions

Kaya blocks may expose actions.

An action may:

- invoke a Karma action
- open a CTA
- navigate to a page
- switch a Maya MFE view
- refresh the current view
- publish an event
- open a modal
- submit a form
- load a list
- show a detail view

Example:

```json
{
  "type": "button",
  "label": "Request Appointment",
  "action": {
    "kind": "karma",
    "target": "request.appointment",
    "onSuccess": {
      "kind": "view",
      "target": "#appointment/confirmation"
    }
  }
}
```

---

## 6. Forms and CTAs

Kaya SHOULD support declarative forms.

Forms may include:

- fields
- groups
- steps
- validation hints
- conditional visibility
- defaults
- prefill rules
- success views
- error views
- submit actions

Example:

```json
{
  "name": "appointmentRequest",
  "type": "cta",
  "karma": "request.appointment",
  "presentation": "modal",
  "steps": [
    {
      "title": "Your Info",
      "fields": ["client.name", "client.email", "client.phone"]
    },
    {
      "title": "Pet Info",
      "fields": ["pet.name", "pet.species"]
    },
    {
      "title": "Visit Details",
      "fields": ["reason", "preferredDate", "timeOfDay"]
    }
  ]
}
```

---

## 7. Lists, Grids, and Spreadsheets

Kaya SHOULD support collection rendering.

Collections may render as:

- list
- card grid
- table
- spreadsheet
- gallery
- carousel
- Kanban-style board

Example:

```json
{
  "name": "inventoryLots",
  "type": "spreadsheet",
  "source": "inventory.lots",
  "columns": [
    "lotNumber",
    "quantity",
    "expiryDate",
    "location"
  ],
  "actions": [
    {
      "label": "Add Lot",
      "kind": "karma",
      "target": "create.inventoryLot"
    }
  ]
}
```

---

## 8. Static Site Rendering

Kaya MAY be used to render public static pages.

Static pages SHOULD remain:

- SEO-readable
- AI-readable
- fast
- shareable
- canonical

Examples:

```text
home page
service page
team page
feed story
review page
job page
```

Static rendering is a projection of the same semantic system, not a separate architecture.

---

## 9. Dynamic App Rendering

Kaya MAY be used inside Maya MFEs to render secured dynamic applications.

Examples:

```text
admin queues
appointment workflows
CRUD editors
approval dashboards
inventory screens
client portals
```

Dynamic app rendering SHOULD support:

- view changes
- refreshes
- async state
- permissions
- personalization
- events
- workflow-driven transitions

---

## 10. Themes, Skins, and Personality

Kaya SHOULD separate structure from presentation.

A Kaya experience may be affected by:

- layout
- CSS
- skin
- theme
- personality
- device
- user context
- tenant configuration

The same semantic block may render differently for different contexts.

---

## 11. Extension Model

Kaya SHOULD be extensible.

Implementations may add:

- new elements
- new composite blocks
- new domain blocks
- new presentation modes
- new action types
- new templates
- new rendering engines

without changing the core protocol philosophy.

---

## 12. Design Philosophy

```text
Define small.
Compose upward.
Render dynamically.
Reuse everywhere.
```

Kaya does not try to hardcode every possible screen.

It defines the building blocks from which screens emerge.

---

## 13. Closing

Kaya is the realization layer.

It turns semantic meaning into experience.

Karma defines what the action means.

Maya decides where the experience lives.

Kaya makes it visible.
