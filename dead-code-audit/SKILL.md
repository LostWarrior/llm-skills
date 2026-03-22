---
name: dead-code-audit
description: Use when the user wants to find unused code, dead files, orphaned exports, unreachable routes, stale dependencies, or safe cleanup candidates in any codebase or language. Works across frontend, backend, CLI, libraries, tests, and mixed-language repos, including projects using multiple AI agents with git worktrees or a shared workspace.
---

# Dead Code Audit

Use this skill to find code that can be safely removed.

## Workflow
1. Start read-only.
- Inspect repo state first.
- If the worktree is dirty, assume some files may be in-flight rather than dead.

2. Map ownership.
- Identify runtime entry points, test entry points, build scripts, routing, package boundaries, and dynamic loading.
- Distinguish runtime code, test-only code, tooling-only code, generated code, and planned-but-unwired code.

3. Validate each candidate with at least two signals.
- `rg` reference search
- compiler or typechecker
- linter
- tests
- build or routing config
- package manager metadata

4. Classify findings.
- `safe-remove`
- `test-only`
- `tooling-only`
- `planned-but-unwired`
- `needs-manual-review`

5. Report before deleting.
- Findings first
- file references
- what was checked
- risks and blockers

6. Only remove code when explicitly asked.
- Delete in small batches.
- Re-run validation after each batch.

## Multi-Agent Mode
If multiple AI agents are working on the same project:

### With separate git worktrees
- Trust the branch/worktree boundary as the main isolation layer.
- Audit only the current worktree unless the user asks for cross-worktree reasoning.
- Treat files changed in other worktrees as out of scope.

### With a shared workspace and no separate worktrees
- Be conservative.
- Do not remove files that appear recently created, partially wired, or mid-refactor.
- If another agent may be touching the same area, report candidates first instead of deleting.

## Rules
- Do not remove tests or test helpers unless the user wants that scope.
- Do not remove assets based only on lack of current references unless the user explicitly allows that class of cleanup.
- Prefer removing dead code completely over commenting it out.
