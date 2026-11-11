## [2.0.0] - 2026-11-09

### Added
- Guía de ajustes opcionales para equipos modestos: renderizado, simulación, entidades, mipmaps y shaders. No se presentan como una mejora de tiempo de generación hasta medirlos en el equipo afectado.
- Guía de perfiles de hojas: `panas-hojas` se recomienda para rendimiento en Gráficos Rápidos; en Gráficos Detallados se puede desactivar y Nautilus3D se ve correctamente, sin el bug visual observado en Rápido.

### Changed
- Texturas de los seis botones principales de FancyMenu actualizadas a 4× de resolución raster, con variantes normal, hover y desactivada. Se conservan dimensiones visibles, posiciones, IDs y funciones; la comprobación dentro del juego tras recargar queda pendiente.

### Fixed
- Evitado el conflicto entre el menú de herramientas de Create y la lista de habilidades de Relics: Create conserva Alt y Relics queda sin tecla predeterminada.
- Guía actualizada a las 14 fases, incluida Fase XIV: Jinetes de Dragón.

### Notes
- No se modificaron IDs, archivos ni recompensas de FTB Quests; el progreso de los mundos se conserva.
- No se cambiaron mods, configuraciones globales de memoria ni generación de estructuras. La optimización para equipos modestos es una recomendación opcional pendiente de medición A/B en la laptop de referencia.
- Antes de publicar el ZIP de CurseForge, incluye panas-hojas.zip en overrides/resourcepacks y verifica la selección/orden del pack en una instancia limpia.

# Changelog

All notable changes to Panas RPG will be documented here.

## [1.9.4] - 2026-11-08

### Fixed
- **El árbol de habilidades vuelve a abrirse.** Pulsar `K` mostraba la pantalla vacía ("Parece que no hay nada por acá…"). La causa no era el mod: los cuatro `experience.json` de 1.9.2 usaban el esquema antiguo (`conditions`/`parameters`) mientras el datapack se declara en formato nuevo (`version: 3`), y Puffish Skills 0.19.2 rechaza el pack entero. Al fallar un pack, el mod descarta **todas** las categorías, así que también desaparecían Combat, Mining, Class Skills y Weapon Skills. Los cuatro archivos están migrados a `variables` + `operations` (`puffish_skills:test` para item, bloque y NBT) y `experience` como expresión o lista de casos. Además se quitaron dos ids muertos del tag `panas:cocina` (`croptopia:dumpling`, `farmersdelight:pumpkin_pie`): de 565 a 563 platos y sin errores en el log.
- **La cama vuelve a funcionar y la noche pasa como en Minecraft.** Somnia exigía 20 de fatiga para dormir y mostraba "You're not tired yet". Ahora `minimumFatigueToSleep = 0`: la cama funciona en cuanto anochece. Además `fading = false` deja de retener el contador de sueño, así que Minecraft completa el descanso con su fundido y su skip normales (~5 s) en vez de la simulación de ~3 minutos. También se puede dormir con la armadura puesta (`sleepWithArmor = true`).
- **Crash al abrir "Mochilas, cofres y tuberías".** `AllTheLeaks` con `ingredientDedupe` activo bloqueaba el `ItemStack` de la mochila de Sophisticated Backpacks y lanzaba `ATLUnsupportedOperation` al renderizarla. Ahora `ingredientDedupe = false`; `resourceLocationDedupe` sigue activo.

### Changed
- **La fatiga ya no bloquea y ya no se cura durmiendo.** Se mantienen el contador, los efectos a 70/80/90/95 y el café. Dormir solo salta la noche (`fatigueReplenishRate = 0.0`); la fatiga baja únicamente con café. Si acumulas demasiadas horas despierto aparecen náuseas, lentitud y veneno, pero la cama nunca se niega.
- **Guía: nueva página "Ajustes y mobs"** en Controles Esenciales (10 páginas). Explica `Ctrl + K` / Dungeon Configs y que los mobs con nombre no desaparecen con Let Me Despawn.
- **Guía: "Descanso y fatiga" reescrita** para reflejar que la cama funciona en cuanto anochece, la noche pasa con el fundido y el skip normales, la armadura ya no estorba y la fatiga solo se cura con café.

