# Oxygen Not Included / 缺氧 — Wiki Reference

## Authoritative Wikis

| Wiki | URL | Notes |
|------|-----|-------|
| wiki.gg (primary) | `oxygennotincluded.wiki.gg/zh` | Most actively maintained Chinese wiki |
| Bilibili mirror | `wiki.biligame.com/oni` | Good for cross-reference |
| Translation table | `oxygennotincluded.wiki.gg/zh/wiki/缺氧_Wiki:译名表` | Check this FIRST for any term |

## Wiki Page URL Pattern

Entity pages follow: `oxygennotincluded.wiki.gg/zh/wiki/[Entity Chinese Name]`

## Known AI Confusions (CHECK THESE BEFORE ANSWERING)

The following entity pairs are FREQUENTLY confused. If the user asks about either, you MUST fetch BOTH wiki pages to confirm which one is correct.

| Entity | AI often confuses with | Key difference |
|--------|----------------------|----------------|
| 矿甲龟 (Orehull) | 哈奇/石壳哈奇 (Hatch/Stone Hatch) | Orehull = 水生行星包 DLC, aquatic, 藻林生态, sheared for iron ore. Hatch = base game, land, 砂岩生态, eats minerals, poops coal |
| 灯喙鱼 (Beakon) | 任意发光生物 | Beakon = 水生行星包 DLC, aquatic, emits light when happy |
| 海马 (Seaquine) | 帕库鱼 (Pacu) or any fish | Seaquine = 水生行星包 DLC, milked for Ovolene at 水生挤奶站 |
| 颚鱼 (Jawbo) | 帕库鱼 (Pacu) | Jawbo = 史前行星包 DLC, hunts live Pacu |
| 金螺 (Gildgo) | 缓螺 (Slogo) | Gildgo = Slogo morph, 深渊生态 |
| 藻蝌蚪 (Kelpole) | 塔藻 (Tower Kelp) | Kelpole = critter (can be harvested), Tower Kelp = plant |

## DLC Identification

| DLC | Chinese name | Key creatures |
|-----|-------------|---------------|
| Base game | 本体 | 哈奇 (Hatch), 帕库鱼 (Pacu), 抛壳蟹 (Pokeshell) |
| Spaced Out! | 眼冒金星！ | — |
| Prehistoric Planet Pack | 史前行星包 | 颚鱼 (Jawbo) |
| Aquatic Planet Pack | 水生行星包 | 矿甲龟 (Orehull), 灯喙鱼 (Beakon), 鼓气鱼 (Blowter), 海马 (Seaquine), 金螺 (Gildgo), 藻蝌蚪 (Kelpole), 缓螺 (Slogo), 彩斑鱿 (Glo Squid) |
| The Bionic Booster Pack | 仿生增幅包 | 仿生复制人 (Bionic Duplicant) |

## Known AI Calculation Errors (Farming/Ranching)

When answering "how many X to feed N dupes", AI frequently:
1. **Uses wrong/stale happiness formula** — the reproduction formula has changed across versions (U57+ introduced a new multiplier). Training data may contain outdated formulas. ALWAYS fetch the `小动物` (Critter) general page to extract the CURRENT formula — look for "繁殖速率 = 基础繁殖速率 * (...)" or similar.
2. **Misattributes happiness sources** — Tamed ≠ +1, it's -1. Groomed ≠ +1, it's +5. Buffs vary per critter. ALWAYS scan the critter's happiness section on its own page.
3. **Confuses wild vs groomed reproduction** — The Beakon page shows "Groomed: 1.5 cycles" but this is after happiness applied. Must compute from base using formula.
4. **Ignores DLC biome gating** — Waterweed is Ocean Biome, NOT on Marinea starting asteroid. Must check which biome the entity spawns in, then cross-reference with the asteroid's biome list.
5. **Forgets food cooking chains** — Fish fillet (1000) → 烤海鲜 (1600) → 海陆双拼 (6000). Cooking multiplies kcal and reduces needed ranch size. Must fetch recipe pages.
6. **Skips chef workload** — Each recipe has a cook time; duplicants have limited work time per cycle. Must fetch cooking station page for times.

