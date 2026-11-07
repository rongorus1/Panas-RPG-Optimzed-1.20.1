# Panas RPG — Changelog para CurseForge

Version larga (anuncio de release) que se pega a mano en la pagina del proyecto en CurseForge.
No confundir con `CHANGELOG.md` (version breve para GitHub).

---

Panas RPG v1.9.3 — La cama vuelve a ser la cama

**Fecha de publicación:** 6 de noviembre de 2026
**Estado:** Release
**Mods:** sin cambios respecto a 1.9.2

## 🛏️ La cama vuelve a ser la cama

En 1.9.2, Somnia pedía **20 de fatiga** para dejarte dormir. Si llevabas menos de ocho minutos despierto, la cama te respondía **"You're not tired yet"** y no había forma de pasar la noche. Después, aunque ya podías dormir, Somnia retenía el contador de sueño y simulaba el mundo tick a tick: había que esperar **casi 3 minutos** hasta que amanecía. Para un jugador de Minecraft eso no es una mecánica: es un bloqueo y una pérdida de tiempo.

En 1.9.3:

- **Puedes dormir en cuanto anochece**, con o sin fatiga.
- **La noche pasa como en Minecraft.** `fading = false` deja de retener el contador de sueño, así que Minecraft completa el descanso con su fundido a negro, su amanecer y su despertar de siempre, en unos **5 segundos**. La espera de ~3 minutos desaparece.
- **Puedes dormir con la armadura puesta.** Se acabó tener que desnudarte en plena mazmorra.
- **Dormir ya no reduce la fatiga** (`fatigueReplenishRate = 0.0`). La cama solo pasa la noche; la fatiga se cura con café.
- El **reloj de despertar** queda desactivado (`wakeTimeSelectItem = ""`): el pack vuelve al sueño de Minecraft, sin elegir hora.
- La **ventana de sueño vuelve a ser la de vanilla** (`12542–23460`): solo de noche.
- **En cooperativo se duerme como en vanilla:** tienen que dormir todos, o el porcentaje que marque la gamerule.
- Los **monstruos cerca siguen bloqueando** el descanso, como en Minecraft. Eso no se toca.

### La fatiga ahora es una consecuencia, no un requisito

El contador y los efectos se quedan enteros. Lo que cambia es que ya no te impiden dormir y que dormir no los cura:

- Sube unos **2,5 puntos por minuto**; a los 40 minutos estás al máximo.
- **70:** náuseas cortas.
- **80:** lentitud II.
- **90:** veneno.
- **95:** náuseas permanentes hasta que bajes con café.
- El café de Croptopia (+10), los granos (+6), el chocolate caliente (+8) y el caramelo de café (+5) siguen ayudando.

Dormir está permitido en cuanto anochece, pero ya no reinicia la fatiga: si encadenas días sin café, los efectos se acumulan. Si la beta te resulta incómoda, `enableFatigue = false` en `config/somnia-common.toml` la desactiva sin romper nada más.

## 🎒 Crash de mochilas resuelto

Abrir la página 2 de **"Mochilas, cofres y tuberías"** (o mirar la mochila en JEI) cerraba el juego con:

```
dev.uncandango.alltheleaks.exceptions.ATLUnsupportedOperation:
An Ingredient that contains this itemstack was cached and locked by mod AllTheLeaks,
modifications of ItemStacks in Ingredients are not allowed!
```

No era falta de RAM ni el libro: el heap iba por 2.049 MB de 8.064 MB. Era `AllTheLeaks` con `ingredientDedupe` activo. Sophisticated Backpacks escribe NBT en la mochila para cachear sus ranuras, y esa mochila estaba dentro de un `Ingredient` bloqueado por AllTheLeaks. El propio autor del mod desaconseja esa opción en 1.20.1.

En 1.9.3:

- `"ingredientDedupe": false` en `config/alltheleaks.json`.
- `"resourceLocationDedupe": true` se mantiene: esa sí es segura y sigue ahorrando memoria.

## 📖 Guía actualizada

- **Controles Esenciales** pasa a 10 páginas con **"Ajustes y mobs"**: el botón **Dungeon Configs** (o `Ctrl + K`), qué hace Let Me Despawn y por qué ponerle nombre a un mob lo protege.
- **Descanso y fatiga** se reescribe: la cama funciona en cuanto anochece, la noche pasa con el fundido y el skip normales, la armadura ya no estorba y la fatiga solo se cura con café.
- **34 archivos JSON validados**, sin BOM.