### Notes
- Sin cambios de mods: siguen siendo 246, con los mismos 241 de CurseForge y 5 en `overrides/mods`.
- 1.9.4 añade únicamente los cuatro `experience.json` corregidos del datapack `panas-professions` y el tag `panas:cocina` limpio. Nada de configuración cambia respecto a 1.9.3.
- No hace falta mundo nuevo. El progreso de misiones, del libro y los puntos ya invertidos en los oficios se conservan.
- Si vienes de 1.9.2 y solo te interesa el crash, pon `"ingredientDedupe": false` en `config/alltheleaks.json` y reinicia. Para la cama hay que actualizar: el arreglo toca seis valores de `config/somnia-common.toml`.
- **Si vienes de 1.9.3**, el árbol no se arregla editando configs: los cuatro `experience.json` del datapack son los que cambian. Actualiza el pack o copia esa carpeta.
- No se añade ningún datapack nuevo: el salto de noche vuelve a ser el de Minecraft.

## [1.9.2] - 2026-11-02

### Added
- **Cuatro profesiones nuevas en Puffish Skills:** Ingeniería, Cocina, Caza y Exploración. Cada una sube hasta nivel 30, da 1 punto por nivel y tiene su propio árbol de 6 nodos. Se abren con `K`, junto a las pestañas que ya existían.
- **FASE XIV · Jinetes de Dragón:** diez misiones cooperativas de doma, cría, equipo y vuelo con Saint's Dragons.
- **Caza salvaje de dragones:** ocho contratos nuevos en Bountiful (uno por especie) además de las misiones de domesticación. El tablón pasa de 43 a 51 objetivos.
- **Loot temático por jefe:** 7 tablas nuevas inyectadas en 334 loot tables de Dungeons Arise, Cataclysm, YUNG's y Repurposed Structures.
- **Recompensas por nivel de jefe:** 4 tablas de tier y 51 funciones reescritas; cada jefe suelta botín acorde a su dificultad.
- **Entrada "Descanso y fatiga"** en la guía, con las cifras de Somnia y cómo desactivarlo.
- **Cuatro mods de cocina:** Create: Central Kitchen 1.5.1, Create: Garnished 2.1.7.c, Nether's Delight 4.0 y End's Delight 2.6.1. Añaden pasteles, frutos secos, guisos del Nether y carne de dragón; verificados contra Create 6.0.8 y Farmer's Delight 1.3.4.
- **Créditos y versión en la guía:** categoría nueva con 5 páginas. La versión se lee de un macro de `book.json`, así que se actualiza sola al cambiar el pack.

### Changed
- **Profesión de Cocina ampliada:** el tag `panas:cocina` pasa a 565 platos y bebidas (+136) e incluye los cuatro mods nuevos.
- **La guía de Saint's Dragons** pasa a 13 páginas: vida, armadura, umbral de doma, comida, hábitat y botín de las 8 especies, más el crisol, los binders y el resumen de drops.
- **"Habilidades y árbol de Skills"** explica la XP exacta de las 4 profesiones, el anti-farm y el ritmo de subida.
- **Somnia activa la fatiga** (beta): sube unos 2,5 puntos por minuto, exige 20 para dormir y acelera el tiempo ×100 mientras duermes. Se puede desactivar.
- **El café vuelve a funcionar:** café de Croptopia +10, granos +6, chocolate caliente +8 y caramelo de café +5.
- **Ajuste de rendimiento:** JVM de referencia con G1GC, pausas de 100 ms y heap fijo 4096–8064 MB; `Ixeris` sin busy-wait, terreno de Forge fuera del hilo principal, `Smooth Boot` a 10 hilos, `Embeddium` con 3 chunks de render-ahead, deduplicación en `AllTheLeaks` y `structure_layout_optimizer`, y `servercore` con caché de chunks ticking y lookups de bioma rápidos. `config/jei` limpio: se quitaron 11 backups, las carpetas `world/` y `server/` y 1,5 MB de caché; JEI puede regenerar 1–2 backups al arrancar.

### Fixed
- **Wither de la guía:** corregidas las cifras reales del pack (500 HP, embestida de 25 que rompe el escudo 20 s) y aclarado que no posee mobs ni usa las fases vanilla.
- **Calendario cooperativo:** el anuncio de nuevo día muestra el día real y recuerda que el tablón de caza sigue abierto.
- **Huérfano de recompensas:** eliminado `panas_boss_rews.json`, sustituido por `panas_boss_rews_v2.json`.

### Notes
- El libro no se entrega automáticamente: sigue saliendo de la misión de inicio.
- Sin respec para las cuatro profesiones: los puntos invertidos se quedan.
- Los cuatro mods de cocina ya vienen incluidos; no hay que instalarlos a mano.
- Actualización de contenido: no requiere mundo nuevo ni reinicia el progreso de misiones.
- El re-export debe llevar los 4 jars nuevos, el tag `panas:cocina` actualizado, la guía con créditos y `config/jei` limpio.
- 246 mods en total: 241 se descargan desde CurseForge y 5 viajan en `overrides/mods` (Clumps, Controlling, Easy Mob Farm, Fabric API, Searchables). El release de GitHub añade el paquete completo con todos los mods y configs para instalación manual.

