# Brainstorm

A Claude Code plugin marketplace for turning fuzzy ideas into concrete design docs.

Inspired by [Jesse Vincent's AI workflow](https://blog.fsck.com/2025/10/05/how-im-using-coding-agents-in-september-2025/).

## Installation

Add this marketplace to Claude Code:

```bash
/plugin marketplace add thepushkarp/brainstorm-plan
```

Then install the brainstorm plugin:

```bash
/plugin install brainstorm@brainstorm-plan
```

## Commands

### `/brainstorm [topic]`

Interactive Q&A to refine an idea into a design specification.

**Features:**
- Explores existing codebase for context (or starts fresh for new projects)
- Asks one question at a time (prefers multiple choice)
- Presents design in 200-300 word sections for approval
- Saves to `docs/brainstorms/<topic>.md`

**Usage:**
```
/brainstorm                           # Start interactively
/brainstorm user authentication       # Start with an initial idea
```

## Typical Workflow

1. **Brainstorm** - `/brainstorm` to explore and refine your idea
2. **Implement** - Use Claude Code's (or Codex's) built-in plan mode, using the saved design doc as reference

## Output Directories

- Design docs: `docs/brainstorms/`

## License

MIT