## 🔧 Cambios técnicos

- `config/alltheleaks.json`: `ingredientDedupe` de `true` a `false`.
- `config/somnia-common.toml`: `minimumFatigueToSleep` de `20` a `0`; `sleepWithArmor` de `false` a `true`; `fading` de `true` a `false` (Somnia deja de retener el contador de sueño); `fatigueReplenishRate` de `0.00833` a `0.0` (dormir no cura la fatiga); `wakeTimeSelectItem` de `minecraft:clock` a `""` (reloj de despertar desactivado); `enterSleepStart`/`enterSleepEnd` de `0`/`24000` a `12542`/`23460` (solo de noche); `validSleepStart`/`validSleepEnd` a `24000`/`24000` (ventana de simulación vacía).
- La ventana `validSleep` vacía desactiva la aceleración de Somnia (`isValidSleepTime` es lo único que la habilita): el reloj no se adelanta mientras duermes y el skip lo hace Minecraft con su transición normal.
- No se añaden datapacks: el salto de noche vuelve a ser el de Minecraft.
- `patchouli_books/guia_supervivencia/en_us/entries/controles_esenciales.json`: página nueva y nota de `Ctrl + K`.
- `patchouli_books/guia_supervivencia/en_us/entries/descanso_y_fatiga.json`: 5 páginas reescritas.
- README: problemas conocidos de AllTheLeaks, Let Me Despawn y fatiga actualizados.

## 📦 Instalación

- Actualiza normalmente desde CurseForge o Prism Launcher.
- No hace falta mundo nuevo: los cambios son de configuración y del libro, así que el progreso de misiones y la lectura se conservan.
- **Instalación manual:** en el release de GitHub está `Panas.RPG-1.9.3-Mods.Completo.rar` con todos los mods, configs, quests y guía; descomprime su contenido en `.minecraft`.
- Si arrastras una config vieja de 1.9.2, comprueba los seis valores de `config/somnia-common.toml` y `ingredientDedupe` en `config/alltheleaks.json`; el pack nuevo ya los trae.

## ⚠️ Si vienes de 1.9.2

Puedes arreglar el crash sin actualizar el pack: abre `config/alltheleaks.json`, pon `"ingredientDedupe": false` y reinicia el juego. Para la cama, actualiza a 1.9.3: en `config/somnia-common.toml` pon `minimumFatigueToSleep = 0`, `sleepWithArmor = true`, `fading = false`, `fatigueReplenishRate = 0.0`, `wakeTimeSelectItem = ""`, la ventana de entrada `12542–23460` y la de simulación `validSleepStart`/`validSleepEnd = 24000`. No hace falta ningún datapack.

## ⚠️ Problemas conocidos

- **JEI debe quedarse en 15.74.0.227.** Con `jeasync-mixin 6.2.0` instalado, la build .232 provoca un `VerifyError` al arrancar. No actualices JEI hasta que el mixin se actualice.
- **Resource packs ARR:** el `manifest.json` referencia FreshAnimations, HyperPunchy, Punchy refined, Enchantment Glows, FA+Player e HIDYKs REALM, y el launcher los instala en `resourcepacks/`. Si tu launcher no los descarga por permisos del autor, instálalos a mano.
- **Shaders no incluidos.** Oculus viene instalado, pero no se distribuye ningún shaderpack.
- **`easy_mob_farm` 11.0.0** es la versión soportada.

## ℹ️ Notas

- El libro **no se entrega automáticamente**: sigue saliendo de la misión de inicio.
- Sin cambios de mods: **246 en total**, los mismos 241 de CurseForge y 5 en `overrides/mods` (Clumps, Controlling, Easy Mob Farm, Fabric API, Searchables).
- La versión que muestra la guía sale de `macros.version` en `book.json`, que en esta release es `1.9.3`.

---

Panas RPG v1.9.2 — Cuatro oficios, dragones, cocina y rendimiento

**Fecha de publicación:** 2 de noviembre de 2026
**Estado:** Release

## 🧑‍🌾 Cuatro profesiones de verdad

El pack deja de tener una sola barra de progreso y pasa a tener **cuatro oficios** dentro de Puffish Skills. Se abren con **K**, junto a las pestañas de combate, minería, clase y armas que ya existían.

