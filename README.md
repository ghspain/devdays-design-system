# DevDays Design System 🎨

Análisis de diseño, assets y plantilla **Slidev** de las presentaciones oficiales de
[GitHub Copilot DevDays](https://github.com/github/dev-days) (2026).

> 🌐 **Demo en vivo:** <https://githubcommunity.es/devdays-design-system/>
> (landing con paleta, tipografía, galería de las 55 slides y el
> [deck Slidev interactivo](https://githubcommunity.es/devdays-design-system/deck/)).
> Alternativa: `ghspain.github.io/devdays-design-system`.

## 🔗 Origen y atribución (versión fijada)

Los materiales originales proceden del repositorio público
**[`github/dev-days`](https://github.com/github/dev-days)** (licencia **MIT**).
Como el repositorio de origen puede publicar más releases, se fija **la versión exacta**
de la que se descargaron los `.pptx`:

| Campo | Valor |
|---|---|
| Release tag | [`2026-07-30`](https://github.com/github/dev-days/releases/tag/2026-07-30) |
| Release ID | `362731584` |
| Publicada | `2026-07-31T16:08:05Z` |
| Nombre | *Dev Days Presentation Decks* |
| Assets totales del release | 7 (5 idiomas de `copilot-app-*` + `copilot-CLI`) |
| Licencia original | MIT |

De esa release se usaron **exactamente** estos 3 assets (URLs de descarga inmutables):

| Asset | Tamaño | Descarga |
|---|---|---|
| `copilot-CLI.pptx` | 7.94 MB | <a href="https://github.com/github/dev-days/releases/download/2026-07-30/copilot-CLI.pptx">releases/download/2026-07-30/copilot-CLI.pptx</a> |
| `copilot-app-english.pptx` | 38.72 MB | <a href="https://github.com/github/dev-days/releases/download/2026-07-30/copilot-app-english.pptx">…/copilot-app-english.pptx</a> |
| `copilot-app-spanish.pptx` | 38.32 MB | <a href="https://github.com/github/dev-days/releases/download/2026-07-30/copilot-app-spanish.pptx">…/copilot-app-spanish.pptx</a> |

Este repositorio contiene **derivados** de esos decks — conversiones a PDF, assets
extraídos, análisis de diseño y una plantilla Slidev propia — publicados con fines
educativos y con atribución a GitHub.

La tipografía **Mona Sans** incluida en la plantilla pertenece a
[`github/mona-sans`](https://github.com/github/mona-sans) (licencia OFL).

## 📁 Contenido

| Ruta | Descripción |
|---|---|
| [`design.md`](./design.md) | **Sistema de diseño** extraído de los decks: paleta, tipografía, escala, layouts, patrones visuales |
| [`analysis.json`](./analysis.json) | Análisis cuantitativo (fuentes, colores, medios por deck) |
| [`pdf/`](./pdf/) | Los 3 decks convertidos a PDF (LibreOffice headless) |
| [`previews/`](./previews/) | 55 previews PNG (una por slide) + `palette.png` |
| [`assets/`](./assets/) | Media y XML extraídos de los `.pptx` (`cli/` y `app-en/`¹) |
| [`slidev-template/`](./slidev-template/) | **Plantilla Slidev** que implementa el sistema de diseño |
| [`docs/`](./docs/) | Sitio publicado en **GitHub Pages** (landing + build del deck) |

¹ *Los media de `copilot-app-spanish.pptx` son byte-idénticos a los de la versión
inglesa, por lo que no se duplican en este repo.*

## 🌐 GitHub Pages

El sitio está servido desde la carpeta [`docs/`](./docs/) de la rama `main`. La
organización `ghspain` usa dominio propio, así que existen dos URLs equivalentes:

| URL | Contenido |
|---|---|
| <https://githubcommunity.es/devdays-design-system/> | Landing: paleta, tipografía, layouts, galería de 55 slides, PDFs y atribución |
| <https://githubcommunity.es/devdays-design-system/deck/> | Presentación Slidev (la plantilla, exportada estática) |
| <https://ghspain.github.io/devdays-design-system/> | misma landing en el dominio por defecto de Pages |
| <https://ghspain.github.io/devdays-design-system/deck/> | mismo deck en el dominio por defecto de Pages |

Para regenerar el deck tras tocar `slides.md` / layouts / estilos:

```bash
cd slidev-template
npm install
npx slidev build --base /devdays-design-system/deck/ --out dist
# 1. vaciar docs/deck/ y copiar ahí TODO el contenido de dist/
#    (incluye fonts/ e img/, que son parte del build)
# 2. copiar dist/404.html -> docs/404.html  (fallback SPA: enlaces directos a /deck/7)
# 3. commit + push; Pages reconstruye solo
```

> El `--base` es obligatorio: un GitHub Pages de proyecto se sirve bajo
> `/<repo>/`, no en la raíz del dominio (y aquí además el deck vive en `/<repo>/deck/`).
> Por el mismo motivo, las imágenes del frontmatter (`image: /img/...`) se resuelven en
> `layouts/feature.vue` concatenando `import.meta.env.BASE_URL`, no en crudo.

## 🚀 Plantilla Slidev

```bash
cd slidev-template
npm install
npm run dev     # editor local
npm run build   # exportar estático a dist/
```

Implementa el diseño de los DevDays: fondo `#0C1116`, acentos verde neón
`#5EEC83` / lima `#D3FA36` / púrpura `#B870FF` / azul `#3194FF`, Mona Sans
(Display/Sans/Mono), 6 layouts (`cover`, `section`, `two-cols`, `code`,
`roadmap`, `quote`) y tokens CSS en `styles/design.css`.

> ⚠️ **Slidev v51**: la sintaxis de fragments `--` ya no existe; se usan
> marcadores de slot `::nombre::` o `<v-click>`. Ver
> [`slidev-template/README.md`](./slidev-template/README.md).

## ⚖️ Licencia

- Contenido derivado de `github/dev-days`: **MIT** (© GitHub).
- Código y análisis propios (plantilla, `design.md`, `analysis.json`): **MIT**.

Ver [LICENSE](./LICENSE).
