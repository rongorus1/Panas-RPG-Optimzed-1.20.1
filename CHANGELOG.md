# Panas RPG v1.8.0 - Changelog

**Fecha:** 24 de Septiembre, 2026  
**Minecraft:** 1.20.1 | **Forge:** 47.4.10  
**Mods totales:** 215 (+7 nuevos)

---

## 🎯 **Fixes Críticos - Load Order & Atributos**

### **Load Order & Registro de Atributos**
- ✅ **Load Order fixado** en 5 mods críticos via `mods.toml` (`ordering = "BEFORE"` / `"AFTER"`)
- ✅ **Duplicados eliminados** en `mods.toml` (causaban crash `entry "[ordering]" defined twice`)
- ✅ **Dependencia `puffish_skills`** restaurada en `skill_tree` con `ordering = "AFTER"`
- ✅ **Load Order final:**
  1. `ranged_weapon_api` (BEFORE)
  2. `spell_power` (BEFORE)
  3. `spell_engine` (BEFORE)
  4. `skill_tree` (depende de los anteriores)
  4. `jewelry` (depende de los anteriores)
  5. `puffish_skills` (AFTER - carga último)

### **Errores de Atributos Resueltos**
- ❌ `Failed to resolve EntityAttribute: critical_strike:chance`
- ❌ `Failed to resolve EntityAttribute: ranged_weapon:haste/damage/velocity`
- ❌ `Failed to resolve EntityAttribute: combat_roll:recharge`
- ❌ `Registry minecraft:mob_effect: Object did not get ID it asked for`

---

## 🎒 **Nuevos Mods Añadidos (+7 mods)**

| Mod | Versión | Qué Añade |
|-----|---------|-----------|
| **Legendary Monsters** | 2.2.3 | 15+ jefes legendarios con mecánicas únicas (Fenrir, Quetzalcoatl, Anubis, etc.) |
| **Grim Kingdoms: Lost Structures** | v1.0.3 | ~100 estructuras: castillos, torres, ruinas, naves, reinos |
| **Skill Tree (RPG Series)** | 1.6.1 | Árbol de habilidades con 100+ nodos, XP compartido en coop |
| **Runes (RPG Series)** | 1.3.2 | Runas crafteables con efectos mágicos |
| **Jewelry (RPG Series)** | 2.4.0 | Joyería con gemas: anillos, collares, atributos configurables |
| **Shield Expansion** | 1.3.7 | Nuevos escudos con habilidades únicas |
| **Grim Kingdoms: Lost Structures** | v1.0.3 | Estructuras vanilla+: castillos, torres, ruinas, naves |

**Total mods:** 215 (+7 nuevos)

---

## 📜 **Nuevas Misiones FTB Quests (+43 misiones / 7 Fases)**

