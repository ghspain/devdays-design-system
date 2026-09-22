# Design System — GitHub Copilot DevDays decks

> Análisis de diseño extraído de las 3 presentaciones oficiales de GitHub para los
> DevDays, con el objetivo de **reproducir este lenguaje visual** en una herramienta
> de slides basada en código (Slidev / Bento / OpenSlide / reveal.js / Marp).
>
> Fuentes de datos: `analysis.json` (parseo XML de los `.pptx`), `previews/` (render
> PDF→PNG), y assets en `assets/`.

---

## 0. Resumen ejecutivo (TL;DR)

Es el **lenguaje de marca de GitHub Copilot**: un tema **casi-negro** con acentos en
**verde neón** y **morado/violeta** (los dos colores de marca de Copilot), tipografía
**Mona Sans** (la fuente open-source de GitHub) para titulares y **mono** para código.
Composición muy limpia: mucho aire, una idea por diapositiva, capturas de producto a
4K sobre fondo oscuro, y "statement slides" de texto gigante.

Para recrearlo: **fondo `#0D1117`‑ish, verde `#5EEC83`, morado `#B870FF`, Mona Sans +
Mona Sans Mono, ratio 16:9, tipografía grande y generosos márgenes.**

---

## 1. Lienzo / formato

| Propiedad | Valor |
|---|---|
| Ratio | **16:9** (1.778) |
| Tamaño | 13.33 × 7.5 in = 12192000 × 6858000 EMU |
| Píxeles de referencia (96 dpi) | 1280 × 720 |
| Píxeles de exportación sugeridos | 1920 × 1080 (o 2560 × 1440) |
| Nº de slides | CLI 22 · App‑EN 17 · App‑ES 16 |

> Los masters usan **4 fondos distintos casi-negros** (ver §2) → el diseño es
> **dark‑only**. No hay variante clara real; el blanco es solo texto/contraste.

---

## 2. Paleta de color (extraída del uso real, no del tema)

El `theme1.xml` de los `.pptx` trae colores "de relleno" de Office/Windows que **no**
son los del diseño. Los colores **reales** (frecuencia de uso en las diapositivas) son:

### Fondos (casi-negros, con tinte frío)
| Rol | Hex | Nota |
|---|---|---|
| `bg/base` | `#000000` | Master principal (CLI). Negro puro. |
| `bg/elevated-1` | `#0C1116` | Tarjetas/paneles sobre negro. |
| `bg/elevated-2` | `#121613` | Master 2 (App). Tinte verdoso. |
| `bg/elevated-3` | `#101411` | Master 3 (App). Tinte verdoso. |

### Verde Copilot (acento primario)
| Rol | Hex | Uso |
|---|---|---|
| `green/brand` | `#5EEC83` | **Acento principal.** Textos destacados, iconos, subrayados. |
| `green/brand-2` | `#5FED83` | Variante (prácticamente idéntica, redondeo). |
| `green/deep` | `#087827` · `#08872B` | Verde oscuro para rellenos/botones. |
| `green/soft` | `#8BF1A6` · `#8CF2A6` | Verde medio. |
| `green/mint` | `#BEFFD0` | Mint pálido (degradados/etiquetas). |

### Lima (acento secundario "pop")
| Rol | Hex | Uso |
|---|---|---|
| `lime` | `#D3FA36` | Highlights muy saturados, números, chips. |
| `lime/soft` | `#DBFF95` | Rellenos suaves. |

### Morado Copilot (acento de marca / "AI")
| Rol | Hex | Uso |
|---|---|---|
| `purple/brand` | `#B870FF` | **Color "AI/Copilot".** Titulares, halos, degradados. |
| `purple/bright` | `#C16EFF` | Variante brillante. |
| `purple/soft` | `#C898FD` | Lavanda clara. |
| `purple/deep` | `#8A11AF` | Morado saturado (más usado en CLI). |
| `purple/ink` | `#26115F` | Morado muy oscuro (fondo de degradado). |

