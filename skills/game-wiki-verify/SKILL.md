---
name: game-wiki-verify
version: 1.0.0
author: zhant
description: "IRON LAW: NO GAME TERMINOLOGY CLAIMS WITHOUT FRESH WIKI VERIFICATION. Before answering ANY question about game creatures, items, mechanics, skills, buildings, DLCs, characters, or MODS — in ANY game — you MUST fetch and read the game's official wiki page for each entity. For mod-related questions, prioritize Steam Workshop and Nexus Mods; always verify game/mod version (default to latest), and include version numbers in answers. Training data recall is NOT evidence. Triggers on: any game name mentioned in user message; any Chinese game question (怎么养 如何用 是什么 怎么造 攻略 推荐 对比 价值 区别 吃什么 产什么 属性 掉落 mod 模组 创意工坊); any English game question (how to, what is, should I use, guide, strategy, worth it, best way, mod). If you are <90% confident about any game term, stop and verify. Applies to ALL games: 缺氧, 饥荒, 星露谷, 泰拉瑞亚, Minecraft, Factorio, RimWorld, Stardew Valley, Don't Starve, Terraria, etc. Game-specific wiki references are in references/ directory — read the relevant one when the game is identified."
user-invocable: true
---

# Game Wiki Verify — Zero-Hallucination Game Knowledge

Adapted from community best-practice patterns:
- **Iron Law** from `verification-before-completion` (Charpup)
- **Evidence Rules** from `fact-check` (Jamie-BitFlight)
- **Anti-Hallucination Protocol** from `anti-hallucination` (brycewang-stanford)
- **Parallel Research** from `independent-research` (ntcoding)

---

## The Iron Law

```
NO GAME TERMINOLOGY CLAIMS WITHOUT FRESH WIKI VERIFICATION EVIDENCE
```

If you haven't fetched the wiki page in this conversation, you cannot claim to know what a game entity is, does, or is called.

## The 5-Step Gate Function

**You cannot produce your answer until ALL 5 steps pass.**

### Step 1: IDENTIFY — What entities need verification?

Scan the user's question. List every game-specific entity mentioned or implied:
- Creature/animal names
- Item/resource names
- Building/station names
- Character/NPC names
- Skill/trait/ability names
- DLC/expansion names
- Biome/zone/area names

### Step 2: SEARCH — Find the authoritative wiki

Determine the game and locate its wiki. Check `references/` for game-specific wiki URLs. If not found, search:
- `"[game name] wiki"` — find the main wiki
- `"[game name] wiki [entity name]"` — find the specific page

### Step 3: READ — Fetch the actual wiki page (NOT snippets)

**CRITICAL: Search snippets are NOT sufficient.** You MUST use `webfetch` to read the full wiki page content. Search results are noisy and ambiguous — only the page content itself is authoritative.

For each entity, fetch its wiki page. If multiple entities, do this in parallel.

### Step 4: VERIFY — The Evidence Check

From the wiki page, extract these verification facts for EACH entity:

| Check | Question |
|-------|----------|
| **Identity** | What is the exact English name? Is this the entity the user asked about? |
| **Origin** | Which game/DLC/expansion does it belong to? Which biome/zone? |
| **Mechanics** | What does it eat/produce/do? How is it interacted with? |

Then ask yourself the **Critical Question**:

> "Do the Identity + Origin + Mechanics from the wiki match what I was about to say?"

**If ANY fact conflicts with your assumption → you were about to hallucinate. Discard your assumption. Use ONLY wiki facts.**

### Step 5: OUTPUT — Conclusion-first, then details

**Put the direct answer where the user sees it immediately.** Long analyses with the conclusion at the end cause users to misunderstand or miss the answer entirely.

**Required output structure:**

```
[直接回答用户的问题，1-3 句话]
[关键理由或限制条件]
---
### 详细说明
[仅在用户需要时才提供：具体步骤、数据、对比表等]
来源: [wiki URLs]
```

**This structure prevents two failure modes:**

| Failure | Example | Fix |
|---------|---------|-----|
| **Conclusion buried** | Listing 5 options then revealing at the end that the user's request is impossible | State impossibility FIRST, then explain why |
| **Answer lost in detail** | User asks "how to get X" and must scroll past paragraphs before finding the method | Answer in first 3 lines; details after `---` |

**Key rules:**

