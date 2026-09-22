# DevDays Copilot Template (Slidev)

Template dark estilo **GitHub Copilot** (extraído de las decks oficiales DevDays; ver
`../design.md` para el análisis completo).

## Usar

```bash
npm install
npm run dev        # editor + preview en http://localhost:3030
npm run build      # export SPA estática a dist/
npm run export     # PDF (requiere playwright-chromium: npx playwright install chromium)
```

## Contenido

| Archivo | Qué es |
|---|---|
| `slides.md` | Deck de ejemplo con los 6 layouts |
| `styles/index.css` | Tokens (§6.1 de design.md) + `@font-face` Mona Sans |
| `layouts/cover.vue` | Portada con degradado IA |
| `layouts/statement.vue` | Large statement (frase hero 80 px) |
| `layouts/feature.vue` | Title and image stacked (`image:` en frontmatter de la slide) |
| `layouts/roadmap.vue` | Roadmap con tarjetas numeradas (pasos `::second::`… y reveal escalonado) |
| `layouts/section.vue` | Separador de sección |
| `layouts/end.vue` | Thank you |
| `public/fonts/` | Mona Sans + Mona Sans Mono variables (oficiales, SIL OFL) |

## Recetas rápidas

```markdown
---
layout: feature
image: /img/mi-capture-4k.png
---
# Título
```

- Acentos: `<span class="accent-green">` · `accent-purple` · `accent-lime` · `muted`
- Degradados: `grad-ai` (morado→azul→cian) · `grad-green` (verde→lima)
- Tarjetas: `<div class="card">…</div>` · chip: `<span class="chip">NEW</span>`
- Halos de fondo: añade clases `halo` / `halo-green` al contenedor de la slide

## Cambiar el acento de una slide

```markdown
---
layout: statement
style: '--green: #B870FF'   # reasigna tokens por slide
---
```

## Animaciones / clicks (Slidev v51)

⚠️ En v51 **ya no existe** el separador de clicks `--` (lo eliminó la reescritura de
v0.48+). Usa:

- `<v-click>` / `<v-clicks>` / `<v-after>` en el markdown o dentro de los layouts
- Marcadores de slot `::nombre::` en su propia línea (abren `<template v-slot:nombre>`;
  el siguiente marcador o el fin de slide los cierra). Ejemplo en `slides.md`:
  portada con `::second::` y roadmap con `::second::` / `::third::` / `::fourth::`
- `clicks:` en frontmatter para reserves; props `at="'+1'"` para offsets

## Nota de marca

Mona Sans es de GitHub (SIL OFL): úsala libremente. Los logos/capturas de GitHub **no**
— sustitúyelos por material propio si el contexto no es GitHub.