| Oficio | Cómo sube | Techo |
| --- | --- | --- |
| ⚙️ **Ingeniería** | Fabricar y fundir piezas de Create, y minar menas sin Toque de Seda | Nivel 30 |
| 🍳 **Cocina** | Comer, cocinar y fundir platos de Farmer's Delight, Croptopia, Central Kitchen, Garnished, Nether's Delight, End's Delight y guisos de dragón | Nivel 30 |
| 🏹 **Caza** | Matar mobs; la XP escala con la vida y la XP del objetivo | Nivel 30 |
| 🧭 **Exploración** | Pescar, romper bloques naturales, minar menas y fabricar equipo de viaje | Nivel 30 |

- **1 punto por nivel**, 6 nodos por oficio y curvas de XP pensadas para semanas, no para una tarde.
- **Anti-farm real:** en Caza, 12 muertes en el mismo chunk en 300 segundos dejan de dar XP. Las granjas de zombis no sustituyen a salir al mundo.
- **Sin respec.** Los puntos se quedan donde los pones. Elige el oficio que el grupo necesite y no el que sea más cómodo hoy.
- Las cuatro pestañas nuevas **conviven** con los árboles de otros mods: nada se sobrescribe y el progreso anterior se conserva.

## 🍲 Cuatro cocinas nuevas

La profesión de Cocina ya no vive solo de Farmer's Delight. Se suman cuatro mods verificados uno a uno contra **Create 6.0.8** y **Farmer's Delight 1.3.4**:

| Mod | Versión | Qué aporta |
| --- | --- | --- |
| 🎂 **Create: Central Kitchen** | 1.5.1 | Pasteles, tartas y platos montados con mecánicas de Create. |
| 🥜 **Create: Garnished** | 2.1.7.c | Frutos secos, especias, salsas y comidas exóticas con cultivos propios. |
| 🔥 **Nether's Delight** | 4.0 | Hoglin, strider, guisos y gelatinas del Nether. |
| 🌌 **End's Delight** | 2.6.1 | Carne de dragón, shulker, coro y tés del End. |

- **565 platos y bebidas** en el tag `panas:cocina` (+136 respecto a 1.9.1). Todos dan XP al comerlos, cocinarlos o fundirlos.
- **Cero recetas pisadas:** se compararon las 3.678 rutas `data/` de los cuatro jars contra el resto del pack; ninguna receta comparte ruta.
- **Dependencias limpias:** Forge `[47,48)`, Create 6.0.8 y Farmer's Delight 1.3.4; ningún `modId` duplicado.
- **Hashes verificados:** los cuatro jars se descargaron de su página oficial y se comprobó el SHA1 antes de instalarlos.

## 🐉 FASE XIV — Jinetes de Dragón

Diez misiones cooperativas para el ciclo completo de Saint's Dragons:

- **Encontrar** la especie adecuada en su bioma.
- **Debilitarla** hasta el umbral de agotamiento sin matarla.
- **Domarla** con *Hearty Dragon Meal* y montura.
- **Cepillarla** para escamas y **fabricar** su equipo en el crisol.
- **Criar** con huevos de hembras salvajes y **volar** en formación.

Ninguna misión obliga a matar un dragón: la caza es una decisión, no un paso del tutorial.

## 🏹 Ocho cacerías nuevas en el tablón

El tablón de Bountiful pasa de 43 a **51 contratos**: uno por cada especie de Saint's Dragons, con dificultad y paga acordes a la bestia.

- **Stegonaut** es la entrada: lento, duradero y perfecto para aprender.
- **Ignivorus** es el techo: 450 de vida, aliento de 80 y una última fase que descarga 200 de daño.
- **Nulljaw** no da escama ni huevo, pero su contrato paga bien y su montura es única.

Las recompensas siguen la regla del pack: objeto distintivo del objetivo, entre 1 y 6 diamantes y exactamente 1 manzana dorada.

## 💎 Botín temático en todo el mundo

- **7 tablas nuevas** inyectadas en **334 loot tables** de Dungeons Arise, Cataclysm, YUNG's y Repurposed Structures.
- **4 tablas de tier y 51 funciones de recompensa** reescritas: cada jefe suelta botín acorde a su dificultad y no un premio genérico.
- Los jefes menores dejan de repetir el mismo cofre que un jefe final.
- El botín de estructuras cambia según el tipo de mazmorra y el jefe que la guarda.

