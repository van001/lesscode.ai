# Maya • Karma • Kaya

> *The Art of Building Living Software*

![Maya MFE Architecture](./maya-mfe-architecture.png)

> “Maybe software was never supposed to be static.  
> Maybe it was supposed to evolve like life itself.”

---

## Why I Started Thinking About Software Differently

I started coding more than three decades ago.

I was never fascinated by complexity.

What always interested me was simplicity at scale.

How do you build systems that:

- scale from day one
- remain operationally efficient
- require minimal infrastructure
- stay composable over time
- avoid unnecessary engineering overhead

Back in the early 2000s, I was already building distributed systems designed to handle billions of requests.

Even then, my philosophy stayed surprisingly simple.

Because fundamentally, most software systems are not that complicated.

Whenever humans interact with computers, they are usually doing some variation of:

- creating
- reading
- updating
- deleting
- viewing

```text
CRUD
```

That realization stayed with me for years.

No matter how complicated businesses sounded, most systems eventually reduced into:

- CRUD
- workflows
- orchestration
- notifications
- state transitions
- reactions

The rest was mostly composition and discipline.

---

## The Realization About Time

Applications are fundamentally either:

- synchronous
- asynchronous

Both still use protocols.

The difference is realization timing.

In synchronous systems:

- realization happens immediately

In asynchronous systems:

- realization happens later

```text
        User Action
             |
     ----------------
     |              |
 Synchronous    Asynchronous
     |              |
 Immediate       Delayed
 Realization     Realization
```

Examples of synchronous interactions:

- loading a webpage
- validating a form
- querying a dashboard
- viewing records

Examples of asynchronous interactions:

- ordering from Amazon
- requesting a veterinary appointment
- applying for a job
- payment processing
- enterprise approvals

The protocol exists in both systems.

But asynchronous systems introduce:

- orchestration
- queues
- retries
- workflows
- state transitions
- eventual realization

That realization changed how I thought about software itself.

Most real-world business systems are actually journeys.

```text
request → review → workflow → notification → realization
```

That journey eventually became Karma.

---

## Frontend Engineering Felt Backwards

Ironically, while backend systems became simpler in my mind, frontend systems started feeling more fragmented.

Designers focused on visuals.

Frontend engineers focused on frameworks.

Backend engineers focused on APIs.

Product teams focused on workflows.

But very few people could reason about the experience as one composable semantic system.

And then I realized something important:

Most UI is actually declarative.

Pages are mostly:

- layouts
- slots
- forms
- blocks
- grids
- lists
- interactions
- workflows

Themes can be separated from structure.

Personality can be separated from content.

The same workflow can render completely differently depending on:

- context
- user
- permissions
- business state
- device
- intent

That realization slowly evolved into:

```text
Maya → Karma → Kaya
```

Inspired philosophically by years of reading Vedic philosophy and the Upanishads.

```text
Maya  = imagination / possibility / soul
Karma = action / intent / movement
Kaya  = realization / experience / body
```

Maya dreams.  
Karma moves.  
Kaya becomes visible.

---

## Maya — The Possibility Layer

> “Maya is not the application.  
> Maya is the infinite container of what could exist.”

Maya became the possibility layer.

Not the experience itself.

Not the forms.

Not the business logic.

Possibility.

Maya evolved into a frontend composition architecture capable of orchestrating:

- static websites
- operational applications
- recursive layouts
- slot-based micro frontends
- dynamic rendering regions

```text
                Maya

        Static + Dynamic Reality

      --------------------------------
      |                              |
 Static Layouts              Slot-Based MFEs
      |                              |
 SEO Pages               Recursive Containers
 Landing Pages            Dynamic Composition
 Editorial Views          Operational Apps
      |                              |
      --------------------------------
                    |
            Infinite Possibilities
```

The static side exists for:

- SEO
- AI readability
- customer-facing experiences
- performance

The dynamic side exists for:

- workflows
- operational systems
- personalization
- recursive composition
- living applications

Maya itself does not care what is inside the containers.

It only defines:

- placement
- composition
- rendering boundaries
- slots
- orchestration

---

## The Fractal Realization

Then something deeper happened.

A Maya MFE stopped feeling like a “component.”

It started feeling like a small application boundary.

Every Maya MFE can contain:

- multiple views
- multiple Mustache templates
- rendering states
- nested slots
- recursive MFEs
- workflows

The default view is always:

```text
#mfe/main
```

But any MFE can dynamically transition into another realization:

```text
#mfe/loading
#mfe/form
#mfe/confirmation
#mfe/error
```

```text
          Maya Slot

      ----------------
      | #mfe/loading |
      ----------------
               ↓
      -----------------------
      | #mfe/request-form  |
      -----------------------
               ↓
      -----------------------
      | #mfe/confirmation  |
      -----------------------
```

The slot remains stable.

Only realization changes.

That’s when Maya started feeling fractal.

Containers can recursively host:

- MFEs
- views
- layouts
- workflows
- other containers

indefinitely.

---

## Messaging Made MFEs Feel Like Distributed Systems

Another realization followed naturally.

MFEs should not be tightly coupled.

They should communicate more like distributed systems.

Instead of directly depending on each other, MFEs communicate through:

