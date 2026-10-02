# Color Palette

This file is the single source of truth for all diagram colors.

## Principles
- Use color semantically, never decoratively.
- Keep the canvas mostly neutral.
- Reserve saturated colors for meaning: focus, warning, external system, evidence.
- Use the same meaning consistently across the whole diagram.
- Prefer strong contrast and readable labels.

## Core Palette

| Role | Fill | Stroke | Text | Usage |
|---|---|---|---|---|
| Canvas | #FFFFFF | — | #1F2937 | Default background |
| Primary concept | #E8F0FE | #4F6BED | #1F2937 | Main subject / focal component |
| Secondary concept | #F3F4F6 | #6B7280 | #1F2937 | Supporting components |
| Positive / success | #E6F4EA | #34A853 | #1F2937 | Successful outcome, healthy path |
| Warning / attention | #FFF4E5 | #F59E0B | #1F2937 | Risks, caveats, bottlenecks |
| Error / failure | #FDECEC | #D93025 | #1F2937 | Failure states, rejected paths |
| External system | #F3E8FF | #8B5CF6 | #1F2937 | Third-party or external dependency |
| Data / storage | #E6F7F8 | #0F9D9A | #1F2937 | Databases, queues, files, persistent state |
| User / human | #FFF0F6 | #D946EF | #1F2937 | Human actor, team, operator |
| New / changed | #FFF7CC | #C59A00 | #1F2937 | Newly introduced or modified component |
| Deprecated / removed | #F1F1F1 | #9CA3AF | #6B7280 | Removed / legacy / de-emphasized |

## Evidence Artifact Palette

| Element | Color |
|---|---|
| Evidence background | #111827 |
| Evidence border | #374151 |
| Evidence primary text | #F9FAFB |
| Evidence muted text | #9CA3AF |
| Code keyword | #C084FC |
| Code string | #86EFAC |
| Code number | #FDE68A |
| Code function / endpoint | #93C5FD |
| Error in artifact | #FCA5A5 |

## Lines and Arrows
- Primary flow: #374151
- Secondary flow: #9CA3AF
- Success flow: #34A853
- Warning flow: #F59E0B
- Error flow: #D93025
- New / proposed flow: #C59A00

## Usage Rules
1. Read this file before generating any diagram.
2. Never invent new semantic colors unless the user explicitly requests a brand palette.
3. If the user provides a brand palette, update this file first and use it everywhere.
4. Do not use more than 5 semantic colors in one diagram unless the diagram genuinely requires it.
5. Evidence artifacts always use the evidence palette unless the user explicitly requests otherwise.
