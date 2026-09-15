# Changelog

All notable changes to Panas RPG will be documented here.

## [1.5.2] - 2026-09-14

**Full mod set restored (206 mods), zip verified 1:1 against the live instance**

- All test-instance mods included: the 15 recovered (Better Combat, Eating Animation, Freecam, Chunky, CorgiLib, Punchy! 2.7e, Traveler's Titles, Oh The Biomes We've Gone, Oh The Trees You'll Grow, and more) plus the 9 test additions (Alex's Caves, Somnia Awoken, Koremods, Tidal Towns, Unnamed Desert, Dungeons and Taverns, Entity Model/Texture Features, ImmediatelyFast)
- Verified: 199 manifest projects + 5 override jars, 605 configs, 24 FancyMenu layouts, zero differences
- Texture packs shipped: `HIDYKs REALM EatingAnimation compat`, `LANOSTRYs JOURNEY` (fixed v2), Nautilus3D; manual set in order: `HIDYKs REALM` (base), FreshAnimations + FA+Player, HyperPunchy + Punchy refined, Enchantment Glows, compat on top

## [1.5.1] - 2026-09-13

### Restored mods (8, disabled content back for existing worlds)
- Alex's Caves, Dungeons and Taverns, Tidal Towns, Somnia Awoken, Advancement Plaques (+ Iceberg library), Koremods + u_desert (Unnamed Desert)

### New & updated
- Forgified Fabric API (required backend for OBE + Embeddium compatibility), AI-Improvements re-added/updated

### Key changes
- Purple/missing deepslate fixed: repaired `LANOSTRYs JOURNEY` broken `deepslate.json` (invalid syntax + vanilla-incompatible variant format)
- Eating Animation now works with `HIDYKs REALM`: compat patch merging all 41 foods (pack visuals + eating/drinking animation, incl. potion/milk/honey)

### Active resource packs
- `HIDYKs REALM` + EatingAnimation compat (on top), `LANOSTRYs JOURNEY` (fixed v2), Nautilus3D, FreshAnimations, FA+Player, Punchy refined, HyperPunchy, Enchantment Glows

## [1.5.0] - 2026-09-12

**Minecraft 1.20.1 | Forge 47.4.10 | 19 new mods**

### New mods
- Animation_Overhaul, bettercombat, BetterThirdPerson, better_looting, c2me, Chunky, cinematic_respawn, Corgilib, eatinganimation, freecam, gml, mc2_interactivefoliage, Oh-The-Biomes-Weve-Gone, Oh-The-Trees-Youll-Grow, player-animation-lib, punchy, StreamsReflowing, TravelersTitles (+1 unnamed)

### Key changes
- VoiceChat updated from `voicechat-forge` to `voicechat-fabric` for better compatibility
- Biome expansion with Oh The Biomes packs (may conflict with Terralith/Cultural Delights worldgen)
- Performance (StreamsReflowing and more) and QoL (BetterCombat, cameras, animations)

### Known issues
- New biome mods may cause unexpected worldgen with Terralith + Cultural Delights
- VoiceChat needs config changes after the Forge to Fabric API switch
- Lower-end systems may feel the extra 19 mods

## [1.4.0] - 2026-09-03

**Minecraft 1.20.1 | Forge 47.4.10 | 179 mods**

### Custom Menu Experience (FancyMenu 3.9.12)
- Fully customized main menu with animated background, custom navigation panels (FTB Quests, JourneyMap, Create), modpack branding, animated particles and responsive layout

### Stability & Compatibility Overhaul
- Dependency alignment across Create, Simply Swords and Sophisticated ecosystems
- Registry conflicts resolved (missing/duplicate entries eliminated)
- Mixin compatibility fixed (Sophisticated Core, Embeddium, ModernFix)
- Loader conflicts eliminated (Simply More now Forge-native, compatible with Simply Swords 1.70.2); Create Addition updated for Create 6.0.8

### Pack overview
- 179 mods, 597 config files; Create 6.0.8 + Additions; Terralith, YUNG's, Dungeons Arise; Ars Nouveau, Simply Swords, Simply More; Embeddium, ModernFix, Canary, FerriteCore, Saturn

### Technical improvements
- Memory: Saturn + AllTheLeaks + ModernFix leak fixes; Worldgen: Noisium + Structure Layout Optimizer + SmoothChunk; Rendering: Embeddium + Oculus + EntityCulling + FerriteCore; Network: Connectivity + ChunkSending; Loading: Smooth Boot + ModernFix parallel loading

## [1.3.1] - 2026-08-31

**Minecraft 1.20.1 | Forge 47.4.10 | 137 -> 145 mods (+8)**

### Mass mod updates
- All mods updated to latest stable for 1.20.1 Forge 47.4.10 (Core/perf: Embeddium 0.3.31, Oculus 1.8.0, ModernFix 5.27.44, FerriteCore 6.0.1, BadOptimizations 2.4.1, EntityCulling 1.9.5, Clumps, AI Improvements, Smooth Boot, Noisium, Saturn, SmoothChunk, Connectivity, Chunksending, FastSuite, FastAsyncWorldSave, Radium, Structure Layout Optimizer; QoL: JEI, JourneyMap, Jade, MouseTweaks, CraftingTweaks, Cupboard, CrashAssistant, Structure Essentials, Vanillin, Cerulean, Chloride, MemGuard; Create suite; Sophisticated suite aligned)

