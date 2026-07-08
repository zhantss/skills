# Game Wiki Verify

**Zero-hallucination game knowledge for AI coding agents.**

Stop AI from confusing 矿甲龟 (Orehull) with 哈奇 (Hatch), or making up Pokemon stats. This skill forces the agent to verify every game entity against the official wiki before answering — a 5-step gate function adapted from battle-tested community patterns.

## How It Works

```
User: "缺氧怎么养矿甲龟？"
  → Gate 1: IDENTIFY entities (矿甲龟)
  → Gate 2: SEARCH wiki (oxygennotincluded.wiki.gg)
  → Gate 3: READ full page (webfetch, NOT snippets)
  → Gate 4: VERIFY identity (Orehull? DLC=水生行星包? Check!)
  → Gate 5: OUTPUT with wiki citation
```

Without this skill, AI sees "矿" in the name and pattern-matches to 哈奇 (Hatch) — a completely different creature. With this skill, it reads the wiki and knows 矿甲龟 is an aquatic creature from the Aquatic Planet Pack DLC that's sheared for iron ore.

## Features

- **Game-agnostic**: Works for 缺氧, 宝可梦, 星露谷物语, 泰拉瑞亚, Don't Starve, Minecraft, RimWorld, and any game with a wiki
- **Iron Law**: "NO GAME TERMINOLOGY CLAIMS WITHOUT FRESH WIKI VERIFICATION"
- **5-Step Gate Function**: IDENTIFY → SEARCH → READ → VERIFY → OUTPUT
- **Evidence-based**: Training data recall is NOT accepted as evidence
- **Extensible**: Add new games by creating a `references/[game].md` file

## Supported Games

| Game | Reference File | Status |
|------|---------------|--------|
| 缺氧 / Oxygen Not Included | `references/oni.md` | Complete (known confusions documented) |
| Other games | Auto-detected via web search | Supported (no pre-built references yet) |

## Adding a New Game

Create `references/[game-name].md` with:

```markdown
# Game Name — Wiki Reference

## Authoritative Wikis
| Wiki | URL | Notes |
|------|-----|-------|

## Known AI Confusions
| Entity | AI often confuses with | Key difference |
|--------|----------------------|----------------|

## Verification Checklist
- [ ] Item 1
- [ ] Item 2
```

## Credits

Methodology adapted from community best-practice skills:
- [verification-before-completion](https://github.com/Charpup/verification-before-completion) — Iron Law & Gate Function pattern
- [anti-hallucination](https://github.com/instantX-research/anthropic-anti-hallucinate-skills) — "Never guess. Verify or say you don't know."
- [fact-check](https://github.com/Jamie-BitFlight/claude_skills) — Evidence rules & citation format
- [independent-research](https://playbooks.com/skills/ntcoding/claude-skillz/independent-research) — Parallel subagent pattern