## [1.9.1] - 2026-10-28

### Added
- **Guía de Supervivencia ilustrada:** 49 páginas nuevas con renders nativos de Patchouli (`spotlight` de ítems y `entity` de criaturas). El libro pasa de 130 a 177 páginas y de 49 a 98 páginas con imagen.
- **Otros jefes del pack:** la entrada pasa de 4 a 17 páginas e incluye 12 criaturas renderizadas: Wilden Chimera, Wildfire, Amethyst Crab, Kobolediator, Wadjet, Ancient Guardian, Frostbitten Golem, Lava Eater, Withered Abomination, Atroxiia, Cindervane y Stalker, con dónde aparece cada una.
- **Controles Esenciales:** teclas reales del pack, teclas que vienen sin asignar y conflictos entre mods.

### Changed
- **11 entradas reescritas** con texto más corto y didáctico: mochilas y tuberías, Create y trenes, atlas de exploración, magia, clases y stats, jefes y tumbas, expediciones, árbol de habilidades, cocina y jefes varios.
- Los textos explican el "cómo" en pasos cortos y dejan el detalle a las imágenes.

### Fixed
- **Teclas corregidas:** `G` es la habilidad especial de Alex's Caves, no de RPG Series; Simply Swords y Spell Engine vienen **sin asignar**; Combat Roll usa **Caps Lock**.

### Notes
- Actualización centrada en la guía: no cambia misiones, botín, calendario ni economías.
- Si un render no carga al entrar, pulsa `F3+T` o reinicia el cliente.
- El progreso y los marcadores del libro se conservan.

## [1.9] - 2026-10-27

### Added
- **FASE IX · Crónicas de los Panas:** seis misiones cooperativas de preparación, provisiones, regreso y metas de 7, 14 y 30 días de Minecraft.
- **FASE X · Ingeniería en movimiento:** trenes, vías, estaciones, horarios y viajes largos con Create.
- **FASE XI · La despensa de los Panas:** cultivos, pesca y cocina cooperativa con Farmer’s Delight y Aquaculture.
- **FASE XII · Maestría de clase:** objetivos de equipo para las cuatro clases RPG y una meta del árbol de habilidades.
- **FASE XIII · Atlas de tierras salvajes:** exploración de biomas de Regions Unexplored y Terralith, con un reto amplio opcional.
- Calendario cooperativo del mundo mediante Paxi: anuncio de nuevos días y metas compartidas de 7, 14 y 30 días.
- Ping Wheel para marcar temporalmente lugares y criaturas durante las expediciones.
- Patchouli guide entry **"Expediciones y Cooperación"**, sobre el calendario, la coordinación del equipo, Ping Wheel y ajustes gráficos opcionales.
- Mensaje personalizado de bienvenida de Panas RPG en el chat al entrar al mundo.
- Los contratos de Bountiful entregan un objeto distintivo del jefe objetivo, entre 1 y 6 diamantes y exactamente 1 manzana dorada; la moneda escala por rareza: 4 de hierro (rara), 1 de oro (épica) o 1 de esmeralda (legendaria).


### Changed
- Las fases IX–XIII están organizadas en grupos desplegables, siguiendo la estructura de capítulos existente.
- Desactivado el anuncio automático de JourneyMap en el chat al entrar al mundo; se muestra el mensaje de bienvenida personalizado de Panas RPG.
- La Guía de Supervivencia refleja los capítulos ampliados, las expediciones cooperativas y la escala de recompensas de jefes.
- **Economía cooperativa entre panas:** las monedas nuevas se obtienen como recompensas de FTB Quests y contratos de caza Bountiful; se desactivan la acuñación, los botines de criaturas/cofres y las recompensas y sustituciones de eventos. Las tiendas de Lightman's Currency siguen habilitadas para intercambiar monedas por artículos.

### Notes
- La meta del árbol de habilidades de la Fase XII se marca manualmente después de gastar un punto de clase.
- Los objetivos de biomas de la Fase XIII pueden requerir explorar terreno nuevo; la meta final de todos los biomas es opcional.
- Las monedas que ya existían en un mundo no se eliminan; la restricción afecta a nuevas emisiones tras cargar la configuración.

## Panas RPG v1.8.2 - Libro, limpieza y rebalanceo de botin