- **User asks "can I..." / "is it possible..."** → Start with "Yes/No" immediately
- **User asks "how to..."** → Start with the method name/location, not the journey
- **User asks "should I..." / "is X worth it"** → Start with the verdict, then reasoning
- **Anything after `---` is optional** — the user should have their answer before the divider

Every factual claim must be traceable to the wiki page you fetched.

Every factual claim must be traceable to the wiki page you fetched. Cite at the end.

## Evidence Rules

| Acceptable Evidence | NOT Acceptable |
|---------------------|----------------|
| WebFetch of official wiki page | Training data recall ("I know this") |
| WebFetch of community wiki page (if no official wiki) | Pattern matching ("矿" in name → must be Hatch) |
| Official game patch notes | Inference from analogy ("creature X works like Y") |
| Game's own database/translation table | Forum posts without wiki confirmation |
| Steam Workshop / Nexus Mods page (mod queries only) | Mod aggregator/curation sites without primary source |

**If you cannot find the wiki page for an entity, state: "I could not verify [entity] against the wiki. Here's what I found in search results, but please confirm."** Never present unverified information as fact.

## Source Hierarchy

When multiple sources exist, prefer in this order:
1. Official game wiki (wiki.gg, official site)
2. Community wiki (Fandom, Bilibili game wiki)
3. Official patch notes / developer updates
4. Game's translation table (译名表)

**For mod-related queries**, the source hierarchy is:
1. Steam Workshop (steamcommunity.com/workshop) — for the mod's official page, description, and changelog
2. Nexus Mods (nexusmods.com) — for mod details, requirements, and version compatibility
3. Game's official wiki — for mod documentation wikis (e.g., official mod wiki pages)
4. Mod developer's own documentation (GitHub, Discord, etc.)

If sources conflict, prefer the higher-tier source and note the discrepancy.

## Mod-Related Queries

When the user's question involves mods, modded content, or game modifications, apply these additional rules:

### Search Priority

Always search mod platforms **before** general game wikis:
- **Steam Workshop** — Search `site:steamcommunity.com/workshop [game name] [mod name]` or browse the game's workshop directly
- **Nexus Mods** — Search `site:nexusmods.com [game name] [mod name]`

General game wikis often have outdated or incomplete mod information. Mod platforms are authoritative for: mod descriptions, features, requirements, compatibility, version history, and user-reported issues.

### Version Verification (MANDATORY)

Game mods are version-sensitive. A mod working on version X may break on version Y. Always:

1. **Check the game version the mod targets** — Look for version requirements on the mod page (Steam Workshop "Required items" section, Nexus Mods "Requirements" tab)
2. **Default to latest version** — When the user does NOT specify a game version, assume the latest stable release of the game and find the mod version that matches
3. **State the version explicitly** — If you can determine the game version the mod targets, include it in your answer

### Output Rules for Mod Queries

When answering mod-related questions, the output MUST include:

```
[直接回答]
---
### 版本信息
- 游戏版本: [具体的游戏版本号，如 1.5.6]
- Mod 版本: [mod 版本号]
- 兼容性: [是否兼容当前最新版本 / 已知冲突]
### 详细说明
[mod 功能、使用方法等]
来源: [Steam Workshop / Nexus Mods URL]
```

If the version **cannot** be determined: state "无法确定具体版本，以下信息基于最新可用数据。" and note that the user should verify against their own game version.

## When to Say "I Don't Know"

If after searching and fetching wiki pages you still cannot confirm the entity:
- **Say so explicitly**: "I was unable to verify [entity] on the game's wiki."
- **State what you found**: "The closest match I found was [X], but I'm not certain this is what you're asking about."
- **Ask the user**: "Can you confirm whether you mean [X]?"

**Never fill gaps with assumptions. A clear "I don't know" is better than a confident wrong answer.**

## Anti-Patterns (NEVER)

- **NEVER** rely on search result snippets — fetch the page
- **NEVER** pattern-match based on Chinese characters in entity names
- **NEVER** say "X is commonly known as Y" without wiki confirmation
- **NEVER** trust training data over wiki page content
- **NEVER** skip the verification gate because "I know this game"
- **NEVER** present options/strategies without verifying entity identities first

## Game-Specific References

When a game is identified, read the corresponding reference file for wiki URLs and known pitfalls:

- **Oxygen Not Included / 缺氧** → `references/oni.md`
- For other games, search for their wiki and note the URL for future reference.

---

*Adapted from: verification-before-completion (Charpub), anti-hallucination (brycewang-stanford), fact-check (Jamie-BitFlight), independent-research (ntcoding)*
