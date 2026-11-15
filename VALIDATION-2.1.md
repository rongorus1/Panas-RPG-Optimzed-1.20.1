# Validación preliminar de Panas RPG 2.1

**Fecha:** 15/11/2026. **Estado:** artefactos locales; sin publicación ni instalación limpia comprobada.

## Artefactos

- CurseForge ZIP limpio: `C:\Users\User\Downloads\Panas RPG 2.1.zip` — SHA256 `6ebf5fb0ed6f0d94c9d25378b04d67a029b259401fedddd5da4c8c12dc221421`.
- RAR manual: `D:\mine\modpack\modpack all mod\Panas.RPG.2.1-Mods.Completo.rar` — SHA256 `B22141812381B7CECC725DDE877BE5A1D625A2CAEA55D0052FE623BA663F93EC` (984.715.756 bytes).
- Variante para GitHub: `D:\mine\modpack\modpack all mod\Panas.RPG.2.1-GitHub-Manual.rar` — SHA256 `3C96A5E03F23674F000B9BA6D81B6D557299F76EE63B1B1F16DD1DAB74BB3760`. Contiene 287 JAR y `INSTALACION-MANUAL-2.1.md`; omite JourneyMap, 3D Skin Layers y los 14 resource packs físicos por restricciones o permisos de redistribución no comprobados. Prueba UnRAR: «Todo correcto».
- Respaldo anterior a la limpieza de ambos archivos: `D:\mine\modpack\respaldos\release-2.1-clean-20261115\`.

## Comparación estructural

- ZIP íntegro: prueba CRC correcta; `manifest.json` declara Minecraft 1.20.1, Forge 47.4.10 y versión 2.1.
- Manifest: 288 proyectos, de los cuales 282 aparecen como mods en `modlist.html`; 7 JAR viajan en `overrides/mods`. 282 + 7 = 289 JAR, igual que la instancia. Los seis proyectos restantes requieren instalación limpia para confirmar su resolución como recursos.
- `tools/audit_pack.py` contra ZIP limpio e instancia: **0 FAIL, 0 WARN**. Los 1.355 archivos de overrides retenidos coinciden en SHA256 con la instancia; 14 capítulos FTB, 701 IDs declarados, 80 dependencias revisadas, 6 datapacks Paxi, un libro Patchouli con 6 categorías y 29 entradas.
- Se retiraron únicamente 52 respaldos/vistas previas de FancyMenu del ZIP (1.409 → 1.357 entradas); `manifest.json`, `options.txt` y los capítulos conservan el contenido. Los ajustes gráficos y de teclas no cambiaron. Los originales están en el respaldo indicado.
- El RAR se preparó desde `overrides/` más los JAR de la instancia y los seis resource packs ausentes físicamente del ZIP; excluye los 52 archivos de desarrollo. Por petición de Juan se retiró `skinlayers3d-forge-1.11.4-mc1.20.1.jar` **solo del RAR**. UnRAR confirmó «Todo correcto»: **288 JAR**, 14 resource packs y 14 capítulos FTB; también contiene libro, Paxi y `options.txt`.

## Pendientes antes de distribución

- El ZIP incluye `options.txt` personal: Gráficos Rápidos, render 8, simulación 6, entidades 0,75; Better Looting en H y JourneyMap «seguir jugador» sin tecla. Están seleccionados simultáneamente `panas-hojas.zip` y `panas-hojas-hd.zip`. Decidir y comprobar el perfil predeterminado con la guía de hojas antes de exportar una versión definitiva.
- Cuatro resource packs seleccionados no están físicamente en `overrides/resourcepacks`: Enchantment Glows, HyperPunchy, Punchy refined y FreshAnimations. FreshAnimations aparece entre los proyectos del manifest; verificar los demás en una instalación limpia. El RAR manual sí contiene los 14 archivos locales de resourcepacks.
- Cargar las 187 misiones en juego y comprobar libro, datapacks, recetas, UI y multijugador. La revisión estática no demuestra funcionamiento en partida.
- El RAR privado omite 3D Skin Layers por la restricción de su autor. El ZIP de CurseForge conserva `Skin Layers 3D (by tr7zw)` como proyecto 521480 en `modlist.html`. La variante GitHub omite además JourneyMap y resource packs de terceros; las instrucciones remiten a sus fuentes oficiales. Antes de llamar «completa» a la instalación manual, deben descargarse esos componentes por separado.

Fuentes: export ZIP 2.1, instancia principal, RAR 2.0.0, `REGISTRO-2.0.0.md`, [licencia/README de 3D Skin Layers](https://github.com/tr7zw/3d-skin-layers).