**Release Date:** October 16, 2026
**Status:** Release • Testers needed • Feedback appreciated

### Added
- **Guia "Habilidades y Arbol de Skills"** en el libro: tecla K, las 4 pestanas (Combat, Mining, Class Skills, Weapon Skills), como se ganan puntos y XP, y clases y especializaciones de arma.
- **Rebalanceo del botin de Dungeons Arise** (nuevo datapack global `panas-loot`): diamantes a 1/3 de peso y max 1; encantamientos max III; encantamientos solo en hierro; manzana encantada mucho mas rara. Sobreescribe las 131 loot tables del mod.

### Fixed
- **El libro "Cronicas de Panas RPG" no abria** (el item mostraba `Invalid book`): restaurado a su ruta correcta (`patchouli_books/` en la raiz del juego) y eliminada la copia inutil de `config/patchouli_books/`.
- **Datapacks ahora cargan correctamente:** se agrego **Paxi** para datapacks globales en `config/paxi/datapacks/`; el datapack de loot estaba en una ruta invalida y no aplicaba.
- **Limpieza de datapacks invalidos:** eliminada la carpeta inerte `datapacks/data` (sin `pack.mcmeta`).
- **Icono de libro (Field Guide) desactivado** en el menu de pausa y el inventario.
- **Mensajes de entrada desactivados:** SecurityCraft, Streams Reflowing y Cataclysm.



### Changed
- Texto del libro: reemplazado el amarillo por naranja (`#FF8000`) para mejor visibilidad.
- **JourneyMap:** desactivado el anuncio automatico del mod en el chat.
- **Terralith:** desactivado el mensaje de bienvenida mediante el datapack `terralith-no-toast`.

### Known issues
- El rebalanceo de botin solo afecta cofres nuevos o sin abrir; los ya abiertos conservan su contenido.

## Panas RPG v1.8.1 - Guia de Jefes & Fix de Combate

**Release Date:** October 16, 2026
**Status:** Release • Testers needed • Feedback appreciated

