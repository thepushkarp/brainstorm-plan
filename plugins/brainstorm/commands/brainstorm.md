---
name: brainstorm
description: Turn a fuzzy idea into a concrete design doc through guided Q&A
argument-hint: "[optional: initial idea or topic]"
allowed-tools:
  - Read
  - Glob
  - Grep
  - Task
  - Write
  - AskUserQuestion
  - TodoWrite
---

# Brainstorm: Idea to Design Doc

Help the user turn a fuzzy idea into a fully formed design and specification through structured conversation.

## Initial Argument

$ARGUMENTS

## Workflow

### Step 1: Understand the Context

First, explore the current project state to understand where we're starting:

1. Check if this is an existing project or a new one:
   - Look for common project indicators: `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, `README.md`, `src/`, etc.
   - If existing project: Use Glob and Read to understand the codebase structure, key files, and existing patterns
   - If new/empty project: Acknowledge this and note we're starting fresh

2. Briefly summarize what you found (2-3 sentences max) before proceeding to questions.

### Step 2: Capture the Initial Idea

If the user provided an argument, use that as the starting idea. Otherwise, ask:
"What's the idea you'd like to explore?"

### Step 3: Guided Q&A (ONE question at a time)

Ask clarifying questions to refine the idea into a concrete spec:

**Rules:**
- Ask only ONE question per message
- Prefer multiple choice questions when possible (use AskUserQuestion tool)
- Open-ended questions are OK when choices aren't clear
- Keep questions focused and specific
- Build on previous answers
- Stop when you have enough clarity to write the design

**Question areas to cover:**
- Core problem being solved
- Target users/use cases
- Key features and behaviors
- Technical constraints or preferences
- Integration with existing code (if applicable)
- Non-goals (what this explicitly won't do)
- Edge cases and error handling

### Step 4: Present the Design (in sections)

Once you understand the requirements, describe the design:

**Rules:**
- Present in sections of 200-300 words each
- After each section, ask: "Does this section look right so far?"
- Wait for confirmation before continuing to the next section
- Revise sections based on feedback before moving on

**Suggested design doc structure:**
1. **Overview** - What this is and why it matters (1 paragraph)
2. **Goals** - What we're trying to achieve (bullet points)
3. **Non-Goals** - What we're explicitly NOT doing (bullet points)
4. **User Experience** - How users will interact with this
5. **Technical Approach** - High-level architecture and key decisions
6. **Key Components** - Main pieces and how they fit together
7. **Open Questions** - Things still to be decided

### Step 5: Save the Design Doc

After all sections are confirmed:

1. Generate a kebab-case filename from the topic (e.g., `user-authentication.md`, `api-rate-limiting.md`)
2. Create the directory if needed: `docs/brainstorms/`
3. Write the complete design doc using the Write tool
4. Tell the user where it was saved
5. Suggest they use their assistant's built-in plan mode next, using the saved design doc as reference

## Output Format

The saved design doc should be clean markdown:

```markdown
# [Title]

## Overview
[1 paragraph summary]

## Goals
- Goal 1
- Goal 2

## Non-Goals
- Non-goal 1
- Non-goal 2

## User Experience
[Description of user interaction]

## Technical Approach
[Architecture and key decisions]

## Key Components
[Main pieces and how they connect]

## Open Questions
- Question 1
- Question 2

---
*Generated via /brainstorm on [date]*
```

## Important Reminders

- Be conversational but focused
- Don't overwhelm with too many options
- Keep the momentum moving forward
- It's OK to suggest answers when you have a reasonable default
- The goal is a useful spec, not a perfect one
