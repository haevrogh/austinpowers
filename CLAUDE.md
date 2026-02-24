# Superpowers

Skills library for Claude Code (v4.3.1, MIT, by Jesse Vincent). Provides 14 development skills, agents, 3 commands, session-start hooks, and `lib/skills-core.js` for skill discovery.

## Structure

- `skills/` - Each subdirectory contains `SKILL.md` with YAML frontmatter (`name`, `description`) + markdown body
- `agents/` - Agent definitions with YAML frontmatter (`name`, `description`, `model`) + markdown body
- `commands/` - Slash commands that proxy to skills
- `hooks/` - Session lifecycle hooks (`session-start` loads `using-superpowers`)
- `lib/skills-core.js` - Skill discovery, frontmatter parsing, path resolution
- `tests/` - Test suites organized by feature

## Before Exploring

Consult `docs/dependency-graph.yaml` before exploring the codebase. It maps skill workflows, file relationships, agent-skill bindings, and infrastructure dependencies. This saves tokens and preserves context.

## Conventions

- Skill descriptions start with "Use when..."
- Skills use YAML frontmatter with `name` and `description` fields
- Follow TDD (RED-GREEN-REFACTOR) for all implementation work
- After adding, removing, or restructuring skills/agents/commands, **update `docs/dependency-graph.yaml`**
