# DevDays Design System 🎨

Análisis de diseño, assets y plantilla **Slidev** de las presentaciones oficiales de
[GitHub Copilot DevDays](https://github.com/github/dev-days) (2026).

## 🔗 Origen y atribución

Los materiales originales proceden del repositorio público
**[`github/dev-days`](https://github.com/github/dev-days)** (licencia **MIT**):

- [`copilot-CLI.pptx`](https://github.com/github/dev-days/releases/tag/2026-07-30)
- `copilot-app-english.pptx`
- `copilot-app-spanish.pptx`

(assets del release `2026-07-30`). Este repositorio contiene **derivados** de esos
decks — conversiones a PDF, assets extraídos, análisis de diseño y una plantilla
Slidev propia — publicados con fines educativos y con atribución a GitHub.

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

¹ *Los media de `copilot-app-spanish.pptx` son byte-idénticos a los de la versión
inglesa, por lo que no se duplican en este repo.*

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
