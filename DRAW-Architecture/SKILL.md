---
name: DRAW-Architecture
description: Inspect and explain real software/system architecture as an editable tldraw diagram. Use for codebases, services, APIs, data flows, infrastructure, integration architecture, deployment architecture, and implementation reviews.
---

# DRAW-Architecture

Use this skill when the user wants to understand a real technical system, codebase, integration, deployment, protocol, or architecture.

## Customization

All colors and brand-specific styles live in `references/color-palette.md`.

Read it before generating any diagram and use it as the single source of truth for all color choices: shape fills, strokes, text colors, evidence artifacts, arrows, highlights, and state distinctions.

If the user asks for a brand style, modify the palette first. Do not scatter hard-coded style decisions through the diagram instructions.

## Core Philosophy

**Diagrams should ARGUE, not DISPLAY.**

A diagram is not formatted text. It is a visual argument showing relationships, causality, hierarchy, state, transformation, or flow that words alone cannot express.

### Isomorphism Test
If all text disappeared, would the spatial structure and shape relationships still communicate the core concept?

If not, redesign.

### Education Test
Could a viewer learn something concrete from the diagram, or does it merely label boxes?

A good diagram teaches. It shows real relationships, examples, states, transformations, data formats, event names, or concrete outputs when those details matter.

## Depth Assessment — Do This First

Classify the request before drawing.

### Simple / Conceptual
Use abstraction when:
- explaining a mental model or philosophy;
- the audience does not need implementation specifics;
- the concept itself is abstract;
- the user asks for a quick explanation;
- the diagram should be understood in roughly 30 seconds.

### Comprehensive / Technical
Use concrete examples when:
- diagramming a real system, protocol, workflow, codebase, or architecture;
- the diagram is educational or review material;
- the audience needs to understand what data, calls, states, or outputs actually look like;
- multiple technologies integrate.

For technical diagrams, include evidence artifacts when useful and available.

## Research Mandate for Technical Diagrams

Before drawing a technical diagram, verify the implementation or specification whenever the relevant source is available.

Prefer, in order:
1. User-provided code/files/repository context
2. Connected source-of-truth systems
3. Official documentation
4. Reliable technical references

Research:
- real JSON/data formats;
- event names;
- method/function names;
- API endpoints;
- framework terminology;
- important state transitions;
- actual component ownership and boundaries.

Never replace known technical detail with generic placeholders.

Bad:
`Protocol -> Frontend`

Better:
`AG-UI events: RUN_STARTED -> STATE_DELTA -> A2UI_UPDATE`
connected to the renderer or handler that actually consumes those events.

If something is inferred rather than observed, label it as inferred.

## Evidence Artifacts

Evidence artifacts are concrete examples that demonstrate how the system or concept actually works.

Use only the artifacts that improve comprehension.

| Artifact | Use when | Render |
|---|---|---|
| Code snippet | API/integration/implementation behavior matters | Dark evidence card with compact syntax-colored text |
| Data/JSON | Schema, payload, state, input/output matter | Dark evidence card |
| Event/step sequence | Order/lifecycle matters | Timeline with dots, labels and directional flow |
| UI mockup | Output or interaction matters | Nested rectangles approximating the real UI |
| Real input | The viewer must understand what enters the system | Visible sample content |
| API/method names | Actual calls matter | Use real endpoint/function names |

Evidence must be concise. A diagram is not a code dump.

## Multi-Zoom Architecture

Comprehensive diagrams should work at multiple zoom levels:

### Level 1 — Summary Flow
A single path that explains the whole system at a glance.

Examples:
`Input -> Processing -> Output`
`Browser -> API -> Database`

### Level 2 — Section Boundaries
Use labeled spatial regions to show ownership or responsibility:
- Frontend / Backend
- User / System / External
- Setup / Runtime / Cleanup
- Application / Platform / Infrastructure

### Level 3 — Detail
Inside sections, show concrete examples:
- actual endpoint;
- payload;
- event;
- data model;
- UI response;
- configuration;
- failure branch.

For comprehensive diagrams, aim to include all three levels.

## Container vs Free-Floating Text

Default to free-floating text.

Use a container only when:
- the element is a distinct system thing;
- arrows need to connect to it;
- the shape itself carries meaning;
- it groups related elements;
- it is a focal point.

Use free-floating text for:
- section titles;
- annotations;
- explanations;
- metadata;
- labels.

### Container Test
For every box ask:

> Would this still work as free-floating text?

If yes, remove the box.

## Visual Grammar

Use structure to encode meaning:
- left-to-right for flow by default;
- top-to-bottom for hierarchy;
- containment for ownership;
- distance for conceptual separation;
- alignment for equivalence;
- larger size for greater conceptual importance;
- arrows only when direction matters;
- dashed lines for optional, inferred, asynchronous, or secondary relationships;
- solid lines for primary observed relationships.

