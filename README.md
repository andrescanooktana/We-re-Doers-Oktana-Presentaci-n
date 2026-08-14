# Oktana · Agentforce QuickStarts — Presentación interactiva (v41)

Separación del archivo `oktana_agentforce_interactive_presentation_v41.html`
en HTML y CSS independientes.

## Archivos

| Archivo | Contenido |
|---|---|
| `index.html` | Estructura y contenido de la presentación (slides, textos, imágenes, script de navegación) |
| `styles.css` | Todo el CSS que estaba embebido en el `<head>` (973 líneas / ~44,5 KB) |
| `README.md` | Este documento |

## Estructura del CSS en esta versión

Igual que en v38, el CSS no venía en un único bloque `<style>` sino en **5 bloques
consecutivos** dentro del `<head>`. La diferencia es que aquí el segundo bloque acumula
muchos más parches versionados que en v38 (comentarios `/* v5 refinements */`,
`v6`, `v8`, `v9`, `v10`, `v11`, `v12`, `v13`, `v16`, `v21`, `v23`, `v25`, `v26`, `v30`,
además de los ya vistos `v34`–`v37`). Todos esos comentarios se conservaron en el
`styles.css` final, en el mismo orden en que aparecían, para que sigas viendo el historial
de qué slide tocó cada iteración.

## Cómo se hizo la separación

1. Se localizaron los 5 bloques `<style>…</style>` (pegados uno a otro, sin HTML entre ellos).
2. Se concatenó el contenido de los 5 bloques, en orden, en un solo `styles.css`.
3. En `index.html` toda la región (desde el primer `<style>` hasta el último `</style>`) se
   reemplazó por una única línea:
   ```html
   <link rel="stylesheet" href="styles.css"/>
   ```
4. Se verificó que:
   - Todo el contenido antes del primer `<style>` y después del último `</style>` es
     **idéntico carácter a carácter** al original.
   - Las llaves `{ }` del CSS combinado están balanceadas (370 aperturas / 370 cierres).
   - Las etiquetas `<html>`, `<head>`, `<body>` y `<script>` cierran correctamente (1/1 cada una).
   - No quedó ningún `<style>` suelto en el HTML resultante.

No se tocó el `<script>` de navegación ni ninguna otra parte de la lógica.

## Por qué `index.html` sigue pesando ~8 MB

Igual que en las versiones anteriores, el peso viene de **imágenes incrustadas en base64**
directamente en el HTML (logos de clientes, ilustraciones de agentes, etc.), no del CSS.
Esas imágenes se dejaron intactas donde estaban.

Quedan además ~15 estilos inline sueltos (`style="margin-top:12px"`, `style="color:#4c8dff"`,
etc.), sin cambios respecto a v38 — no los toqué para no arriesgar cambios visuales no
solicitados. Avísame si quieres que los pase también a clases dentro de `styles.css`.

## Uso

Mantén `index.html` y `styles.css` en la **misma carpeta** y abre `index.html` en el
navegador; el `<link>` los conecta automáticamente.