## Farming/Ranching Calculation Workflow

For ONI "feed N dupes" questions, fetch in this order:

```
Phase 1 — Context Pages (parallel):
  → 游戏设置 (Game Settings) — hunger kcal/cycle per difficulty
  → 小动物 (Critter) — current reproduction/happiness formula (look for "繁殖速率 = 基础繁殖速率 * (...)")
  → [if cooking mentioned] 电动烤炉 + 燃气灶 — per-recipe cook time

Phase 2 — Entity Pages (parallel, after Phase 1):
  → Each critter's own page — lifespan, base egg cycle, happiness sources, death drops (kcal)
  → Each plant's own page — growth cycle (人工/野生), yield per harvest, irrigation/fertilizer needs
  → Each food recipe page — input ingredients (kcal each), output kcal, cooking station, cook time

Phase 3 — Synthesize:
  → List each happiness source with its value (驯化/温顺, 打扮/抚摸, 特殊buff)
  → Sum happiness → plug into formula from Phase 1 → compute eggs/cycle
  → Compute lifetime eggs using formula on 小动物 page (or adult_cycles / egg_cycle)
  → Compute ranch size: needed_kcal_per_cycle / (meat_kcal_per_kill × eggs_per_cycle_per_breeder)
  → Compute chef count: recipes_per_cycle × base_cook_time / work_seconds_per_cycle

Phase 4 — Food chain upgrade (if user wants efficiency):
  → For each food tier, fetch recipe page → compute new kill/plant count
  → Present comparison table: 生吃 → 初级加工 → 高级烹饪
```

### Calculation Output Structure

When user asks "how many X to feed N dupes", structure the answer as:

```
[直接答案]

### 计算基准（来自 wiki）
| 参数 | 数值 | 来源页面 |
|------|------|---------|
| 最高难度饥饿速率 | 2000 kcal/周期 | 游戏设置 |
| ... | ... | ... |

### 幸福度明细（逐项列出）
| 来源 | 数值 |
|------|------|
| 温顺（驯化） | -1 |
| 打扮（抚摸） | +5 |
| [特殊buff] | +X |
| **最终幸福度** | **N** |

### 繁殖率推算
[完整公式代入：基础周期 → ×(1+N×幸福度) → 最终周期 → 蛋/周期]

### 一生产蛋数
[代入 小动物 页面的一生产蛋公式，计算最终结果]

### 烹饪进阶对比（可选）
| 方案 | 热量/份 | 需宰杀/周期 | 需种鱼 | 需厨师 |
|------|---------|------------|--------|--------|
| 生吃 | 1000 | X | X | 0 |
| 加工 | 1600 | X | X | 1 |
| 高级 | 6000 | X | X | 1 |

来源: [wiki URLs]
```

## Biome-to-Food Mapping

When user mentions a specific starting asteroid + DLC, verify which food entities are actually available:

| Starting Asteroid | DLC | Starting Biome | Native Food Plants | Native Food Critters |
|-------------------|-----|---------------|--------------------|---------------------|
| Marinea (汪洋星) | 水生行星包 | 沙滩生态 | 咸蔗, 水草 | 缓螺 |
| Marinea Fragment | 水生行星包+眼冒金星 | 沙滩生态 | 咸蔗 | 缓螺 |

Other biomes on Marinea: 珊瑚生态 (灯喙鱼, 鼓气鱼, 海马), 藻林生态 (矿甲龟, 藻蝌蚪, 塔藻), 深渊生态 (彩斑鱿, 管虫, 针胆团).
If the user says "不开任何生态融入", limit to starting biome only.

## Verification Checklist for ONI

Before answering any ONI question:
- [ ] Did I fetch the wiki page for the creature/item the user asked about?
- [ ] Did I confirm which DLC it belongs to?
- [ ] Did I check the "Known AI Confusions" list above?
- [ ] Did I check the "Known AI Calculation Errors" list above?
- [ ] If user asked a "how many" question, did I fetch the general mechanics page for CURRENT formulas?
- [ ] Did I verify which biome the entity is in vs. the user's starting asteroid?
- [ ] If the user asked in Chinese, did I verify the Chinese name against the wiki's 译名表?