### Soporte / enlaces
| Rol | Hex | Uso |
|---|---|---|
| `blue` | `#3194FF` | Enlaces / acento frío. |
| `cyan` | `#9EECFF` | Acento claro. |
| `teal` | `#56CCC4` | Followed‑link / detalle. |
| `text/primary` | `#FFFFFF` | Texto principal. |
| `text/muted` | ~`#8B949E` | (derivado) texto secundario sobre negro. |

**Degradados característicos:** verde→lima y morado→azul/cian sobre negro, usados en
halos y titulares "AI". Ver `previews/palette.png`.

---

## 3. Tipografía

El **tema** declara Arial (CLI) / Segoe UI (App), pero el **uso real** en las cajas de
texto es otro: es la pila de GitHub.

| Rol | Fuente real (uso) | Fallback / open‑source | Peso |
|---|---|---|---|
| **Display / titulares** | **Mona Sans Display** | `Mona Sans` (variable) → `Inter` | 600–700 |
| Titulares (variante) | Mona Sans Display Medium | Mona Sans 500 | 500 |
| **Body** | **Mona Sans** · Aptos | `Inter` · `Segoe UI` | 400–500 |
| **Código / mono** | **Mona Sans Mono** · Consolas | `JetBrains Mono` · `Fira Code` | 400 |

- **Mona Sans** es **open-source (SIL OFL)** y la fuente corporativa de GitHub → **usar
  la real**, no un sustituto. Descarga: <https://github.com/github/monas> (familia
  Display / Text / Mono, variable).
- **Aptos** es la fuente por defecto de Microsoft Office (aparece por herencia del
  master); en la práctica **úsala como Mona Sans**.

### Escala tipográfica (pt detectadas → px @96dpi)
| Nivel | pt | px aprox | Uso |
|---|---|---|---|
| Hero / statement | 60 | 80 | Frase grande a pantalla completa |
| H1 (título slide) | 36–40 | 48–53 | Título de diapositiva |
| H2 | 24 | 32 | Subtítulo / sección |
| Body grande | 16 | 21 | Texto principal (el más usado en CLI) |
| Body | 12–14.67 | 16–20 | Texto de apoyo, captions |
| Micro / meta | 10–10.5 | 13–14 | Etiquetas, fuentes, números de página |

Regla visual: **pocos niveles, tamaños grandes**. El 16 pt (≈21 px) es el caballo de
batalla del deck CLI; los titulares escalan a 36–60 pt.

---

## 4. Composición y layouts (nombres reales de los layouts)

Patrón de diseño por tipo de diapositiva detectado en los masters/layouts:

| Layout | Qué es | Cuándo usar |
|---|---|---|
| **Title and image stacked** | Título arriba + captura de producto debajo (el más usado) | Slides de feature con screenshot |
| **Roadmap slide (1/2 features, stacked/reversed)** | Columnas/tarjetas numeradas tipo roadmap | Listados de capacidades, "próximos pasos" |
| **Large statement** | Frase enorme centrada, casi sin más | Transiciones, ideas fuerza |
| **Three / Four statements** | 3–4 bloques de texto cortos en fila | Pilares, beneficios |
| **Title & Subtitle** | Portada / apertura de sección | Cover y secciones |
| **Section** | Separador de sección | Cambio de bloque temático |
| **Thank you** | Cierre | Última diapositiva |
| **Blank entirely / Blank** | Lienzo libre para imagen a sangre | Demo, vídeo, hero |

Convenciones de layout:
- **Márgenes amplios y simétricos** (~5–7 % del ancho). Contenido centrado o en
  semibloque izquierda‑derecha.
- **Una idea por slide**; mucho vacío intencional (el negro *es* parte del diseño).
- **Capturas a 4K** (3840×2160) de la app/CLI sobre el fondo negro → la UI "flota".
- **Vídeo embebido** (mp4) para demos (el deck App trae 5 clips, uno de 5.7 MB).
- **Iconografía SVG** plana en verde/morado (ver `assets/*/ppt/media/*.svg`).

---

## 5. Assets disponibles (ya extraídos)