## 📖 La guía se pone al día

- **Saint's Dragons pasa de 8 a 13 páginas:** vida, armadura, umbral de doma, comida, hábitat y botín de las ocho especies, más el crisol, los binders y un resumen de qué guardar.
- **"Habilidades y árbol de Skills"** explica la XP exacta de cada oficio, el anti-farm y el ritmo real de subida.
- **Nueva entrada "Descanso y fatiga"** con las cifras de Somnia, los efectos por tramo y cómo desactivarlo.
- **Nueva categoría "Créditos y versión"** con 5 páginas: quién hizo qué, qué versión estás jugando y por qué faltan algunos resource packs. La versión sale de `book.json` y se actualiza sola.
- **"Jefes Vanilla" corregido:** el Wither del pack tiene 500 de vida, embestida de 25 que rompe el escudo 20 segundos, y **no** posee mobs ni usa las fases vanilla. La entrada anterior describía el mod, no la configuración real.

## ☕ Somnia entra en beta

- La fatiga sube unos **2,5 puntos por minuto**; a los 40 minutos estás al máximo.
- Necesitas **20 o más** para dormir y el tiempo corre **×100** mientras duermes.
- Efectos a 70 (náuseas), 80 (lentitud II), 90 (veneno) y 95 (náuseas permanentes hasta dormir).
- **El café ya funciona:** café de Croptopia +10, granos +6, chocolate caliente +8, caramelo de café +5.
- **Es reversible:** `enableFatigue = false` en `config/somnia-common.toml` y desaparece la obligación de dormir sin tocar el resto del mod.

## ⚡ Rendimiento: CPU y RAM bajo control

Esta versión no añade mods de rendimiento nuevos: ajusta los que ya estaban y limpia lo que sobraba.

- **JVM de referencia:** G1GC con pausas objetivo de 100 ms, `G1NewSizePercent=20`, `G1HeapRegionSize=8M` y heap fijo de **4096–8064 MB**. Menos picos de GC y menos basura. Si tu launcher no importa el `instance.cfg`, copia estos valores a mano.
- **`Ixeris`:** desactivado el busy-wait del limitador de FPS. El cliente deja de quemar un núcleo cuando va sobrado de frames.
- **`forge-client`:** el terreno se prepara fuera del hilo principal; bajan los tirones al cargar chunks.
- **`Smooth Boot`:** 10 hilos de carga principal en vez de 15. El arranque sigue rápido sin saturar el CPU.
- **`Embeddium`:** 3 chunks de render-ahead en vez de 4. Un frame más de latencia a cambio de menos CPU y menos stutter.
- **`AllTheLeaks` + `structure_layout_optimizer`:** deduplicación activada en recetas, ingredientes y listas de plantillas de estructura.
- **`servercore`:** caché de chunks ticking y lookups de bioma rápidos. Los mobs pueden aparecer unos bloques al otro lado de una frontera de bioma; no afecta a estructuras.
- **`config/jei` limpio:** se quitaron 11 backups, las carpetas `world/` y `server/` y 1,5 MB de caché de búsqueda. JEI puede regenerar 1–2 backups al arrancar; son inofensivos.

## 🔧 Correcciones

- **Calendario cooperativo:** el anuncio de nuevo día muestra el día real y recuerda que el tablón de caza sigue abierto.
- **Recompensas de jefe:** eliminado `panas_boss_rews.json`, un archivo huérfano que ya no se cargaba, y consolidado todo en `panas_boss_rews_v2.json`.
- **Libro:** los 34 JSON validan sin errores; los renders siguen siendo nativos de Patchouli, sin capturas.

## ⚠️ Problemas conocidos

- **JEI debe quedarse en 15.74.0.227.** Con `jeasync-mixin 6.2.0` instalado, la build .232 provoca un `VerifyError` al arrancar. No actualices JEI hasta que el mixin se actualice.
- **Resource packs ARR:** el `manifest.json` referencia FreshAnimations, HyperPunchy, Punchy refined, Enchantment Glows, FA+Player e HIDYKs REALM, y el launcher los instala en `resourcepacks/`. Si tu launcher no los descarga por permisos del autor, instálalos a mano.
- **Shaders no incluidos.** Oculus viene instalado, pero no se distribuye ningún shaderpack.
- **`easy_mob_farm` 11.0.0** es la versión soportada; el ZIP 1.9.1 traía 10.10.0.

