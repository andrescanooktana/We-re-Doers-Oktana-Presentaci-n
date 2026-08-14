# Oktana · Agentforce QuickStarts — Presentación interactiva (v38)

Separación del archivo `oktana_agentforce_interactive_presentation_v38.html`
en HTML y CSS independientes.

## Archivos

| Archivo | Contenido |
|---|---|
| `index.html` | Estructura y contenido de la presentación (slides, textos, imágenes, script de navegación) |
| `styles.css` | Todo el CSS que estaba embebido en el `<head>` (946 líneas / ~43 KB) |
| `README.md` | Este documento |

## Diferencia clave respecto a v30

Esta versión **no traía un único bloque `<style>`**, sino **5 bloques `<style>` consecutivos**
en el `<head>`: el bloque principal más cuatro parches incrementales con comentarios de
versión (`/* v34 — Slide 2 grouped product logos */`, `v35`, `v36`, `v37`), cada uno agregando
o ajustando reglas sobre slides específicos.

## Cómo se hizo la separación

1. Se localizaron los 5 bloques `<style>…</style>` (iban uno pegado al otro, sin contenido
   HTML entre ellos).
2. Se concatenó el contenido de los 5 bloques, en el mismo orden en que aparecían, en un solo
   `styles.css` — conservando los comentarios `/* vXX — ... */` que marcan cada parche, para
   que quede claro qué regla pertenece a qué iteración.
3. En `index.html` toda la región (desde el primer `<style>` hasta el último `</style>`) se
   reemplazó por una única línea:
   ```html
   <link rel="stylesheet" href="styles.css"/>
   ```
4. Se verificó que:
   - Todo el contenido antes del primer `<style>` y después del último `</style>` es
     **idéntico carácter a carácter** al original.
   - Las llaves `{ }` del CSS combinado están balanceadas (361 aperturas / 361 cierres).
   - Las etiquetas `<html>`, `<head>`, `<body>` y `<script>` cierran correctamente (1/1 cada una).
   - No quedó ningún `<style>` suelto en el HTML resultante.

No se tocó el `<script>` de navegación ni ninguna otra parte de la lógica.

## Por qué `index.html` sigue pesando ~8 MB

Igual que en la versión anterior, el peso viene de **imágenes incrustadas en base64**
directamente en el HTML (logos de clientes, ilustraciones de agentes, etc.), no del CSS.
Esas imágenes se dejaron intactas donde estaban.

Quedan además ~15 estilos inline sueltos (`style="margin-top:12px"`, `style="color:#4c8dff"`,
etc.) — son ajustes puntuales de espaciado/color en elementos específicos. No los toqué para
no arriesgar cambios visuales no solicitados; si quieres que los pase también a clases dentro
de `styles.css`, dímelo y lo hago en una siguiente pasada.

## Uso

Mantén `index.html` y `styles.css` en la **misma carpeta** y abre `index.html` en el
navegador; el `<link>` los conecta automáticamente.