Do not create a card grid unless the underlying concept is actually a set of independent cards.

## tldraw Execution Rules

Use tldraw as the preferred canvas when its tools are available.

When producing the canvas:
- make all important elements editable;
- prefer native shapes, arrows, text, frames, and groups;
- keep labels short;
- avoid decorative icon clutter;
- maintain enough whitespace to make relationships obvious;
- preserve semantic colors from `references/color-palette.md`;
- organize the canvas so the user can continue editing manually.

If a tldraw canvas cannot be created in the current execution context, provide a diagram specification that can be reproduced exactly later rather than silently changing the methodology.

## Final Quality Pass

Before considering the diagram complete, verify:
1. The diagram has one clear visual thesis.
2. The primary flow is obvious within 3 seconds.
3. Removing labels would still leave meaningful structure.
4. Technical claims are observed, sourced, or explicitly marked as inferred.
5. No important relationship is hidden merely to make the drawing cleaner.
6. No box exists only because there was text to place somewhere.
7. Colors match `references/color-palette.md`.
8. Evidence artifacts teach rather than overwhelm.
9. The user can edit the result in tldraw.


## Architecture-Specific Objective

The drawing must explain:

> What are the system's important parts, who owns them, how do they communicate, what data moves between them, and what actually happens at runtime?

The diagram must be grounded in evidence from the implementation or authoritative technical documentation.

## Mandatory Inspection Order

Before drawing:
1. Identify the system boundary.
2. Identify user/actor entry points.
3. Identify runtime entry points.
4. Identify main components/services/modules.
5. Identify calls/dependencies between them.
6. Identify persistent stores, queues, caches, files, or state.
7. Identify external systems.
8. Identify deployment/runtime boundaries if relevant.
9. Identify the primary happy-path request/event flow.
10. Identify one or two important failure or fallback paths if they materially affect the architecture.

## Architecture Truth Model

Every represented element should be one of:

- **Observed** — directly verified in source/code/config/docs.
- **Documented** — stated in authoritative documentation.
- **Inferred** — strongly implied but not directly verified.
- **Proposed** — future-state design or recommendation.

Do not visually present inferred/proposed elements as observed facts.

Recommended visual distinction:
- observed/documented: solid boundary;
- inferred: dashed boundary;
- proposed/new: `New / changed` color plus label.

## Evidence Artifact Requirement

For a comprehensive technical diagram, include at least **two** relevant evidence artifacts whenever the source contains them.

Examples:
- a real endpoint;
- a function/method call;
- an actual JSON payload;
- a database table/model;
- an event sequence;
- an environment variable or config mapping;
- a compact UI state;
- a log/event example.

Do not include secrets, tokens, credentials, or personal data.

## Multi-Zoom Layout Requirement

Comprehensive architecture diagrams should include:

### Level 1 — Runtime Summary
A single prominent flow such as:
`User -> Web App -> API -> Service -> Database`

### Level 2 — Architectural Boundaries
Group by the most meaningful boundary:
- application;
- service;
- repository/package;
- deployment/runtime;
- trust/security zone;
- team ownership;
- frontend/backend/platform.

### Level 3 — Concrete Detail
Place evidence artifacts near the component they prove.

Example:
- API box
- beside it: `POST /api/reports`
- below it: compact request JSON
- arrow to service handler
- arrow to persistence

## Architecture Diagram Types

Select based on the user's question:

- **System Context** — actors + system + external systems
- **Container / Service** — apps/services/databases and communication
- **Component** — modules/classes/functions inside a service
- **Runtime Flow** — what happens for one request/event
- **Data Flow** — where data originates, transforms, persists and exits
- **Deployment** — runtime environments, nodes, containers, networks
- **Integration** — APIs, queues, events, third-party systems
- **Change Architecture** — before vs after, with introduced/removed components
- **Failure / Resilience** — normal path plus fallback/retry/degraded paths

Do not try to force every architecture view into one canvas. If necessary, use adjacent frames on the same tldraw canvas.

## Codebase Analysis Rules

When a repository is available, prioritize:
1. README / architecture docs
2. package manifests and dependency files
3. entry points
4. routing/controllers
5. service/domain layer
6. persistence/data layer
7. integrations
8. deployment/configuration
9. CI/CD only when relevant to the user's question

Avoid treating folder structure as architecture unless runtime behavior supports that interpretation.

## Security and Secrets

Never copy:
- API keys
- access tokens
- passwords
- private keys
- session secrets

If a secret appears in source, show only:
`SECRET / credential (redacted)`

## Final Architecture Checks

Before completion, verify:
- every arrow has a clear meaning;
- sync vs async relationships are distinguishable when important;
- external systems are visibly external;
- persistent storage is distinguishable from processing;
- the primary runtime flow can be followed end-to-end;
- evidence artifacts substantiate the important claims;
- unknowns are labeled instead of guessed;
- proposed changes are visibly distinct from existing architecture.