## 📦 Instalación

- Actualiza normalmente desde CurseForge o Prism Launcher.
- No hace falta mundo nuevo: las profesiones, la Fase XIV y el botín se cargan en mundos existentes.
- Si vienes de 1.9.1, revisa que JEI siga en .227 antes de lanzar.
- Los cuatro mods de cocina (**Central Kitchen 1.5.1, Garnished 2.1.7.c, Nether's Delight 4.0, End's Delight 2.6.1**) ya vienen incluidos en `mods/`.
- El export lleva `config/jei` limpio. Si arrastras una config vieja, borra los `.bak.1` y `search_string_cache.json.gz`.
- **Instalación manual:** en el release de GitHub está `Panas.RPG-1.9.2-Mods.Completo.rar` con todos los mods, configs, quests y guía; descomprime su contenido en `.minecraft`.

## ℹ️ Notas

- El libro **no se entrega automáticamente**: sigue saliendo de la misión de inicio.
- La XP de las profesiones es **personal**, no se comparte con el equipo.
- Las misiones de dragones no exigen matar ninguna especie.
- La versión que muestra la guía sale de `macros.version` en `book.json`; si el pack sube de versión, cambia esa línea y todas las páginas se actualizan.

---

Panas RPG v1.9.1 — La Guía de Supervivencia se vuelve ilustrada

**Fecha de publicación:** 28 de octubre de 2026
**Estado:** Release

## 📖 La Guía de Supervivencia, renovada

La guía deja de ser un muro de texto: cada tema importante tiene una imagen del propio mod o de vanilla, y las explicaciones se redujeron a lo esencial.

- **49 páginas nuevas con render nativo** de Patchouli (de 49 a 98 en total): ítems con `spotlight` y criaturas con `entity`. Sin capturas estáticas ni texturas copiadas de otros packs.
- **177 páginas** en total, repartidas en las mismas 25 entradas y 5 categorías.
- Se conserva el progreso de lectura y los marcadores: no hay que empezar el libro de nuevo.

### Secciones reescritas

- **Mochilas, cofres y tuberías:** Sophisticated Backpacks, Sophisticated Storage y Pretty Pipes, con las mejoras que de verdad se usan.
- **Create y trenes:** de la rueda hidráulica al horario del tren, en 4 pasos, más señales y Steam 'n' Rails.
- **Atlas de exploración:** biomas, estructuras, Lootr y waystones.
- **Magia:** Ars Nouveau y RPG Series por separado, con lo básico de glifos, Source y escuelas.
- **Clases, stats y progresión:** las cuatro familias, XP compartida y atributos clave.
- **Jefes, muerte y tumbas:** preparación, Corail Tombstone y contratos de Bountiful.
- **Expediciones y cooperación:** calendario del mundo, equipo, Ping Wheel y ajustes de FPS.
- **Habilidades y árbol de Skills:** pestañas, puntos, anti-farm y respec.
- **La cocina de Panas:** Farmer's Delight, Croptopia, Cultural Delights y pesca.
- **Controles Esenciales:** teclas reales, teclas sin asignar y conflictos.

## 🐉 Más jefes, con imagen

La entrada **"Otros Jefes del Pack"** pasó de 4 a 17 páginas e incluye 12 criaturas renderizadas:

- **Ars Nouveau:** Wilden Chimera.
- **Friends & Foes:** Wildfire.
- **Cataclysm:** Amethyst Crab, Kobolediator y Wadjet, más la lista de mini-jefes.
- **Legendary Monsters:** Ancient Guardian, Frostbitten Golem, Lava Eater y Withered Abomination.
- **Saint's Dragons:** Atroxiia y Cindervane, con los dragones domesticables.
- **Deep Dark Regrowth:** Stalker y su fauna.
- **Wither Reincarnated:** nota de que no añade jefe, sino que rehace el Wither vanilla.

## ⌨️ Controles: teclas verificadas

Revisamos tecla por tecla contra los archivos de cada mod:

- **Combat Roll = Caps Lock.** Es la esquiva: cancela caídas y saca de un golpe.
- **Skill Tree = K**, **mochila = B**, **Ping Wheel = Mouse 5**, **Wall Jump = Shift**.
- **G** es la habilidad especial de **Alex's Caves**, no de RPG Series.
- **Simply Swords** (mainhand/offhand) y **Spell Engine** (hotbar 1-9) vienen **sin asignar**.
- Conflictos documentados: **C, X, V, G, R, B y T**.

