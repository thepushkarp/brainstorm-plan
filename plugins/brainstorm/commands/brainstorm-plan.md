---
name: brainstorm-plan
description: Create a comprehensive implementation plan from a design doc or conversation context
argument-hint: "[optional: path to design doc, e.g., docs/brainstorms/my-feature.md]"
allowed-tools:
  - Read
  - Glob
  - Grep
  - Task
  - Write
  - TodoWrite
---

# Plan: Design to Implementation

Create a comprehensive, detailed implementation plan that a skilled but zero-context engineer could follow.

## Input Source

$ARGUMENTS

If an argument was provided, read that file as the design doc.
If no argument, use the conversation context (assume a design was just discussed via /brainstorm or otherwise).

If neither exists, ask the user: "What feature or design would you like me to create an implementation plan for?"

## Target Audience

Write this plan for an engineer who:
- Is skilled at coding but has **zero context** for this codebase
- Has **questionable taste** - needs explicit guidance on patterns and style
- Knows almost nothing about the **toolset or problem domain**
- Doesn't know **good test design** very well

This means: be explicit, be detailed, leave nothing to interpretation.

## Implementation Plan Structure

Create a plan with these sections:

### 1. Overview
- 2-3 sentence summary of what we're building
- Link back to the design doc if one exists

### 2. Prerequisites
- Required tools and versions
- Environment setup steps
- Dependencies to install
- Any accounts or API keys needed

### 3. Codebase Orientation
- Key files/directories the engineer needs to understand
- Existing patterns to follow (with file references)
- Relevant documentation to read first
- Architecture context (where this fits in the system)

### 4. Implementation Tasks

Break the work into **bite-sized tasks**. Each task should:

```markdown
### Task N: [Clear task title]

**Goal:** What this task accomplishes

**Files to touch:**
- `path/to/file.ts` - [what to add/modify]
- `path/to/other.ts` - [what to add/modify]

**Implementation steps:**
1. Step one with specific details
2. Step two with specific details
3. ...

**Code patterns to follow:**
- Reference existing code: `path/to/similar.ts:45-67`
- Use pattern X for Y (explain why)

**Testing:**
- Unit tests: what to test, where to put them
- Test file: `path/to/file.test.ts`
- Key test cases to cover
- How to run tests: `npm test path/to/file.test.ts`

**Verification:**
- How to manually verify this works
- What success looks like

**Commit:** `feat: [concise commit message]`
```

### 5. Testing Strategy

Overall testing approach:
- What types of tests are needed (unit, integration, e2e)
- Coverage expectations
- Testing patterns to follow from existing code
- Common test utilities available

### 6. Documentation Updates

What docs need updating:
- README changes
- API documentation
- Inline code comments
- Architecture docs

### 7. Definition of Done

Checklist for completion:
- [ ] All tasks implemented
- [ ] Tests passing
- [ ] Code reviewed
- [ ] Documentation updated
- [ ] Manual verification complete

## Principles to Enforce

Throughout the plan, emphasize:

- **DRY** (Don't Repeat Yourself) - Point out reuse opportunities
- **YAGNI** (You Aren't Gonna Need It) - Keep scope tight, no gold-plating
- **TDD** (Test-Driven Development) - Write tests first or alongside
- **Frequent commits** - One logical change per commit

## Output

1. Generate filename: `[topic]-implementation.md` (kebab-case)
2. Create `docs/plans/` directory if needed
3. Write the complete implementation plan
4. Tell the user where it was saved

## Relationship to Claude Code Plan Mode

This written plan complements Claude Code's built-in plan mode:

- **Built-in plan mode** (`EnterPlanMode`): Live, interactive exploration and execution
- **This `/brainstorm-plan` command**: Creates a persistent document that can be:
  - Shared with other engineers
  - Referenced across sessions
  - Version controlled
  - Reviewed before implementation begins

Suggest the user can use the written plan as a reference while using Claude Code's plan mode for actual implementation.

---
*The goal is a plan so detailed that any competent engineer could pick it up and execute without asking questions.*