### Added
- **Guia "Jefes"** en el libro (13 entradas): todos los jefes del pack agrupados por mod (Cataclysm, Legendary Monsters, Mowzie's, Born in Chaos, Mutant Monsters, Myths & Legends, Graveyard, Undergarden, Alex's Caves/Mobs, Saint's Dragons, vanilla y mas) con que hacen, como encontrarlos/invocarlos y sus drops reales (con el modelo del mob renderizado).
- **Guia "Habilidades"** en el libro (nueva entrada): explica como funcionan las skills y el arbol — tecla K, las 4 pestanas (Combat, Mining, Class Skills, Weapon Skills), como se ganan puntos y XP, y el listado de clases y especializaciones de arma.

### Fixed
- **Punchy × Better Combat:** restaurada la animacion de ataque en primera persona (se cancelaba en cada golpe).
- **Mision "Quimica verde" (FASE VIII):** corregida al advancement correcto (`mutantmonsters:gunpowder_spice`).



### Changed
- RAM mas nivelada (sin picos de GC de varios segundos).
- Punchy `2.7e → 2.8f`; `bettercombatCompat → false`, `firstPersonAnimations → YES`; ajuste G1GC (`MaxMemAlloc=8064`).

### Known issues
- GeckoLib: animaciones de Saint's Dragons / Myths & Legends (solo visual).
- Skill Tree: `critical_strike:chance` sin provider (el juego funciona igual).
- 237 mods → 6–8 GB de RAM recomendados.

## [1.8] - 2026-10-13

### Added
- FASE VIII · Expansion: 57 new FTB Quests covering gaps I–VII, each with themed rewards plus coins (cooking, economy/storage, jewelry/runes, bosses, Create extras, Ars extras, dimensions, advancements, endgame).
- Combat Roll 1.3.3 (dodge-roll mechanic, rebindable key).
- AsyncParticles 20.1.4.1 (async/GPU particle tick and rendering).
- RuOK FPS HUD on; Kerria `fastLightTextureUpload` on.
- GeckoLib animation fixes: Born in Chaos `"-"` placeholders (babyskeleton ×2, boneimp, scarletpersecutor) + Elokesa spacing cleanup — zero animation parse failures in log.



### Changed
- AI-Improvements: `remove_look_random` on; Foliaath 70→45, Gazelle 40→28 (outliers only).
- ModernFix: +`clear_mixin_classinfo`; EntityCulling 96/5 → 128/10.
- Removed `.duplicate` jar + orphan configs (c2me, canary, lithium, DistantHorizons).

### Fixed
- `combat_roll:recharge` now resolves (was missing provider).

### Known issues
- `critical_strike:chance` still without provider (3 skill bonuses inactive, game unaffected).

## [1.7.3] - 2026-10-13

### Added
- Custom window icon via FancyMenu (full pack branding, no manual steps).
- Working survival guide book: delivered automatically in new worlds, all content visible.
- Custom No-Premium launcher: Panas RPG Launcher (https://github.com/rongorus1/LauncherPanasRPG/releases) — no premium account, no complicated setup, just download and play.

### Coming soon
- Performance update so the pack loads the CPU less (normal update, no config or world wipe needed).

## [1.7.2] - 2026-10-12

Release `v-1.7.2` publicado (GitHub + CurseForge): `Panas.RPG.1.7.2.zip` (35.7 MB).

### Added
- Bundle: `manifest.json` (234 archivos) + `overrides/` (`config`, `datapacks`, `fancymenu_data`, `mods` ×6, `resourcepacks`).
- 219 → 240 mods cargados (detalle por mod pendiente).



### Changed
- Sin cambios de quests (FASE I–VII de v1.7) ni de configs documentados.

## [1.7.1] - 2026-09-27

### Added
- Fixed skill tree dependencies issue
- Added Archers (RPG Series) mod
- Added Paladins & Priests (RPG Series) mod
- Added Rogues & Warriors (RPG Series) mod
- Added Wizards (RPG Series) mod

### Fixed
- Fixed skill tree branch issue
- Fixed missing dependencies for RPG classes
- System now works correctly with all skills enabled



### Changed
- Updated RPG series mods integration
- Improved skill tree stability

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
  4. `spell_engine` (BEFORE) — registers spell engine effects
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

- **v1.7.0** (Sep 2026): +7 mods, +43 quests (FASE VII), load order fix, attribute fixes, 215 mods total
- **v1.6.0** (Sep 2026): Cinematic menus + video loading screens with full audit, Chloride crash fix
- **v1.5.2** (Sep 2026): Full mod set restored (206), texture pack lineup completed
- **v1.5.1** (Sep 2026): 8 mods restored, Fabric API backend, deepslate + Eating Animation fixes
- **v1.5.0** (Sep 2026): 19 new mods added, VoiceChat update, biome expansion, performance fixes
- **v1.4.0** (Aug 2026): Initial release – 179 mods, Terralith + Cultural Delights, Create suite

---

## 💬 Feedback

Report bugs or issues on CurseForge page or join Discord: discord.gg/panas-rpg

---

## Era V1–V1.3.1 (Ago 2026, rescatado de CurseForge)

### [V1] — Lanzamiento inicial (87 mods)
Base técnica + exploración + cocina (Create, Dungeon Crawl, Farmer's/Alex's Delight).

### [V1.1] — Living, Technical World (87 → 129 mods, +42)
Create expandido (6.0.8, Addition, Steam Rails, Copycats, BetterFPS, Easy Structures, Enchantment Industry, Structures Arise); mazmorras (DungeonsArise, Deep Dark Regrowth, Born in Chaos, L_Ender's Cataclysm); cocina profesión (Croptopia, Bountiful, SliceAndDice); QoL (FTB Quests, Controlling, VoiceChat, Patchouli, Lightman's Currency); Simply Swords; Noisium/Saturn/Clumps/AI Improvements/Smooth Boot; configs para 130 FPS base.

### [V1.2] — Optimization Patch (129 → 137, 30/08/2026)
Ixeris/Kerria/gnetum/asynclogger + zfastnoise/flerovium/bocchium/Icterine + AppleSkin. GPUTape eliminado (100% GPU en idle).

### [V1.3] — Performance & Content (30/08/2026)
Balm/Chunksending/Connectivity/FastSuite/FastAsyncWorldSave/SLO/SmoothChunk/Chloride/Cerulean; MouseTweaks/Cupboard/CrashAssistant/Vanillin/Placebo/Redirected/ServerCore/JEI-async; Aquaculture 2 + Delight, Creeper Overhaul, Alex's Mobs Tweaks; Sophisticated Suite alineada (fix NoSuchMethodError).

### [V1.3.1] — Full Update & Policy Workaround (137 → 145, 31/08/2026)
~120 mods actualizados; 8 mods por políticas como dependencias externas en `manifest.json` (EcoTask, Corail Tombstone, Voicechat, Simply More 1.1.4, Entity Culling, Balm, Sophisticated Storage/Inventory); fixes RunicSwordItem, createaddition:cake_base, SophisticatedCore.registerMessage. (En CF el encabezado dice "V1.4" por error.)