## ⚠️ Notas

- Actualización centrada en la guía: no cambia misiones, botín, calendario ni economías.
- Si un render no carga al entrar, pulsa **F3+T** o reinicia el cliente.
- El libro se ve bien en mundos ya creados; no hace falta empezar de cero.

## 📦 Instalación

- Actualiza normalmente desde CurseForge o Prism Launcher.
- Si usas Prism y los packs ARR no aparecen, instálalos manualmente en `resourcepacks/`.

---

Panas RPG v1.9 — Crónicas de los Panas y nuevas expediciones

**Fecha de publicación:** 27 de octubre de 2026
**Estado:** Publicado

## 🆕 Novedades

### 🧭 FASE IX — Crónicas de los Panas
- Seis misiones cooperativas: **Mapa de la expedición**, **Provisiones para los panas**, **Siete amaneceres**, **Dos semanas en equipo**, **Un mes de aventuras** y **Ruta de regreso**.
- Hitos compartidos al alcanzar 7, 14 y 30 días de Minecraft.

### 🚂 FASE X — Ingeniería en movimiento
- Un recorrido de Create por vías, estaciones, paneles de destino, horarios y viajes largos en tren.
- Las misiones acompañan al grupo desde la construcción de la infraestructura hasta completar un viaje ferroviario.

### 🍲 FASE XI — La despensa de los Panas
- Objetivos de agricultura, pesca y cocina con Farmer’s Delight y Aquaculture.
- Prepara ingredientes y comidas para sostener las expediciones del equipo.

### 🛡️ FASE XII — Maestría de clase
- Metas de equipo para las cuatro clases: arquero, paladín, pícaro y mago.
- Incluye un objetivo para invertir un punto en el árbol de habilidades. Como el mod del árbol no expone ese avance a FTB Quests, el jugador marca esa tarea manualmente después de gastar el punto.

### 🗺️ FASE XIII — Atlas de tierras salvajes
- Explora biomas de Regions Unexplored y Terralith con objetivos de viaje y descubrimiento.
- El reto final de explorar 71 biomas es opcional; algunas ubicaciones pueden requerir recorrer terreno nuevo.

### 🕰️ Calendario cooperativo del mundo
- Paxi anuncia los nuevos días del mundo y registra hitos compartidos de 7, 14 y 30 días para las misiones de la Fase IX.
- En mundos existentes, el calendario continúa desde el día actual del mundo.

### 📍 Ping Wheel
- Marca temporalmente lugares y criaturas para coordinar al grupo durante la exploración y el combate.
- Tecla predeterminada: **Mouse 5**. Puedes cambiarla en **Options → Controls**.
- Mantén **Tab** para mostrar información de los jugadores asociados a las marcas.

### 📖 Guía de Supervivencia
- Nueva entrada **“Expediciones y Cooperación”**, con consejos sobre el calendario, preparación, rutas, Ping Wheel y ajustes gráficos opcionales.
- La guía acompaña la progresión ampliada de las misiones.

## 🧹 Limpieza de mensajes al entrar
- Se desactivó el anuncio automático de JourneyMap en el chat al entrar al mundo.
- Se añadió un mensaje personalizado de bienvenida de Panas RPG: **“¡Bienvenido a Panas RPG! Prepárate para explorar, construir y sobrevivir en equipo. Abre FTB Quests y tu guía Patchouli para comenzar. ¡Juega con tus panas!”**

## 🪙 Economía cooperativa entre panas
- Las monedas nuevas proceden de las recompensas de FTB Quests y de los contratos de caza Bountiful. Se desactivan la acuñación, los botines de criaturas y cofres, y las recompensas y sustituciones de botín de eventos estacionales.
- Los contratos de caza entregan el objeto distintivo del jefe cazado, entre 1 y 6 diamantes y exactamente 1 manzana dorada; la paga monetaria escala con la dificultad: 4 monedas de hierro (rara), 1 de oro (épica) y 1 de esmeralda (legendaria). Los discos de Cataclysm son recuerdos coleccionables y evitan sumar equipo de alto poder a esos jefes.
- Los jugadores pueden montar tiendas de Lightman's Currency para vender artículos y comprar lo que ofrecen los demás con las monedas obtenidas en las misiones.
- No hace falta un servidor dedicado: el comercio funciona en el mundo compartido mientras el anfitrión lo tenga abierto.
- Las monedas que ya existían en un mundo se conservan; el cambio limita las nuevas emisiones una vez cargada la configuración.

