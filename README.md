# ai-workflows-setup

Portable development configuration: agents, skills, MCPs, and memory. Works across Claude Code, OpenCode, and other LLMs.

**Powered by [Skillshare](https://github.com/runkids/skillshare)** — centralized skills distribution to all AI tools.

## Structure

```
.
├── .claude/
│   ├── agents/              # Custom agents
│   │   ├── project-planner.md
│   │   └── task-breakdown.md
│   ├── CLAUDE.md           # Global instructions
│   └── settings.json       # MCP/hook config
├── .dev/
│   ├── MEMORY.md           # Exported Engram memory
│   ├── AGENTS.md           # Agent documentation
│   ├── SKILLS.md           # Skills documentation
│   ├── MCPs.md             # MCP servers config
│   └── PREFERENCES.md      # Global preferences
└── README.md
```

## Setup in New Project

### Option 1: Symlinks (Recommended)

```bash
# In your project root
ln -s ~/ai-workflows-setup/.claude .claude
ln -s ~/ai-workflows-setup/.dev .dev
```

Then push to your project repo normally.

### Option 2: Copy Files

```bash
cp -r ~/ai-workflows-setup/.claude your-project/
cp -r ~/ai-workflows-setup/.dev your-project/
```

Commit to your project repo. Updates won't sync automatically.

### Option 3: Git Submodule

```bash
git submodule add git@github.com:perezadria28/ai-workflows-setup.git .dev-config
ln -s .dev-config/.claude .claude
ln -s .dev-config/.dev .dev
```

## What's Included

### Agents
- **project-planner**: Strategy without timings (architecture, MVP, features, market analysis, risks, evolution)
- **task-breakdown**: Operational decomposition (phases, tasks, subtasks, dependencies, parallelization)
- **senior-reviewer**: Issue validation, testing checklists, best practices 2026

### Skills
All skills are managed via **Skillshare** and automatically distributed to:
- Claude Code (`~/.claude/skills/` via symlink)
- Cursor (`~/.cursor/extensions/claude/skills/` via copy)
- OpenCode (`~/.config/opencode/skills/` via symlink)

To add a new skill:
```bash
# 1. Create skill in ai-workflows-setup/skills/
# 2. Run skillshare sync (automatic via hook)
# 3. Skill appears in all tools
```

### Global Preferences
- Spanish (ES) language
- Haiku model for agents
- NO AI-powered apps by default (only workflow automation)
- Always verify LTS versions with context7

### Memory
Exported from Engram: decisions, stack choices, discoveries, conventions

## Skill Distribution with Skillshare

Skills in this repo are automatically distributed to all tools via **Skillshare**.

### Configuration
```yaml
# ~/.config/skillshare/config.yaml
source: ~/.claude/ai-workflows-setup/skills
targets:
  claude: ~/.claude/skills (symlink)
  cursor: ~/.cursor/extensions/claude/skills (copy)
  opencode: ~/.config/opencode/skills (symlink)
```

### Workflow
1. Create skill file in `skills/` directory
2. Edit agent/hook triggers sync automatically:
   - `skillshare sync` (distribute to all tools)
   - Git commit + push to GitHub
3. Skill available in Claude Code, Cursor, OpenCode immediately

### Manual Sync
```bash
skillshare sync
```

## Usage in Claude Code

1. Symlink `.claude/` to your project
2. Claude Code will auto-detect:
   - Agents in `./.claude/agents/`
   - Skills via skillshare (auto-synced)
   - CLAUDE.md instructions
   - MCP settings in settings.json

## Usage in OpenCode

OpenCode reads:
- `.claude/CLAUDE.md` (file conventions fallback)
- `.claude/skills/` (if configured)
- `.dev/AGENTS.md` for reference

Manually invoke agents documented in `.dev/AGENTS.md`

## Updating

If using symlinks:
```bash
cd ~/ai-workflows-setup
git pull
# Changes auto-sync to all projects
```

If using copies:
```bash
cd your-project
cp -r ~/ai-workflows-setup/.dev .dev
# Manual update
```

## Contributing

Update memory, agents, or skills here:
1. Edit relevant file
2. Commit: `docs: update [file] with [change]`
3. Push to main
4. All projects with symlinks auto-update

---

**Created**: 2026-04-17  
**Last updated**: [will auto-update]
