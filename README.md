# Oktana · Agentforce QuickStarts — Presentación interactiva (v42)

Separación del archivo `oktana_agentforce_interactive_presentation_v42.html`
en HTML y CSS independientes.

## Archivos

| Archivo | Contenido |
|---|---|
| `index.html` | Estructura y contenido de la presentación (slides, textos, imágenes, script de navegación) |
| `styles.css` | Todo el CSS que estaba embebido en el `<head>` (973 líneas / ~44,5 KB) |
| `README.md` | Este documento |

## Novedad de esta versión

Los 5 bloques `<style>` y su contenido son **idénticos, carácter a carácter, a los de v41**.
Es decir, los cambios de v42 fueron exclusivamente en el **contenido/HTML** (textos, slides,
imágenes, etc.), no en el CSS. Por eso `styles.css` en esta entrega es igual al de la versión
anterior.

## Cómo se hizo la separación

1. Se localizaron los 5 bloques `<style>…</style>` (pegados uno a otro, sin HTML entre ellos),
   con el mismo patrón de las versiones v38 y v41.
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

Quedan además los mismos ~15 estilos inline sueltos (`style="margin-top:12px"`,
`style="color:#4c8dff"`, etc.), sin cambios respecto a versiones anteriores — no los toqué
para no arriesgar cambios visuales no solicitados. Avísame si quieres que los pase también a
clases dentro de `styles.css`.

## Uso

Mantén `index.html` y `styles.css` en la **misma carpeta** y abre `index.html` en el
navegador; el `<link>` los conecta automáticamente.