## 📦 Instalación
- Actualiza normalmente desde CurseForge o Prism Launcher; Paxi carga el calendario, el mensaje de bienvenida y las funciones de recompensa de caza desde los datapacks incluidos.
- En un servidor dedicado, instala Paxi y conserva los datapacks de Panas RPG en la configuración del servidor.
- Ping Wheel debe estar instalado en el servidor y en cada cliente que vaya a usar las marcas.
- Para las misiones de biomas, explora el mundo; no hace falta crear un mundo nuevo.

## ℹ️ Notas
- Los hitos cuentan días de Minecraft, no días reales.
- La fase de árbol de habilidades se confirma manualmente en FTB Quests.
- Las misiones de las fases nuevas están agrupadas como desplegables, siguiendo el diseño de las fases anteriores.


Panas RPG v1.8.2 - Libro: contenido nuevo, fix, limpieza y rebalanceo de botin

Release Date: October 16, 2026
Status: Release • Testers needed • Feedback appreciated

🆕 What's New
📖 Guia de Supervivencia — contenido nuevo
- Nueva entrada "Habilidades y Arbol de Skills": como abrir el arbol (tecla K), las 4 pestanas (Combat, Mining, Class Skills, Weapon Skills), como se ganan puntos y experiencia, y el listado de clases y especializaciones de arma.

⚖️ Botin de mazmorras rebalanceado (nuevo datapack global panas-loot)
- Diamantes: peso reducido a un tercio (minimo 1) y cantidad maxima de 1 por tirada.
- Encantamientos: nivel maximo III (antes llegaban a V+). Los rolls de mayor nivel se recortan y los aleatorios usan un cap menor.
- Encantamientos solo en hierro: el equipo encantado de diamante/oro/netherite se convierte a su version de hierro; el de cuero/malla ya no sale encantado.
- Manzana encantada: mucho mas rara (peso 1 y probabilidad de tirada 0.3).
- Se sobreescriben las 131 loot tables de Dungeons Arise. Aplica a cofres nuevos o sin abrir de cualquier mundo.

🔧 Fixes
- Datapacks ahora se cargan correctamente: se agrego Paxi para cargar datapacks globales desde config/paxi/datapacks/. El datapack panas-loot estaba en una ruta invalida y no aplicaba; restaurado a su ubicacion correcta.
- Limpieza de datapacks invalidos: eliminada la carpeta inerte datapacks/data (sin pack.mcmeta, no aplicaba).
- El libro "Cronicas de Panas RPG" no se abria (el item decia "Invalid book: patchouli:guia_supervivencia"): estaba en la carpeta equivocada. Restaurado a su ruta correcta (patchouli_books/ en la raiz del juego) y eliminada la copia inutil en config/patchouli_books/.
- No hay que recrear el mundo: basta con actualizar y recargar.

🧹 Limpieza de UI y mensajes automaticos
- Icono de libro (Field Guide) desactivado: ya no aparece en el menu de pausa ni en el inventario (config/fieldguide-client.json).
- Mensajes de entrada desactivados: SecurityCraft (sayThanksMessage=false), Streams Reflowing (welcomeMessage=false) y Cataclysm (showLoginNotice=false).
- JourneyMap: desactivado el anuncio automatico del mod en el chat (announceMod=false).
- Terralith: desactivado el mensaje de bienvenida mediante el datapack terralith-no-toast (sin modificar el jar).

⚙️ Changed
- Texto del libro: reemplazado el color amarillo por naranja (#FF8000) para mejor visibilidad.

📦 Installation
- Los cambios del libro se aplican solos, sin pasos manuales.
- Paxi va incluido en el modpack (mod nuevo) y el datapack vive en config/paxi/datapacks/. No requiere pasos manuales.
- Si el libro no abre tras actualizar, recarga con F3+T o reinicia el cliente.

⚠️ Known Issues
- El rebalanceo de botin solo afecta cofres nuevos o sin abrir. Los cofres ya abiertos conservan su contenido anterior.

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
