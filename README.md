# Oktana · Agentforce QuickStarts — Presentación interactiva

Separación del archivo original `oktana_agentforce_interactive_presentation_v30.html`
en HTML y CSS independientes.

## Archivos

| Archivo | Contenido |
|---|---|
| `index.html` | Estructura y contenido de la presentación (slides, textos, imágenes, script de navegación) |
| `styles.css` | Todo el CSS que estaba dentro del bloque `<style>` del `<head>` (735 líneas / ~36 KB) |
| `README.md` | Este documento |

## Cómo se hizo la separación

1. Se localizó el bloque `<style>…</style>` original (líneas 9 a 745 del archivo fuente) y se
   volcó tal cual, sin modificar ni una regla, a `styles.css`.
2. En `index.html` ese bloque se reemplazó por una única línea:
   ```html
   <link rel="stylesheet" href="styles.css"/>
   ```
3. Se verificó que:
   - El resto del documento (desde `</head>` hasta `</html>`) es **byte a byte idéntico** al original.
   - Las llaves `{ }` del CSS extraído están balanceadas (319 aperturas / 319 cierres).
   - Las etiquetas `<html>`, `<head>`, `<body>` y `<script>` siguen balanceadas 1 apertura / 1 cierre.

No se tocó el `<script>` de navegación entre slides ni ninguna otra parte de la lógica.

## Por qué `index.html` sigue pesando ~8 MB

El CSS extraído es liviano (36 KB). El peso real del archivo viene de **imágenes incrustadas
en base64** directamente en el HTML (logos de clientes como Total360, ARIA, Sony Interactive
Entertainment, 211 San Diego, el logo oficial de Oktana, e ilustraciones de los agentes tipo
SDR Agent, etc.). Esas imágenes no son CSS, así que se dejaron donde estaban, dentro del HTML,
tal como en el original.

Si en algún momento quieres además:
- Extraer esas imágenes a archivos `.png`/`.svg` separados (para aligerar aún más el HTML), o
- Convertir los ~19 estilos inline (`style="margin-top:12px"`, etc.) que quedan sueltos en el
  HTML en clases dentro de `styles.css`,

dímelo y lo hago en una siguiente pasada — no lo hice ahora para no arriesgar cambios visuales
no solicitados.

## Uso

Basta con mantener `index.html` y `styles.css` en la **misma carpeta** y abrir `index.html`
en el navegador; el `<link>` los conecta automáticamente.
