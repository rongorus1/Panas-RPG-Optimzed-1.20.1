# Panas RPG — Changelog para CurseForge

Version larga (anuncio de release) que se pega a mano en la pagina del proyecto en CurseForge.
No confundir con `CHANGELOG.md` (version breve para GitHub).

---

Panas RPG v1.8.2 - Libro: contenido nuevo y fix

Release Date: October 16, 2026
Status: Release • Testers needed • Feedback appreciated

🆕 What's New
📖 Guia de Supervivencia — contenido nuevo
- Nueva entrada "Habilidades y Arbol de Skills": como abrir el arbol (tecla K), las 4 pestanas (Combat, Mining, Class Skills, Weapon Skills), como se ganan puntos y experiencia, y el listado de clases y especializaciones de arma.

🔧 Fixes
- El libro "Cronicas de Panas RPG" no se abria (el item decia "Invalid book: patchouli:guia_supervivencia"): estaba en la carpeta equivocada. Restaurado a su ruta correcta (patchouli_books/ en la raiz del juego) y eliminada la copia inutil en config/patchouli_books/.
- No hay que recrear el mundo: basta con actualizar y recargar.

⚙️ Changed
- Texto del libro: reemplazado el color amarillo por naranja (#FF8000) para mejor visibilidad.

📦 Installation
- Los cambios del libro se aplican solos, sin pasos manuales.
- Si el libro no abre tras actualizar, recarga con F3+T o reinicia el cliente.

---

Panas RPG v1.8.1 - Guia de Jefes & Fix de Combate

Release Date: October 16, 2026
Status: Release • Testers needed • Feedback appreciated

🆕 What's New
📖 Guia de Supervivencia — seccion "Jefes" + explicacion de "Habilidades"
- Nueva categoria + 13 entradas que cubren TODOS los jefes del pack, agrupados por mod: Vanilla/Wither Reincarnated, Cataclysm (8), Legendary Monsters, Mowzie's Mobs, Born in Chaos, Mutant Monsters, Myths & Legends, The Graveyard, The Undergarden, Alex's Caves, Alex's Mobs, Saint's Dragons y varios (Ars Nouveau, Friends & Foes, Deep Dark Regrowth).
- Cada jefe indica QUE HACE, COMO ENCONTRARLO/INVOCARLO y su RECOMPENSA real (extraida de los loot tables), con paginas que renderizan el modelo del mob.
- Nueva entrada "Habilidades y Arbol de Skills": como abrir el arbol (tecla K), las 4 pestanas (Combat, Mining, Class Skills, Weapon Skills), como se ganan puntos y experiencia, y el listado de clases y especializaciones de arma.
- Libro en su ruta correcta (patchouli_books/ en la raiz del juego).

🔧 Fixes
- Animacion de ataque en primera persona (Punchy × Better Combat): con bettercombatCompat activado, Punchy cancelaba la animacion de Better Combat en cada golpe (el daño entraba pero no se veia el ataque). Ahora conviven: Punchy mantiene movimiento/manos y Better Combat maneja el ataque en primera persona.
- Mision FTB "Quimica verde" (FASE VIII): apuntaba a un item inexistente (mutantmonsters:chemical_x); corregida al advancement correcto (mutantmonsters:gunpowder_spice).

⚡ Performance
- RAM mas nivelada: la memoria ahora se estabiliza (sin picos de GC de varios segundos).

⚙️ Changed
- Punchy 2.7e → 2.8f (ultima para Forge 1.20.1).
- config/punchy/punchy_config.json: bettercombatCompat → false.
- config/bettercombat/client.json5: firstPersonAnimations → "YES" (brazos visibles en primera persona).
- JVM/memoria (Prism): ajuste G1GC + MaxMemAlloc=8064, MinMemAlloc=512; eliminado watermedia.toml.

🖥️ Recommended setup for this update
- RAM: 6 GB (8 GB PC) o 8 GB (16 GB PC) — no asignarla toda.
- JVM flags: -Xms8G -Xmx8G -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 (ajusta al tamaño de tu RAM).
- Cierra apps en segundo plano (navegador, Discord, launchers).

⚠️ Known Issues
1. GeckoLib animations — Saint's Dragons / Myths & Legends tienen animaciones rotas (solo visual, sin crash).
2. Skill Tree: 3 bonus de skill inactivos (critical_strike:chance sin provider aun — el juego funciona bien).
3. FancyMenu resource errors — cosmetico, sin impacto en el juego.
4. StructureEssentials — "Non-unique structure_set salt" (preexistente, solapamiento ocasional de estructuras).
5. Biome stability — Oh The Biomes packs pueden chocar con la generacion de Terralith.
6. FPS impact — 237 mods activos — se recomiendan 6–8 GB de RAM.

📦 Installation
- Haz copia de seguridad de worlds/ antes de actualizar.
- Borra la carpeta mods/ antigua para evitar conflictos.
- Los cambios de configs/guia se aplican solos, sin pasos manuales.
- Se recomienda mundo nuevo para quien juegue por primera vez.

📈 Version History
- v1.8.2 (Oct 2026): contenido nuevo y fix del libro, color naranja
- v1.8.1 (Oct 2026): seccion Jefes + explicacion de habilidades en el libro, fix Punchy × Better Combat, fix mision Quimica verde, ajuste de RAM
- v1.8 (Oct 2026): FASE VIII quests, optimizacion CPU, fixes GeckoLib, Combat Roll
- v1.7.3 (Oct 2026): icono de ventana FancyMenu, libro guia funcional, anuncio de optimizacion
- v1.7.2 (Oct 2026): bundle manifest 234 + overrides, 240 mods cargados
- v1.7.1 (Sep 2026): +4 mods RPG Series, fix dependencia skill tree, 219 mods
- v1.7 (Sep 2026): +7 mods, +43 quests (FASE VII), fix load order, fixes de atributos, 215 mods
- v1.6.1 (Sep 2026): menus estaticos, Watermedia eliminado, Upgrader Items añadidos
- v1.6.0 (Sep 2026): menus cinematicos + pantallas de carga con video, fix crash Chloride
- v1.5.2 (Sep 2026): set completo de mods restaurado (206), lineup de texture packs
- v1.5.1 (Sep 2026): 8 mods restaurados, backend Fabric API, fixes deepslate + Eating Animation
- v1.5.0 (Sep 2026): 19 mods nuevos, update VoiceChat, expansion de biomas
- v1.4.0 (Aug 2026): release inicial – 179 mods, Terralith + Cultural Delights, Create suite