```
assets/
├── cli/     ppt/media (59: 52 png · 4 svg · 2 jpeg · 1 mp4) · theme · masters · layouts
├── app-en/  ppt/media (67: 53 png · 5 svg · 3 jpeg · 1 emf · 5 mp4) · ...
└── app-es/  ppt/media (67, IDÉNTICO a app-en — solo cambia el texto de las slides)
```
- **88 media únicos** en total; **67 archivos compartidos** entre decks (mismos
  screenshots/brand assets).
- Iconos SVG reutilizables: `image3/6/12/14.svg` (CLI), `image1/6/9/18/21.svg` (App).
- Imágenes hero 4K: p. ej. `app-*/ppt/media/image14.png` (6.7 MB, 3840×2160).
- Los `.emf` son vectores de Office (convertir a SVG si se reutilizan).

> ⚠️ **Copyright:** estos assets son marca de GitHub. Válidos para **reproducir el
> estilo** en un contexto GitHub/Copilot; para un uso propio, sustituye logos y
> capturas por material propio conservando la paleta/tipografía.

---

## 6. Tokens listos para pegar

### 6.1 CSS variables (universal — Slidev / Bento / OpenSlide / reveal / Marp)
```css
:root{
  /* Canvas */
  --slide-w: 1280px; --slide-h: 720px;   /* 16:9 */
  --gutter: 64px;

  /* Backgrounds (dark-only) */
  --bg:            #000000;
  --bg-elev-1:     #0C1116;
  --bg-elev-2:     #121613;
  --bg-elev-3:     #101411;

  /* Copilot greens (primary accent) */
  --green:         #5EEC83;
  --green-deep:    #087827;
  --green-soft:    #8BF1A6;
  --green-mint:    #BEFFD0;

  /* Lime (pop accent) */
  --lime:          #D3FA36;
  --lime-soft:     #DBFF95;

  /* Copilot purple (AI accent) */
  --purple:        #B870FF;
  --purple-bright: #C16EFF;
  --purple-soft:   #C898FD;
  --purple-deep:   #8A11AF;
  --purple-ink:    #26115F;

  /* Support */
  --blue:          #3194FF;
  --cyan:          #9EECFF;
  --teal:          #56CCC4;

  /* Text */
  --text:          #FFFFFF;
  --text-muted:    #8B949E;

  /* Gradients (brand) */
  --grad-ai:    linear-gradient(120deg, var(--purple) 0%, var(--blue) 55%, var(--cyan) 100%);
  --grad-green: linear-gradient(120deg, var(--green-deep) 0%, var(--green) 50%, var(--lime) 100%);

  /* Type */
  --font-display: "Mona Sans Display","Mona Sans","Inter",system-ui,sans-serif;
  --font-body:    "Mona Sans","Inter","Segoe UI",system-ui,sans-serif;
  --font-mono:    "Mona Sans Mono","JetBrains Mono","Consolas",ui-monospace,monospace;

  /* Type scale (px @ 1280x720) */
  --fs-hero: 80px; --fs-h1: 52px; --fs-h2: 32px;
  --fs-body: 21px; --fs-small: 16px; --fs-micro: 14px;
}
```

### 6.2 Tailwind `theme.extend` (Bento / cualquier stack con Tailwind)
```js
// tailwind.config.js  → theme.extend
colors: {
  cop: {
    bg: "#000000", elev1: "#0C1116", elev2: "#121613", elev3: "#101411",
    green: "#5EEC83", greenDeep: "#087827", mint: "#BEFFD0",
    lime: "#D3FA36", purple: "#B870FF", purpleDeep: "#8A11AF",
    blue: "#3194FF", cyan: "#9EECFF",
  },
},
fontFamily: {
  display: ['"Mona Sans Display"','"Mona Sans"','Inter','sans-serif'],
  body: ['"Mona Sans"','Inter','sans-serif'],
  mono: ['"Mona Sans Mono"','"JetBrains Mono"','monospace'],
},
aspectRatio: { slide: "16 / 9" },
```

