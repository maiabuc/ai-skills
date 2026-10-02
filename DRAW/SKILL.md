---
name: DRAW
description: Create simple, editable visual explanations of concepts, processes, algorithms, decisions, and "what the AI just did". Use when the goal is fast comprehension rather than implementation-level architecture.
---

# DRAW

Use this skill when the user wants a concept explained visually, wants a simple drawing of a process, or wants to understand what an AI/tool/agent has done without reading detailed code.

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


## DRAW-Specific Objective

Optimize for **understanding in 30 seconds**.

The diagram should answer:

> What is happening, why does it happen, and what should I notice?

Prefer:
- 3 to 7 major visual elements;
- one dominant visual argument;
- short labels;
- concrete examples only where they materially improve understanding;
- transformations, before/after states, cause/effect, or sequence instead of generic boxes.

## Concept Design Patterns

Choose the pattern that best matches the concept:

- **Transformation** — before -> mechanism -> after
- **Cause/effect** — causes converge into an outcome
- **Pipeline** — ordered stages with meaningful intermediate state
- **Feedback loop** — circular flow where outputs affect future inputs
- **Decision** — branching based on explicit condition
- **Layered model** — stacked abstractions with clear dependency
- **Comparison** — mirrored structures showing one meaningful contrast
- **System boundary** — inside vs outside and what crosses the boundary

Do not choose a pattern merely because it is visually attractive.

## Simplicity Budget

Default:
- 1 title
- 3–7 main concepts
- maximum 2 supporting annotations per concept
- maximum 2 levels of nested grouping
- one main arrow direction

If more detail is necessary, reconsider whether the user actually needs DRAW-Architecture.

## AI-Work Explanation Mode

When the user asks what AI coded/did:
1. Inspect the available source or changes.
2. Identify the user-visible objective.
3. Identify the smallest meaningful set of implementation actions.
4. Translate implementation into a causal visual story.
5. Show concrete implementation names only when they teach something.
6. Distinguish:
   - what existed before;
   - what AI added or changed;
   - what happens now.

Use the `New / changed` palette role for new behavior.

## Output Standard

A strong DRAW output should let a non-author explain the idea back correctly after viewing it once.
