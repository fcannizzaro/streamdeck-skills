# streamdeck-skills

A collection of agentic skills for building [Elgato Stream Deck](https://docs.elgato.com/streamdeck/sdk/introduction/getting-started/) plugins with the Node.js SDK.

These skills are designed to be consumed by AI coding agents (e.g. GitHub Copilot, Claude, Cursor) to provide deep, contextual guidance on common patterns and challenges encountered during Stream Deck plugin development.

## What Are Skills?

Skills are structured Markdown documents (`SKILL.md`) that teach an AI agent **how** to perform a specific task. Each skill contains:

- **When to use it** — triggers that tell the agent this skill is relevant
- **Background knowledge** — domain context the agent needs to reason correctly
- **Step-by-step workflows** — exact procedures to follow
- **Reference implementations** — real code patterns and config types
- **Troubleshooting guides** — common failure modes and their fixes

Think of them as reusable, machine-readable runbooks that turn a general-purpose coding agent into a Stream Deck plugin development specialist.

## Available Skills

| Skill | Directory | Description |
|---|---|---|
| **Lazy-Load Bindings** | `skills/lazy-load-bindings` | Build Vite plugins for napi-rs native modules that lazy-load platform-specific `.node` binaries from npm at runtime instead of bundling them. Reduces cross-platform bundle size by fetching only the binary matching the current OS/arch on first use. |

## Usage

### With OpenCode

Add skills to your OpenCode configuration (`~/.config/opencode/config.json`):

```json
{
  "skills": [
    {
      "path": "/path/to/streamdeck-skills/skills/lazy-load-bindings/SKILL.md"
    }
  ]
}
```

### With Other AI Agents

Point your agent to the relevant `SKILL.md` file or include its contents in your system prompt / context. The skills are written as self-contained Markdown and can be ingested by any agent that supports custom instructions.

## Repository Structure

```
streamdeck-skills/
├── README.md
└── skills/
    └── lazy-load-bindings/
        └── SKILL.md          # Lazy-load native bindings for Vite
```

## Contributing

To add a new skill:

1. Create a new directory under `skills/` with a descriptive name
2. Add a `SKILL.md` file following the frontmatter format:

```markdown
---
name: your-skill-name
description: >-
  A concise description of what the skill covers and when to use it.
---

# Skill Title

## When to Use This Skill
<!-- Describe the triggers / scenarios -->

## Background
<!-- Domain knowledge the agent needs -->

## Reference Implementation
<!-- Code patterns, config types, examples -->

## Step-by-Step
<!-- Numbered workflow the agent should follow -->

## Troubleshooting
<!-- Common issues and how to resolve them -->
```

3. Keep skills **focused** — one skill per well-defined problem domain
4. Include **real code** — agents work best with concrete examples, not abstract advice
5. Cover **failure modes** — troubleshooting sections are what make a skill production-grade

## License

MIT