### 6.3 Tokens JSON (OpenSlide / Bento design tokens)
```json
{
  "color": {
    "bg": {"value": "#000000"},
    "bgElev2": {"value": "#121613"},
    "green": {"value": "#5EEC83"},
    "lime": {"value": "#D3FA36"},
    "purple": {"value": "#B870FF"},
    "text": {"value": "#FFFFFF"},
    "textMuted": {"value": "#8B949E"}
  },
  "font": {
    "display": {"value": "Mona Sans Display"},
    "body": {"value": "Mona Sans"},
    "mono": {"value": "Mona Sans Mono"}
  },
  "size": {
    "hero": {"value": "80px"}, "h1": {"value": "52px"}, "h2": {"value": "32px"},
    "body": {"value": "21px"}, "micro": {"value": "14px"}
  },
  "ratio": {"value": "16:9"}
}
```

---

## 7. Mapeo a cada herramienta

### Slidev (recomendado para este estilo)
`themes/setup` + frontmatter. Copia las variables CSS de §6.1 en `styles/index.css` y:
```yaml
---
theme: seriph          # o base
colorSchema: dark
fonts:
  sans: 'Mona Sans'
  serif: 'Mona Sans'
  mono: 'Mona Sans Mono'
---
```
- Instala las fuentes Mona Sans (OFL) localmente o vía `@fontsource`.
- Crea layouts en `layouts/`: `cover.vue` (Title&Subtitle), `statement.vue` (Large
  statement), `feature.vue` (Title and image stacked), `roadmap.vue`, `section.vue`,
  `end.vue` (Thank you). Replican los nombres de §4.
- Usa `--grad-ai` en titulares con `<span class="gradient">`.

### Bento (slides en React + Tailwind)
- Pega §6.2 en `tailwind.config.js`.
- Cada "slide" es un componente con `aspect-slide` y `bg-cop-bg`.
- Mapea los layouts de §4 a componentes: `<FeatureSlide>`, `<StatementSlide>`, etc.

### OpenSlide (si te refieres a la app de slides open-source)
- Aliméntala con los **design tokens** de §6.3 (JSON) — es el formato portable.
- Si "OpenSlide" era un error por **Open‑Slides / Marp**: usa §6.1 (CSS) con tema dark.

### reveal.js / Marp (alternativas)
- reveal: `--r-background-color: #000`, `--r-main-font: "Mona Sans"`, tema `black`.
- Marp: `theme: gaia` + `class: invert`, o CSS custom con §6.1.

---

## 8. Checklist para "nuestras" slides

- [ ] Fondo negro `#000` / paneles `#121613`. **Nunca** fondo claro.
- [ ] Titulares en **Mona Sans Display** 600, blanco o con `--grad-ai`.
- [ ] Un acento por slide: **verde `#5EEC83`** (default) o **morado `#B870FF`** (AI).
- [ ] **Lima `#D3FA36`** solo para 1 highlight puntual (números, chips).
- [ ] Código en **Mona Sans Mono** sobre `#0C1116`, con `--green` para strings.
- [ ] Capturas de producto **a sangre sobre negro**, sin marcos, sombra suave opcional.
- [ ] Márgenes ≥ 64 px, una idea por slide, mucho vacío.
- [ ] Cierre tipo "Thank you" y apertura tipo "Title & Subtitle".
- [ ] Sustituir logos/capturas de GitHub por los propios si el contexto no es GitHub.

---

## 9. Diferencias CLI vs App

| | **CLI deck** | **App deck (EN/ES)** |
|---|---|---|
| Slide size | 16:9 (12192000 EMU) | 16:9 (12188825 EMU) |
| Fuente dominante | Aptos + Mona Sans Display | **Mona Sans Display** (casi todo) |
| Color estrella | Verde `#5EEC83` + morado `#8A11AF` | Verde + **morado `#B870FF`** (más violeta) |
| Media | Ligero (7.7 MB, 1 vídeo) | **Pesado (36 MB, 5 vídeos, 4K)** |
| Nº layouts | Más variedad (statements, roadmap) | Más "Title and image stacked" |
| Idiomas | Solo EN | **EN y ES idénticos** (mismos 67 assets) |

> El deck App es el "hermano mayor" del CLI: misma marca, más rico en medios y más
> morado (enfatiza el lado "AI"). El EN y el ES son el **mismo diseño** traducido →
> para un template basta con uno, parametrizando el texto.