### Manually added mods (license/policy workaround)
- Declared as external dependencies in `manifest.json` (auto-downloaded by CurseForge, not in `overrides/mods/`): EcoTask 1.4.1, Corail Tombstone 9.0.10, Voicechat 2.6.22, Simply More 1.1.4, Entity Culling 1.9.5, Balm 7.3.42, Sophisticated Storage 1.4.86.2131, Sophisticated Inventory Interactions 0.1.13.210

### Critical fixes
- `NoSuchMethodError: RunicSwordItem` — Simply More 1.1.3 incompatible with Simply Swords 1.56.0, updated to 1.1.4
- `Registry entry not present: createaddition:cake_base` — Create Addition 1.3.3 incompatible with Create 6.0.8, updated
- `NoSuchMethodError: SophisticatedCore.registerMessage` — Core/Backpacks/Storage/Inventory aligned

### Configs included
- BadOptimizations 40/8, EntityCulling 96/5 + whitelist 22; Embeddium Fog Occlusion ON, Block Face Culling ON, Leaves FAST; ModernFix dynamic_resources=true, deduplicate_location=true

## [1.3.0] - 2026-08-30

**Minecraft 1.20.1 | Forge 47.4.10 | 129 -> 137 mods (+8)**

### Performance & Optimization
- Balm 7.3.38 -> **7.3.42**, Chunksending 2.8 -> **3.9**, Connectivity 5.6 -> **7.6**, FastSuite 5.1.2, FastAsyncWorldSave 2.6, Structure Layout Optimizer 1.0.11, SmoothChunk 4.1, Chloride 1.8.1, Cerulean 1.0.0, GPUTape 1.0.5.1 (debug only)

### QoL
- MouseTweaks 2.25.1, Cupboard 4.1, CrashAssistant 1.11.12, Structure Essentials 5.0, Vanillin 1.1.3, Placebo 8.6.3, Redirected 1.0.0, ServerCore 1.5.2, JEI 15.32.0.173-async

### Gameplay
- Aquaculture 2.5.7, Aquaculture Delight 1.1.0, Creeper Overhaul 3.0.2, Alex's Mobs Tweaks 1.3.0

### Sophisticated Suite (critical crash fix)
- Core 1.3.84 + Backpacks 3.24.67.2109 + Storage 1.4.86.2131 + Inventory Interactions 0.1.13.210 — fixed `NoSuchMethodError` (mandatory update from 1.2.0)

### Configs included
- BadOptimizations 40/8 + EntityCulling 96/5 + whitelist 22; Embeddium Fog Occlusion ON, Block Face Culling ON, Leaves FAST; ModernFix dynamic_resources=true, deduplicate_location=true

## [1.2.0] - 2026-08-30

### Added (8) - 30/08/2026
- **Ixeris 4.6.5 + Kerria 1.3.2 + gnetum 2.5.0 + asynclogger 2.2.2** - async chunk/render logging, smoother worldgen with Terralith/YUNG's
- **zfastnoise 1.0.13 + flerovium 1.2.19 + bocchium 0.0.3 + Icterine 1.3.0** - fast noise for worldgen (less CPU stutter)
- **AppleSkin 2.5.1** - hunger/saturation HUD

### Removed
- **GPUTape 1.0.5.1** - caused 100% GPU / fan at max even when idle (RTX 5060). Removed, GPU now stable at 60-75%.

### Kept Optimized (from V1.1)
- Noisium 2.3.0 + Saturn 0.1.3 + Clumps 12.0.0.4 + AI Improvements 0.5.2 + Smooth Boot Reloaded 0.0.4
- Tuned BadOptimizations (40/8) & EntityCulling (96/5, 22 whitelist)

## [1.1.0] - 2026-08-28

**Minecraft 1.20.1 | Forge 47.4.10 | 87 -> 129 mods (+42) | 6-8GB recommended**

- **Engineering with Create:** Create 6.0.8 + Addition, Steam Rails, Copycats, Structures Arise (was missing in V1)
- **Exploration & Dungeons:** DungeonsArise 2.1.58 + Deep Dark Regrowth 1.2.6.1 + Born in Chaos 1.7.5 + L_Ender's Cataclysm 3.31
- **Extended Cooking:** Croptopia 4.0.1 + Bountiful 6.0.4 + SliceAndDice 3.6.0
- **Optimization:** Noisium 2.3.0 + Saturn 0.1.3 + Clumps + AI Improvements + Smooth Boot + tuned configs (BadOptimizations 40/8, EntityCulling 96/5)
- **Combat:** Simply Swords 1.56.0 + Simply More 1.1.3
- **Configs Tuned:** BadOptimizations, EntityCulling, ModernFix/Embeddium vanilla for 100+ FPS

See full V1.1 changelog on [CurseForge](https://www.curseforge.com/minecraft/modpacks/panasrs-v-1/files).

## [1.0.0] - 2026-03-23

- Initial release - 87 mods - Panas /V1 is a mod pack where explore a living, technical world in Minecraft 1.20.1. Master the engineering in Create, survive epic dungeons, and create feasts with Farmer's Delight. Optimized for lag-free play with friends!