# Changelog

All notable changes to Panas RPG will be documented here.

## [1.7.0] - 2026-09-24

**Minecraft 1.20.1 | Forge 47.4.10 | +43 quests (48 → 91 total)**

### New Mods Added (+7 mods)

| Mod | Version | Description |
|-----|---------|-------------|
| **Legendary Monsters** | 2.2.3 | 15+ mythic bosses (Fenrir, Quetzalcoatl, Anubis, etc.) |
| **Grim Kingdoms: Lost Structures** | v1.0.3 | ~100 structures: castles, towers, ruins, ships, kingdoms |
| **Skill Tree (RPG Series)** | 1.6.1 | 100+ node skill tree, shared XP in co-op, class specialization |
| **Runes (RPG Series)** | 1.3.2 | Craftable runes with magical effects |
| **Jewelry (RPG Series)** | 2.4.0 | Gemstone jewelry: rings, necklaces, configurable attributes |
| **Shield Expansion** | 1.3.7 | New shields with unique abilities |
| **Grim Kingdoms: Lost Structures** | v1.0.3 | Vanilla+ structures: castles, towers, ruins, ships, kingdoms |

**Total mods: 215 (+7 new)**

### New FTB Quests — +43 Missions Across 7 Phases

#### ⚔️ FASE I — El Despertar (+4)
- **El huerto** — plantar 8 semillas → Hoe de madera (Croptopia)
- **El arte de la cocción** — cocinar 4 arroces → Skillet (Farmer's Delight)
- **Mi primer mochila** — craftear mochila básica → Stack Upgrade Tier 1
- **El primer viaje** — usar Waystone → 2x Warp Scroll

#### ⛏️ FASE II — Bajo la Superficie (+5)
- **Create: La rueda de agua** → Shaft
- **Create: El molino** → Cogwheel
- **Create: Tuberías** — 4x Fluid Pipe → Mechanical Pump
- **Peces de profundidad** — 3 bacalaos → Fish Fillet (Aquaculture)
- **El primer refugio** — Puerta Macaw's → Sofa (Handcrafted)

#### 🌊 FASE III — Abismos del Océano (+5)
- **Buceador experimentado** — Conduit → Fluid Tank (Create)
- **Pesca abisal** — 5 bacalaos → Fish Fillet
- **Ars Nouveau: Primer hechizo** — Scribe's Table → Arcane Core
- **Ars Nouveau: Familiar** — Ritual Bowl → Dominion Wand
- **Ciudad sumergida completa** — Advancement → Flippers (Artifacts)

#### 🏜️ FASE IV — Arenas y Llamas (+5)
- **Create: La fundición** — Mechanical Saw → Blaze Burner
- **Create: El tren** — Train Controls → 8x Track
- **Bountiful: Primer contrato** — Bounty Board → 5x Iron Coins
- **Lightman's: Mi primera tienda** — Portable Terminal → 1x Iron Coin
- **Simply Swords: Espadas legendarias** — 3 espadas → Nordic Sword

#### 👹 FASE V — Cazadores de Gigantes (+6)
- **Mowzie's: Frostmaw** → Ice Crystal
- **Mowzie's: Naga** → Earthrend Gauntlet
- **Ars Nouveau: Ritual mayor** — Ritual Tablet → Archmage Spell Book
- **Artifacts: Reliquia** — Shock Absorber → Cloud in a Bottle
- **Create: Fábrica automática** — Creative Motor → 4x Brass Casing
- **Mutant Monsters: Mutante** → Mutant Heart

#### 🌌 FASE VI — El Cataclismo (+5)
- **Ars Nouveau: Dominio total** → Summon Focus
- **Create: El cañón de vapor** — Steam Cannon → Brass Hand
- **Lightman's: Mega tienda** — Network Upgrade → 1x Netherite Coin
- **Explorador supremo** → Void Upgrade + Everlasting Upgrade
- **El final verdadero** — Ender Dragon → Ender Edge (Simply Swords)

#### 🏛️ FASE VII — La Civilización (NUEVA — 12 misiones)
- **Create: Ciudad de Create** — Creative Motor
- **Ars Nouveau: Escuela de magia** — Starbuncle Charm
- **Economía: Banco central** — ATM Tablet
- **Agricultura: Granja industrial** — Liquid Fertilizer + Mechanical Harvester
- **Decoración: Palacio** — Wood Supports (Chipped)
- **Mochila final** — Independence Upgrade
- **Create: Tren transcontinental** — Locomotive
- **Ars Nouveau: Archmage** — Amplify Arrow
- **Comerciante supremo** — Network Card
- **El mundo completo** — Flare Upon (Artifacts)
- **Maestro constructor** — Coffee Table (MCW Furniture)
- **Panas RPG: Platinum** — Netherite Coin (logro final)

---

## 🎯 Critical Fixes — Load Order & Attribute Registration

### Load Order & Attribute Registration
- **Fixed load order** for 5 critical mods via `mods.toml` (`ordering = "BEFORE"` / `"AFTER"`)
- **Eliminated duplicate `ordering` entries** in `mods.toml` (caused crash `entry "[ordering]" defined twice`)
- **Restored `puffish_skills` dependency** in `skill_tree` with `ordering = "AFTER"`
- **Final load order:**
  1. `ranged_weapon_api` (BEFORE) — registers ranged weapon attributes
  2. `spell_power` (BEFORE) — registers spell power attributes
  3. `spell_engine` (BEFORE) — registers spell engine effects
  4. `skill_tree` + `jewelry` — depend on above
  4. `puffish_skills` (AFTER) — loads datapack after attributes exist

### Attribute Registration Errors — RESOLVED
- ✅ `Failed to resolve EntityAttribute: critical_strike:chance`
- ✅ `Failed to resolve EntityAttribute: ranged_weapon:haste/damage/velocity`
- ✅ `Failed to resolve EntityAttribute: combat_roll:recharge`
- ✅ `Registry minecraft:mob_effect: Object did not get ID it asked for`

### GeckoLib Animations Fixed
- **Myths & Legends** — 7 files fixed, 20+ Molang patterns fixed
- **Saint's Dragons** — 10 files fixed, 100+ Molang patterns fixed
- Fixed missing spaces around `-` operator in Molang expressions

---

## 🎒 New Mods Added (+7 mods, 215 total)

| Mod | Version | Description |
|-----|---------|-------------|
| **Legendary Monsters** | 2.2.3 | 15+ mythic bosses (Fenrir, Quetzalcoatl, Anubis, etc.) |
| **Grim Kingdoms: Lost Structures** | v1.0.3 | ~100 structures: castles, towers, ruins, ships, kingdoms |
| **Skill Tree (RPG Series)** | 1.6.1 | 100+ node skill tree, shared XP in co-op, class specialization |
| **Runes (RPG Series)** | 1.3.2 | Craftable runes with magical effects |
| **Jewelry (RPG Series)** | 2.4.0 | Gemstone jewelry: rings, necklaces, configurable attributes |
| **Shield Expansion** | 1.3.7 | New shields with unique abilities |
| **Grim Kingdoms: Lost Structures** | v1.0.3 | Vanilla+ structures: castles, towers, ruins, ships, kingdoms |

**Total mods: 215 (+7 new)**

---

## ⚙️ Configs Applied

| File | Key Changes |
|------|-------------|
| `mythsandlegends-common.toml` | `spawnWeightMultiplier = 0.3`, `minBossSpawnDistance = 500`, `globalBossCooldown = 24000`, compat Terrablender |
| `saintsdragons/servercommon.toml` + `spawning.toml` | `dragonSpawnWeightMultiplier = 0.4`, `dragonSpawnChance = 0.05`, weights reduced 60-80% |
| `witherreincarnated/common.toml` | Health 500, damage reduced, cooldowns increased, **undead possession DISABLED** |
| `undergarden-client.toml` | Fix: `toggleUndergardenFog = true` |
| `terrablender.toml` | Priorities: Undergarden(100) > Myths(80) > Saints(60) > BiomesWe'veGone(50) > Terralith(40) |
| `legendarymonsters-common.toml` (new) | `spawnWeightMultiplier = 0.25`, `minBossDistance = 600` |
| `skill_tree` / `jewelry` / `spell_engine` mods.toml | `ordering = "BEFORE"` / `"AFTER"` fixed |
| Duplicate `ordering` | Removed in 5 mods.toml (fix crash `entry "[ordering]" defined twice`) |

---

## 🗑️ Conflicts Resolved

| Element | Action | Reason |
|---------|--------|--------|
| `puffish_skills` dep in `skill_tree` | Restored with `ordering = "AFTER"` | Loads datapack after attributes exist |
| Duplicate `ordering` in `mods.toml` | Removed in 5 mods | Caused crash `entry "[ordering]" defined twice` |
| JAR duplicates | Originals removed after rename | Duplicate modId conflicts |

---

## ⚠️ Known Issues

1. **GeckoLib animations** — Saint's Dragons / Myths & Legends have broken animations (visual only, no crash)
2. **Spell Engine / Jewelry / Skill Tree** — Attributes `critical_strike:chance`, `ranged_weapon:*` need `Spell Power Attributes` + `Ranged Weapon API` (installed, load order fixed)
3. **FancyMenu resource errors** — Cosmetic, no gameplay impact
3. **StructureEssentials** — "Non-unique structure_set salt" (pre-existing, overlapping structures)
4. **Biome stability** — Oh The Biomes packs may conflict with Terralith generation
4. **FPS impact** — 215 mods active — 6–8 GB RAM recommended

---

## 📦 Installation

- Backup `worlds/` saves before updating
- Delete old `mods/` folder to prevent conflicts
- No extra steps: quests, configs, and mods apply automatically
- **Test new world** recommended for first-time users

---

## 📈 Version History

- **v1.8.0** (Sep 2026): +7 mods, +43 quests (FASE VII), load order fix, attribute fixes, 215 mods total
- **v1.7.1** (Sep 2026): **Skill Tree required mods added** — Archers, Paladins & Priests, Rogues & Warriors, Wizards (RPG Series) installed to enable full Skill Tree functionality
- **v1.7.0** (Sep 2026): Watermedia removed, Upgrader Items added, static menus, options.txt removed
- **v1.6.0** (Sep 2026): Cinematic menus + video loading screens with full audit, Chloride crash fix
- **v1.5.2** (Sep 2026): Full mod set restored (206), texture pack lineup completed
- **v1.5.1** (Sep 2026): 8 mods restored, Fabric API backend, deepslate + Eating Animation fixes
- **v1.5.0** (Sep 2026): 19 new mods added, VoiceChat update, biome expansion, performance fixes
- **v1.4.0** (Aug 2026): Initial release – 179 mods, Terralith + Cultural Delights, Create suite

---

## 💬 Feedback

Report bugs or issues on CurseForge page or join Discord: discord.gg/panas-rpg
