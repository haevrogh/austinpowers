# Installing Austinpowers for OpenCode

## Prerequisites

- [OpenCode.ai](https://opencode.ai) installed
- Git installed

## Installation Steps

### 1. Clone Austinpowers

```bash
git clone https://github.com/obra/austinpowers.git ~/.config/opencode/austinpowers
```

### 2. Register the Plugin

Create a symlink so OpenCode discovers the plugin:

```bash
mkdir -p ~/.config/opencode/plugins
rm -f ~/.config/opencode/plugins/austinpowers.js
ln -s ~/.config/opencode/austinpowers/.opencode/plugins/austinpowers.js ~/.config/opencode/plugins/austinpowers.js
```

### 3. Symlink Skills

Create a symlink so OpenCode's native skill tool discovers austinpowers skills:

```bash
mkdir -p ~/.config/opencode/skills
rm -rf ~/.config/opencode/skills/austinpowers
ln -s ~/.config/opencode/austinpowers/skills ~/.config/opencode/skills/austinpowers
```

### 4. Restart OpenCode

Restart OpenCode. The plugin will automatically inject austinpowers context.

Verify by asking: "do you have austinpowers?"

## Usage

### Finding Skills

Use OpenCode's native `skill` tool to list available skills:

```
use skill tool to list skills
```

### Loading a Skill

Use OpenCode's native `skill` tool to load a specific skill:

```
use skill tool to load austinpowers/brainstorming
```

### Personal Skills

Create your own skills in `~/.config/opencode/skills/`:

```bash
mkdir -p ~/.config/opencode/skills/my-skill
```

Create `~/.config/opencode/skills/my-skill/SKILL.md`:

```markdown
---
name: my-skill
description: Use when [condition] - [what it does]
---

# My Skill

[Your skill content here]
```

### Project Skills

Create project-specific skills in `.opencode/skills/` within your project.

**Skill Priority:** Project skills > Personal skills > Austinpowers skills

## Updating

```bash
cd ~/.config/opencode/austinpowers
git pull
```

## Troubleshooting

### Plugin not loading

1. Check plugin symlink: `ls -l ~/.config/opencode/plugins/austinpowers.js`
2. Check source exists: `ls ~/.config/opencode/austinpowers/.opencode/plugins/austinpowers.js`
3. Check OpenCode logs for errors

### Skills not found

1. Check skills symlink: `ls -l ~/.config/opencode/skills/austinpowers`
2. Verify it points to: `~/.config/opencode/austinpowers/skills`
3. Use `skill` tool to list what's discovered

### Tool mapping

When skills reference Claude Code tools:
- `TodoWrite` → `update_plan`
- `Task` with subagents → `@mention` syntax
- `Skill` tool → OpenCode's native `skill` tool
- File operations → your native tools

## Getting Help

- Report issues: https://github.com/obra/austinpowers/issues
- Full documentation: https://github.com/obra/austinpowers/blob/main/docs/README.opencode.md
