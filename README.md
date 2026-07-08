# AI Agent Skills Collection

A curated collection of skills for AI coding agents (Claude Code, OpenCode, Codex CLI, Cursor, and any [Agent Skills](https://agentskills.io)-compatible runtime).

## Skills

| Skill | Description | Version |
|-------|-------------|---------|
| [game-wiki-verify](skills/game-wiki-verify/) | Zero-hallucination game knowledge — verifies all game entities against official wikis before answering | v1.0.0 |

## Installation

### Quick Install (Windows PowerShell)

```powershell
# Clone and install all skills
git clone https://github.com/YOUR_USERNAME/skills.git D:\Space\skills
cd D:\Space\skills
.\install.ps1
```

### Quick Install (macOS / Linux)

```bash
git clone https://github.com/YOUR_USERNAME/skills.git ~/skills
cd ~/skills
./install.sh
```

### Install a Single Skill

```bash
# Install only game-wiki-verify
./install.sh game-wiki-verify
```

### Manual Install

Copy or symlink individual skills to your client's skills directory:

| Client | Skills Directory |
|--------|-----------------|
| Claude Code | `~/.claude/skills/` |
| OpenCode | `~/.claude/skills/` or `~/.agents/skills/` |
| Codex CLI | `~/.agents/skills/` |

```bash
# Example: manual install for Claude Code
ln -s $(pwd)/skills/game-wiki-verify ~/.claude/skills/game-wiki-verify
```

## Adding a New Skill

1. Create `skills/<skill-name>/SKILL.md` with proper YAML frontmatter
2. Add any reference files in `skills/<skill-name>/references/`
3. Optionally add a skill-level `README.md`
4. Update the skills table above

```yaml
# SKILL.md frontmatter template
---
name: my-skill
version: 1.0.0
description: "What it does and when to trigger"
user-invocable: true
---
```

## License

MIT — see [LICENSE](LICENSE)
