---
theme: seriph
title: Copilot DevDays Template
info: |
  Template dark estilo GitHub Copilot (verde #5EEC83, morado #B870FF, Mona Sans).
class: text-center
drawings:
  persist: false
transition: slide-left
mdit:
  plugins:
    footnotes: true
    taskLists: true
---

# Copilot DevDays Template

Tema **dark** estilo GitHub Copilot para Slidev · 16:9 · Mona Sans

<span class="kbd">usa `←`/`→` para navegar · `o` para overview · `f` fullscreen</span>

---
layout: cover
---

# Title and image stacked

Layout de portada con degradado IA

::second::
## Una idea por slide

Mucho aire, fondo negro, un solo acento.

---
layout: statement
---

# Large <span class="grad-green">statement</span>

---
layout: feature
image: /img/demo-shot.png
---

# Title & Content

Captura de producto a sangre sobre negro (aquí `image:` apunta a un asset propio;
sustitúyelo por tus screenshots 4K).

- Acento **verde** por defecto
- Texto secundario en `--text-muted`
- Código en Mona Sans Mono

```ts [tokens.ts]
const accent = "#5EEC83" // verde Copilot
const ai     = "#B870FF" // morado IA
```

---
layout: roadmap
---

# Roadmap

::second::
## Foundations

Tokens, fuentes y fondo dark.

::third::
## Layouts

cover · statement · feature · roadmap · section · end

::fourth::
## Ship

Exporta a PDF/PPTX con `slidev export`.

---
layout: section
---

# Section divider

---
layout: end
---

# Thank you

github.com/github/mona-sans · SIL OFL