### **FASE I - El Despertar (+4 misiones)**
- **El huerto** - Plantar 8 semillas (recompensa: Hoe de madera Croptopia)
- **El arte de la cocción** - Cocinar 4 arroces (recompensa: Skillet Farmer's Delight)
- **Mi primer mochila** - Craftear mochila básica (recompensa: Stack Upgrade Tier 1)
- **El primer viaje** - Usar Waystone (recompensa: 2x Warp Scroll)

### **FASE II - Bajo la Superficie (+5 misiones)**
- **Create: La rueda de agua** - Craftear Water Wheel (recompensa: Shaft)
- **Create: El molino** - Craftear Millstone (recompensa: Cogwheel)
- **Create: Tuberías** - 4x Fluid Pipe (recompensa: Mechanical Pump)
- **Peces de profundidad** - Pescar 3 bacalaos (recompensa: Fish Fillet Aquaculture)
- **El primer refugio** - Puerta Macaw's (recompensa: Sofa Handcrafted)

### **FASE III - Abismos del Océano (+5 misiones)**
- **Buceador experimentado** - Craftear Conduit (recompensa: Fluid Tank Create)
- **Pesca abisal** - 5 bacalaos (recompensa: Fish Fillet)
- **Ars Nouveau: Primer hechizo** - Scribe's Table (recompensa: Arcane Core)
- **Ars Nouveau: Familiar** - Ritual Bowl (recompensa: Dominion Wand)
- **Ciudad sumergida completa** - Advancement (recompensa: Flippers Artifacts)

### **FASE IV - Arenas y Llamas (+5 misiones)**
- **Create: La fundición** - Mechanical Saw (recompensa: Blaze Burner)
- **Create: El tren** - Train Controls (recompensa: 8x Track)
- **Bountiful: Primer contrato** - Bounty Board (recompensa: 5x Iron Coins)
- **Lightman's: Mi primera tienda** - Portable Terminal (recompensa: 1x Iron Coin)
- **Simply Swords: Espadas legendarias** - 3 espadas (recompensa: Nordic Sword)

### **FASE V - Cazadores de Gigantes (+6 misiones)**
- **Mowzie's: Frostmaw** - Derrotar Frostmaw (recompensa: Ice Crystal)
- **Mowzie's: Naga** - Derrotar Naga (recompensa: Earthrend Gauntlet)
- **Ars Nouveau: Ritual mayor** - Ritual Tablet (recompensa: Archmage Spell Book)
- **Artifacts: Reliquia** - Shock Absorber (recompensa: Cloud in a Bottle)
- **Create: Fábrica automática** - Creative Motor (recompensa: 4x Brass Casing)
- **Mutant Monsters: Mutante** - Derrotar Mutant Zombie (recompensa: Mutant Heart)

### **FASE VI - El Cataclismo (+5 misiones)**
- **Ars Nouveau: Dominio total** - Archmage Spell Book (recompensa: Summon Focus)
- **Create: El cañón de vapor** - Steam Cannon (recompensa: Brass Hand)
- **Lightman's: Mega tienda** - Network Upgrade (recompensa: 1x Netherite Coin)
- **Explorador supremo** - Void Upgrade (recompensa: Everlasting Upgrade)
- **El final verdadero** - Ender Dragon (recompensa: Ender Edge Simply Swords)

### **FASE VII - La Civilización (NUEVA - 12 misiones)**
- **Create: Ciudad de Create** - Creative Motor
- **Ars Nouveau: Escuela de magia** - Starbuncle Charm
- **Economía: Banco central** - ATM Tablet
- **Agricultura: Granja industrial** - Liquid Fertilizer + Mechanical Harvester
- **Decoración: Palacio** - Wood Supports (Chipped)
- **Mochila final** - Independence Upgrade
- **Create: Tren transcontinental** - Locomotive
- **Ars Nouveau: Archmage** - Amplify Arrow
- **Comerciante supremo** - Network Card
- **El mundo completo** - Flare Upon (Artifacts)
- **Maestro constructor** - Coffee Table (MCW Furniture)
- **Panas RPG: Platinum** - Netherite Coin (logro final)

---

## ⚙️ **Configs Aplicadas**

| Archivo | Cambios Clave |
|---------|---------------|
| `mythsandlegends-common.toml` | `spawnWeightMultiplier = 0.3`, `minBossSpawnDistance = 500`, `globalBossCooldown = 24000`, compat Terrablender |
| `saintsdragons/servercommon.toml` | `dragonSpawnWeightMultiplier = 0.4`, `dragonSpawnChance = 0.05`, `minDragonSpawnDistance = 200` |
| `saintsdragons/spawning.toml` | Spawn weights reducidos 60-80%, `globalSpawnWeightMultiplier = 0.4` |
| `witherreincarnated/common.toml` | Health 500, daño reducido, cooldowns aumentados, **posesión undead DESACTIVADA** |
| `undergarden-client.toml` | Key fix: `toggleUndergardenFog = true` |
| `terrablender.toml` | Prioridades: Undergarden(100) > Myths(80) > Saints(60) > BiomesWe'veGone(50) > Terralith(40) |
| `legendarymonsters-common.toml` (nuevo) | `spawnWeightMultiplier = 0.25`, `minBossDistance = 600` |
| `skill_tree` mods.toml | `ranged_weapon_api` BEFORE, `spell_power` BEFORE, `spell_engine` BEFORE, `puffish_skills` AFTER |
| `jewelry` mods.toml | `ranged_weapon_api` BEFORE (era AFTER), `spell_power` BEFORE |
| `spell_engine` mods.toml | `spell_power` BEFORE |

---

## 🗑️ **Eliminados / Conflictos Resueltos**

| Elemento | Acción | Motivo |
|----------|--------|--------|
| `puffish_skills` dependencia en `skill_tree` | Temporalmente eliminada, luego restaurada con `ordering = "AFTER"` | Cargaba datapack antes de que existieran atributos |
| Duplicados `ordering` en `mods.toml` | Eliminados todos los duplicados | Causaban crash `entry "[ordering]" defined twice` |
| Duplicados de JARs | Eliminados originales tras renombrar | Conflictos de modId duplicado |

---

## 📦 **Mods Actualizados / Fixados**

| Mod | Acción |
|-----|--------|
| `skill_tree` | `mods.toml` fixado + dep `puffish_skills` restaurada (AFTER) |
| `jewelry` | `ranged_weapon_api` AFTER → BEFORE |
| `spell_engine` | `spell_power` BEFORE |
| `skill_tree` | `ranged_weapon_api` BEFORE, `spell_power` BEFORE, `spell_engine` BEFORE, `puffish_skills` AFTER |
| `jewelry` | `ranged_weapon_api` AFTER → BEFORE, `spell_power` BEFORE |
| `spell_engine` | `spell_power` BEFORE |
| Duplicados `ordering` | Eliminados en 5 mods.toml |

---

## 📋 **Para CurseForge - Próximos Pasos**

1. **Subir 7 mods nuevos** al manifest con projectIDs
2. **Actualizar `manifest.json`** con nuevos projectIDs y fileIDs
3. **Subir configs** (`config/` en overrides)
4. **Subir quests** (`config/ftbquests/quests/` en overrides)
5. **Changelog en CurseForge** (usar este Markdown)

---

## ✅ **Testing Checklist**

- [ ] Iniciar juego sin errores de atributos
- [ ] Skill Tree (tecla `K`) funciona
- [ ] Jewelry - craft joyería funciona
- [ ] Legendary Monsters - jefes spawnean
- [ ] Grim Kingdoms - estructuras generan
- [ ] Trials Chambers (`/locate structure minecraft:trial_chambers`)
- [ ] Wither Reincarnated - spawnear Wither
- [ ] FTB Quests - nuevas misiones visibles
- [ ] Skill Tree (tecla `K`) - árbol abre correctamente
- [ ] Jewelry - craft joyería en mesa
- [ ] Runes - craft runas
- [ ] Shield Expansion - craft escudos

---

**Generado:** 24/09/2026  
**Versión:** 1.8.0  
**Autor:** Panas RPG Team