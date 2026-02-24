# Installing Austinpowers for Codex

Enable austinpowers skills in Codex via native skill discovery. Just clone and symlink.

## Prerequisites

- Git

## Installation

1. **Clone the austinpowers repository:**
   ```bash
   git clone https://github.com/obra/austinpowers.git ~/.codex/austinpowers
   ```

2. **Create the skills symlink:**
   ```bash
   mkdir -p ~/.agents/skills
   ln -s ~/.codex/austinpowers/skills ~/.agents/skills/austinpowers
   ```

   **Windows (PowerShell):**
   ```powershell
   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills"
   cmd /c mklink /J "$env:USERPROFILE\.agents\skills\austinpowers" "$env:USERPROFILE\.codex\austinpowers\skills"
   ```

3. **Restart Codex** (quit and relaunch the CLI) to discover the skills.

## Migrating from old bootstrap

If you installed austinpowers before native skill discovery, you need to:

1. **Update the repo:**
   ```bash
   cd ~/.codex/austinpowers && git pull
   ```

2. **Create the skills symlink** (step 2 above) — this is the new discovery mechanism.

3. **Remove the old bootstrap block** from `~/.codex/AGENTS.md` — any block referencing `austinpowers-codex bootstrap` is no longer needed.

4. **Restart Codex.**

## Verify

```bash
ls -la ~/.agents/skills/austinpowers
```

You should see a symlink (or junction on Windows) pointing to your austinpowers skills directory.

## Updating

```bash
cd ~/.codex/austinpowers && git pull
```

Skills update instantly through the symlink.

## Uninstalling

```bash
rm ~/.agents/skills/austinpowers
```

Optionally delete the clone: `rm -rf ~/.codex/austinpowers`.
