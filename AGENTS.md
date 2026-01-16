# AGENTS.md

This file provides guidance to AI coding agents (Claude Code, Cursor, Copilot, etc.) when working with this repository.

## Repository Overview

A go-to-market toolkit for launching products, brands, and campaigns. Skills are packaged instructions that extend agent capabilities.

## Available Skills

### campaign-hud

Campaign dashboard showing countdown, phases, and tasks.

**Use when:**
- "Show me the dashboard"
- "How many days until launch?"
- "What's the status?"

**Commands:**
```
/hud              # Full dashboard
/hud --compact    # One-line status
```

### brand-architect

Generate brand identity - marks, colors, typography options.

**Use when:**
- "Create a brand"
- "Generate logo options"
- "Design color palette"

**Commands:**
```
/brand-architect          # Full workflow
/brand-architect marks    # Just marks
/brand-architect colors   # Just colors
```

### web-architect

Generate brand assets and audit web code against best practices.

**Use when:**
- "Generate favicon package"
- "Create social assets"
- "Audit React code"
- "Check performance"

**Commands:**
```
/web-architect audit              # Check what's missing
/web-architect implement all      # Generate everything
/web-architect audit react        # React best practices audit
/web-architect audit static       # Static site audit
```

### content-creator

Generate threads, articles, one-pagers with brand voice.

**Use when:**
- "Write a Twitter thread"
- "Create a launch post"
- "Generate an article"

**Commands:**
```
/content thread [topic]       # Twitter thread
/content post [topic]         # Single post
/content article [topic]      # Long-form
/content one-pager [topic]    # Print-ready summary
```

### react-best-practices

React and Next.js performance optimization guidelines from Vercel Engineering. 45+ rules across 8 categories.

**Use when:**
- Writing new React components
- Reviewing code for performance
- Optimizing bundle size
- Refactoring React/Next.js code

**Categories:**
- Eliminating waterfalls (Critical)
- Bundle size optimization (Critical)
- Server-side performance (High)
- Client-side data fetching (Medium-High)
- Re-render optimization (Medium)
- Rendering performance (Medium)
- JavaScript micro-optimizations (Low-Medium)

See `skills/react-best-practices/SKILL.md` for full rule reference.

## Skill Structure

Each skill contains:
- `SKILL.md` - Instructions for the agent (YAML frontmatter + workflow)
- `scripts/` - Helper scripts for automation (optional)
- `rules/` - Rule files for audit skills (optional)

### SKILL.md Format

```markdown
---
name: skill-name
description: One sentence describing when to use this skill
---

# Skill Title

{What the skill does}

## Capabilities
## Commands
## Workflow
## Output Examples
```

## Creating a New Skill

1. Create directory: `skills/{skill-name}/`
2. Add `SKILL.md` with YAML frontmatter
3. Add supporting files as needed

### Naming Conventions

- **Skill directory**: `kebab-case` (e.g., `brand-architect`, `web-architect`)
- **SKILL.md**: Always uppercase, always this exact filename

## Installation

Skills are automatically available when the repo is cloned. The agent reads `CLAUDE.md` which references skills.

For additional skills:
```bash
# Copy skill from another repo
cp -r path/to/skill skills/

# Or use add-skill if available
npx add-skill {source}
```

## Best Practices for Context Efficiency

- **Keep SKILL.md under 500 lines** — put detailed reference in separate files
- **Write specific descriptions** — helps agent know exactly when to activate
- **Use progressive disclosure** — reference supporting files that get read only when needed
- **Prefer scripts over inline code** — script execution doesn't consume context

## License

MIT
