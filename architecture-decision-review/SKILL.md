---
name: architecture-decision-review
description: Use when the user wants to compare architecture options, review a proposed system design, identify tradeoffs, clarify ownership boundaries, or decide what should be built now versus deferred. Works across backend, frontend, infrastructure, data, platform, and mixed systems.
---

# Architecture Decision Review

Use this skill to evaluate architecture choices and turn ambiguous design discussions into concrete decisions.

## Workflow
1. Challenge the premise.
- Ask whether the stated problem is the real problem.
- Check whether the user is solving a local symptom instead of the actual system constraint.

2. Identify the real decision.
- State the decision in one sentence.
- Separate the primary decision from adjacent topics.

3. Define the decision surface.
- Current state
- proposed options
- constraints
- invariants
- risks of being wrong

4. Compare options directly.
- ownership boundaries
- operational complexity
- performance and scale implications
- security and safety impact
- developer ergonomics
- migration cost
- reversibility

5. Separate now vs later.
- decide what must be built now
- defer anything not required by the current decision
- avoid solving future problems unless current constraints demand it

6. Make the recommendation explicit.
- recommended option
- why it wins
- what is being rejected
- what remains open

7. Turn the decision into execution.
- implementation order
- prerequisite seams or contracts
- validation steps
- rollback or migration path

## Heuristics
- Prefer clear ownership boundaries over clever abstractions.
- Prefer additive migration paths over rewrites when possible.
- Treat data ownership and read/write boundaries as first-class concerns.
- Do not let tactical UI or performance fixes replace architectural correction.
- If a technology is optional, define the adoption trigger instead of adopting it early.

## Output Format
Use this structure:
- `Title`
- `Status`
- `Context`
- `Options`
- `Tradeoffs`
- `Rejected options`
- `Decision`
- `Failure modes`
- `Consequences`
- `What to build now`
- `What to defer`
- `Open questions`

## Rules
- Do not hide uncertainty; name it.
- Distinguish facts from assumptions.
- Challenge overbuilt designs.
- Keep recommendations concrete enough to execute.
