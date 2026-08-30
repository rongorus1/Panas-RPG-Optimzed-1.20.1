# Panas RPG - Guía de Rendimiento
**137 mods | 1.20.1 Forge 47.4.10 | Optimizado para 8GB y laptops**

> Panas RPG une ingeniería Create, dungeons y cocina en un mundo vivo. Esta guía reúne las mejores técnicas de optimización probadas en packs pesados (inspiradas en los packs más descargados) para que juegues fluido incluso en PC modesta.

---

## Requisitos

* **Mínimo (8GB RAM total, integrada):** Asigna 4GB a Minecraft, todo en LOW, sin shaders. Esperado 25-45 FPS. Cierra Chrome/Discord.
* **Recomendado (8GB + GTX 1650 / RTX 3050):** Asigna 5-6GB, medio, 45-75 FPS.
* **Óptimo (16GB + dedicada):** Asigna 6-8GB, 75-130 FPS con shaders ligeros.
* **No recomendado:** Asignar 8GB en sistema de 8GB (dejas 0 a Windows y se congela).

---

## 1. Optimiza tu PC antes de jugar

**RAM y sistema:**
- En PrismLauncher -> Panas RPG -> Ajustes -> Memoria: `Min 2048 / Max 4096 (8GB) o 6144 (16GB)`. Nunca Max = RAM total.
- Cierra todo lo que use RAM/CPU en segundo plano. En laptop, usa `Alto rendimiento` enchufada y base con ventilación.
- Activa `Modo juego` en Windows y desactiva `Fondo de pantalla con presentación`.

**Drivers y Java:**
- Actualiza Nvidia/AMD con GeForce Experience/Adrenalin (driver 616.56+). En `Nvidia Control Panel -> Manage 3D`: `Power management: Optimal Power`, `Max Frame Rate: 75`, `Shader Cache: 10GB`.
- Usa el `Java 17.0.15 Microsoft` que trae Prism. Añade en `JVM Args`: `-XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200`

**Tip de packs top:** Los packs más fluidos usan `G1GC` y `ParallelRefProc` para evitar tirones al explorar. Ya lo tienes configurado en esta guía.

---

## 2. Ajustes de Minecraft que más FPS dan

En `Opciones -> Video`:

- **Render Distance: 14 -> 8 (integrada) / 10 (dedicada)** - Cada chunk con Terralith cuesta 5 FPS. Es el ajuste #1.
- **Simulation Distance: 13 -> 6** - Menos mobs activos = menos CPU.
- **Graphics: Fancy -> Fast** si tienes <40 FPS. `Smooth Lighting OFF`, `Biome Blend OFF`, `Mipmap 2`.
- **Max FPS: 150 -> 60** + `VSync ON` en Nvidia. Con 150 tu RTX se pone al 100% y los ventiladores a tope (como te pasó con GPUTape).
- **Nubes: OFF, Partículas: Minimal, Sombras de entidades: OFF**

En `Opciones -> Video -> Embeddium`:
- `Chunk Builder Threads: 0 (auto)`
- `Use Block Face Culling: ON` y `Use Fog Occlusion: ON` - Ganancia de 15 FPS en bosques de Regions Unexplored (los tenías OFF).
- `Leaves Quality: FAST`
- `Animate Only Visible Textures: ON`

En `Opciones -> Video -> Shaders (Oculus)`:
- **Integrada: OFF siempre.** Dedicada: usa `Sildur's Vibrant Lite` no `High-MB`.

---

## 3. Mods que ya te ayudan (no los quites)

Tu pack ya incluye lo que usan los packs más optimizados del mercado:

- **Embeddium + Oculus** (port de Sodium/Iris) - base de FPS
- **Canary** (port de Lithium) + **FerriteCore** + **ModernFix** - RAM y ticks
- **Noisium + Saturn + Clumps + AI Improvements + Smooth Boot** - worldgen y mobs (añadidos en V1.2)
- **BadOptimizations + EntityCulling + Fast Noise (zfastnoise/gnetum/ixeris)** - micro-optimizaciones que suman 10-20 FPS

Mantener `ModernFix` con `dynamic_resources=true` y `deduplicate_location=true` te ahorra 50-80MB y carga 2x más rápido con 137 mods.

---

## 4. Dentro del juego

- No dejes el `JourneyMap` en pantalla completa mientras corres.
- Tapa tus fábricas `Create` con bloques cuando no las uses (menos `belts` visibles).
- Baja `Entity Distance` a 75% si hay muchos `Alex's Mobs` juntos.
- Reinicia el mundo cada 2h si tienes 8GB (libera RAM).

---

## 5. Controles clave

| Tecla | Acción | Mod |
|---|---|---|
| `B` | Abrir mochila | Sophisticated Backpacks |
| `G` | Abrir Curios (accesorios) | Curios API |
| `J` | Mapa completo | JourneyMap |
| `K` | Activar/desactivar shaders | Oculus/Iris |
| `O` | Selección de shaderpacks | Oculus |
| `R` | Recargar shaders | Oculus |
| `U` / `R` | Ver usos/receta | JEI |
| `Z` | Zoom | Just Zoom |

> Cambia todo en `Opciones -> Controles`. Si dos mods usan la misma tecla, reasigna.

## 6. Solución de problemas

| Síntoma | Causa probable | Solución rápida |
|---|---|---|
| `OutOfMemory` al explorar | Asignaste 8GB en sistema de 8GB | Baja a 4GB y cierra Chrome |
| Tirones cada 10s | `Render 14` + Terralith | Baja a 8 y `Simulation 6` |
| GPU 100% ventiladores a tope | `maxFps 150 + GPUTape` | Quita GPUTape, pon `maxFps 60` |
| Mundo tarda 3 min en cargar | `ModernFix` sin `dynamic_resources` | Activa `dynamic_resources=true` en `modernfix-mixins.properties` |

---

*Creado para Panas RPG - 1.20.1 Forge. Inspirado en las mejores prácticas de packs optimizados destacados. ¿Dudas? Discord del proyecto.*
