# DRAW Skills

This package contains two Agent Skill directories:

- `DRAW` — simple conceptual and explanatory diagrams.
- `DRAW-Architecture` — evidence-grounded technical architecture diagrams.

Both are designed to use **tldraw** as the preferred editable canvas and share the same diagram methodology and color system.

## Shared customization

Each skill contains:

`references/color-palette.md`

This is intentionally duplicated so each skill remains self-contained and portable. If you change your visual identity, update the palette in both skills or keep them synchronized from a shared source in your own skill repository.

## Core distinction

**DRAW** asks: “What is the simplest visual argument that makes this understandable?”

**DRAW-Architecture** asks: “What does the real system do, how do the parts connect, and what evidence proves it?”

## Example prompts

### DRAW
- “DRAW how a DQN learns.”
- “DRAW what the agent changed in this feature.”
- “DRAW this business process so I can explain it in 30 seconds.”

### DRAW-Architecture
- “DRAW-Architecture this repository.”
- “DRAW-Architecture the runtime flow from login to database.”
- “DRAW-Architecture what changed in this branch versus main.”
- “DRAW-Architecture this API integration and include real payload examples.”
