---
name: architecture-decision-records
description: Use when the user wants to capture, read, update, or manage architecture decision records (ADRs). Use for prompts like "ADR this", "record this decision", or "why did we choose X?".
---

# Architecture Decision Records

Use this skill to capture architectural decisions as ADRs.

This skill is for ADR writing and maintenance, not decision analysis. If the user is still comparing options, use `architecture-decision-review` first.

## When To Use
- `ADR this`
- `record this decision`
- `why did we choose X?`
- a significant technical decision has already been made

## ADR Template
```md
# ADR-NNNN: [Decision Title]

**Date**: YYYY-MM-DD
**Status**: proposed | accepted | deprecated | superseded by ADR-NNNN
**Deciders**: [people or roles]

## Context
[problem, constraints, forces]

## Decision
[the decision]

## Alternatives Considered
- [option]: why rejected

## Consequences
### Positive
- [benefit]

### Negative
- [trade-off]

### Risks
- [risk and mitigation]
```

## Workflow
1. Check whether an ADR is warranted.
2. If `docs/adr/` does not exist, ask before creating it.
3. Draft the ADR from the decision, alternatives, and consequences.
4. Show the draft to the user.
5. Only write files after explicit approval.
6. Update `docs/adr/README.md` if the project keeps an ADR index.

## Reading ADRs
If the user asks why a decision was made:
- check `docs/adr/`
- scan the index or files
- summarize the matching ADR
- if none exists, say so and offer to record one

## Rules
- Keep ADRs short.
- Record the why, not just the what.
- Ask before creating directories or files.
- Mark old ADRs as deprecated or superseded instead of deleting them.
