# Skills Collection

AI coding agent skills — compatible with Claude Code, OpenCode, Codex CLI, and any [Agent Skills](https://agentskills.io) runtime.

## Skills

| Skill | Description | Version |
|-------|-------------|---------|
| [game-wiki-verify](skills/game-wiki-verify/) | Zero-hallucination game knowledge — verifies all game entities against official wikis before answering | v1.0.0 |

## Installation

Clone and symlink individual skills to your client's skills directory:

```bash
git clone https://github.com/YOUR_USERNAME/skills.git
```

| Client | Skills Directory |
|--------|-----------------|
| Claude Code | `~/.claude/skills/` |
| OpenCode | `~/.claude/skills/` |
| Codex CLI | `~/.agents/skills/` |

```bash
# Example: install game-wiki-verify for Claude Code / OpenCode
ln -s $(pwd)/skills/game-wiki-verify ~/.claude/skills/game-wiki-verify
```

Start a new session for skills to take effect.

## Adding a New Skill

1. Create `skills/<name>/SKILL.md` with YAML frontmatter
2. Add reference files in `skills/<name>/references/` if needed
3. Optionally add a skill-level `README.md`
4. Update the skills table above

## License

MIT — see [LICENSE](LICENSE)