- publish / subscribe
- semantic events
- signals
- workflow notifications

```text
     MFE A
       |
   publish(event)
       |
  -----------------
  | Event Channel |
  -----------------
     /        \
    /          \
MFE B        MFE C
 subscribe    subscribe
```

Examples:

```text
appointment.requested
review.published
workflow.completed
theme.changed
client.loggedIn
```

This allows:

- loose coupling
- async orchestration
- recursive composition
- independent deployment
- dynamic personalization

without MFEs needing deep awareness of each other.

Maya orchestrates everything dynamic all the time.

---

## Karma — The Semantic Backend Protocol

> “Karma transforms imagination into operational reality.”

As Maya evolved, I realized backend systems could become semantic too.

Most business interactions eventually reduce into:

```text
actor + intent + noun
```

Examples:

```text
client + request + appointment
doctor + approve + refill
manager + publish + feed
```

Karma became the semantic backend protocol that defines:

- schemas
- workflows
- ACLs
- ownership
- APIs
- storage
- state transitions
- effects
- semantic meaning

```text
             Karma Protocol

        Semantic Backend Engine

      actor + intent + noun
                 |
        -------------------
        |        |        |
      ACL    Workflow   Schema
                 |
              Storage
```

REST models resources.

GraphQL models data shape.

Karma models business intent.

That difference matters.

Because:

```text
POST /appointments
```

does not really explain:

```text
client requests appointment
```

And those are very different ideas.

Karma understands journeys.

```text
client + request + appointment
```

does not instantly become:

```text
appointment scheduled
```

There is:

- submission
- review
- orchestration
- notification
- realization

That lifecycle is Karma.

Full RFC:

- [Karma Protocol RFC](./karma-rfc.md)

---

## Kaya — The Realization Layer

> “Kaya is where imagination becomes experience.”

Kaya became the realization layer inside Maya.

My original goal with Kaya was very simple.

Almost every application ultimately contains:

- forms
- lists
- grids
- spreadsheets
- blocks
- containers
- text
- images
- workflows
- interactions

Users interact.

Systems react.

```text
 User Interaction
        |
        v
  -----------------
  | Forms         |
  | Lists         |
  | Grids         |
  | Blocks        |
  | Containers    |
  | Images/Text   |
  -----------------
        |
        v
 System Reaction
```

The realization was that these experiences should not be rebuilt repeatedly for every framework or business.

They should emerge dynamically from semantic meaning.

Kaya dynamically generates:

- CTAs
- CRUD systems
- workflows
- dashboards
- editorial layouts
- SEO pages
- operational applications

through declarative configuration.

At its core, Kaya is built from:

- Mustache templates as structural skeletons
- CSS layouts
- skins
- themes
- personalities
- semantic rendering rules

```text
Maya  = soul / imagination / possibility
Karma = action / movement / intent
Kaya  = body / realization / experience
```

Just like the human body, Kaya provides:

- structure
- appearance
- interaction
- expression
- realization

while Maya remains the possibility behind it.

Same semantic system.

Different realization.

---

## The Recursive Loop

Then the final realization emerged.

A button click inside Maya does not simply “run JavaScript.”

It performs Karma.

That Karma can trigger another Kaya realization.

Which Maya then displays again.

```text
Maya interaction
        ↓
Karma action
        ↓
Kaya realization
        ↓
Maya view update
```

Example:

```text
User clicks “Request Appointment”
        ↓
Karma executes request.appointment
        ↓
Appointment enters submitted state
        ↓
Kaya resolves confirmation experience
        ↓
Maya renders #appointment/confirmation
```

One action can simultaneously:

- update the current view
- refresh another MFE
- publish an event
- trigger workflows
- notify staff
- update queues
- generate SEO projections
- affect secured applications

without rebuilding the same business idea repeatedly.

That’s when the architecture started feeling alive.

```text
Maya → Karma → Kaya → Maya
```

Imagination.  
Action.  
Realization.  
Evolution.

---

## Real-World Example — Camino Alto Veterinary Hospital

This philosophy is already being used to build the platform powering Camino Alto Veterinary Hospital.

The same semantic system dynamically generates:

- customer CTAs
- operational workflows
- CRUD systems
- admin experiences
- SEO pages
- notifications
- queue views
- public website projections

from shared semantic meaning.

For example:

```text
request.appointment
```

can become:

- a public CTA
- a scheduling workflow
- an admin queue
- notifications
- operational records
- state transitions
- future AI interactions

without rebuilding the same idea repeatedly.

The public website becomes the AI-readable and SEO-readable projection of the same operational system powering the clinic internally.

---

## Why AI Changes Everything

> “AI did not invent composability.  
> It finally made semantic systems practical.”

AI naturally reasons about:

- semantic meaning
- workflows
- layouts
- orchestration
- rendering
- reusable building blocks

without emotional attachment to frameworks.

Future systems must become:

- semantic
- composable
- workflow-aware
- AI-readable
- continuously evolving

The future is not bigger frameworks.

The future is:

- smaller reusable meaning
- composable semantic systems
- less repeated engineering
- more emergence

Maybe software was never supposed to be static.

Maybe it was supposed to evolve like life itself.
