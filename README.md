# gemfyi-embed

[![npm](https://img.shields.io/npm/v/gemfyi-embed)](https://www.npmjs.com/package/gemfyi-embed)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen)](https://www.npmjs.com/package/gemfyi-embed)

Embed **GemFYI** widgets — gems, glossary terms, interactive tools, and inline elements — on any website. **8 widget types**, zero dependencies, Shadow DOM style isolation, 4 built-in themes (light, dark, sepia, auto), 2 styles (modern, technical), and live data from the [GemFYI](https://gemfyi.com) database.

Every widget includes a "Powered by GemFYI" backlink directing readers to the full reference.

> **Try the interactive widget builder at [widget.gemfyi.com](https://widget.gemfyi.com)**

## Quick Start

```html
<!-- Place widget div where you want it to appear -->
<div data-gemfyi="entity" data-slug="gems" data-theme="light"></div>

<!-- Load the embed script once, anywhere on the page -->
<script src="https://cdn.jsdelivr.net/npm/gemfyi-embed@1/dist/embed.min.js"></script>
```

That's it. The widget fetches data from the GemFYI API and renders with full style isolation.

## Widget Types

| Type | Usage | Description |
|------|-------|-------------|
| `entity` | `<div data-gemfyi="entity" data-slug="..."></div>` | Entity detail card — element, alloy, gem, star, or mineral |
| `glossary` | `<div data-gemfyi="glossary" data-slug="..."></div>` | Glossary term definition with cross-references |
| `guide` | `<div data-gemfyi="guide" data-slug="..."></div>` | Guide summary card with key takeaways |
| `compare` | `<div data-gemfyi="compare" data-slug="..."></div>` | Side-by-side entity comparison |
| `search` | `<div data-gemfyi="search" data-slug="..."></div>` | Search box linking to the full database |
| `mohs-scale` | `<div data-gemfyi="mohs-scale" data-slug="..."></div>` | Mohs hardness scale visualization with colored segments |
| `optical-card` | `<div data-gemfyi="optical-card" data-slug="..."></div>` | Gemological optical properties — RI, birefringence, dispersion |
| `mohs-inline` | `<div data-gemfyi="mohs-inline" data-slug="..."></div>` | Inline Mohs hardness dot + number |

## Widget Options

| Attribute | Values | Default | Description |
|-----------|--------|---------|-------------|
| `data-gemfyi` | entity, compare, glossary, guide, search, [tools] | required | Widget type |
| `data-slug` | e.g. "gems" | — | Entity slug from the GemFYI database |
| `data-theme` | light, dark, sepia, auto | light | Visual theme (`auto` follows OS preference) |
| `data-style` | modern, technical | modern | Widget design style |
| `data-size` | default, compact, large | default | Widget size |
| `data-placeholder` | any string | "Search Gems..." | Search box placeholder |

## Themes

```html
<!-- Light (default) -->
<div data-gemfyi="entity" data-slug="gems" data-theme="light"></div>

<!-- Dark -->
<div data-gemfyi="entity" data-slug="gems" data-theme="dark"></div>

<!-- Sepia -->
<div data-gemfyi="entity" data-slug="gems" data-theme="sepia"></div>

<!-- Auto — follows OS dark/light preference -->
<div data-gemfyi="entity" data-slug="gems" data-theme="auto"></div>
```

## Styles

```html
<!-- Modern (default) — clean lines, rounded corners, accent gradients -->
<div data-gemfyi="entity" data-slug="gems" data-style="modern"></div>

<!-- Technical — monospace type, grid overlays, laboratory aesthetic -->
<div data-gemfyi="entity" data-slug="gems" data-style="technical"></div>
```

## Web Components (Custom Elements)

As an alternative to `data-*` attributes, you can use native HTML custom elements:

```html
<!-- Custom element form -->
<gemfyi-entity slug="gems" theme="light"></gemfyi-entity>
<gemfyi-compare slugs="gems,other-slug"></gemfyi-compare>
<gemfyi-search placeholder="Search Gems..."></gemfyi-search>

<script src="https://cdn.jsdelivr.net/npm/gemfyi-embed@1/dist/embed.min.js"></script>
```

Use `style-variant` (not `style`) to avoid conflicts with the HTML reserved `style` attribute.

## Examples

### Entity Card

```html
<div data-gemfyi="entity" data-slug="gems" data-theme="light"></div>
<script src="https://cdn.jsdelivr.net/npm/gemfyi-embed@1/dist/embed.min.js"></script>
```

### Side-by-Side Comparison

```html
<div data-gemfyi="compare" data-slugs="gems,other-slug"></div>
<script src="https://cdn.jsdelivr.net/npm/gemfyi-embed@1/dist/embed.min.js"></script>
```

### Search Box

```html
<div data-gemfyi="search" data-placeholder="Search Gems..."></div>
<script src="https://cdn.jsdelivr.net/npm/gemfyi-embed@1/dist/embed.min.js"></script>
```

### Glossary Term

```html
<div data-gemfyi="glossary" data-slug="example-term" data-theme="light"></div>
<script src="https://cdn.jsdelivr.net/npm/gemfyi-embed@1/dist/embed.min.js"></script>
```

## CDN Options

### jsDelivr (recommended — global CDN, auto-updates with npm)

```html
<script src="https://cdn.jsdelivr.net/npm/gemfyi-embed@1/dist/embed.min.js"></script>
```

### Specific version (production stability)

```html
<script src="https://cdn.jsdelivr.net/npm/gemfyi-embed@1.0.0/dist/embed.min.js"></script>
```

### npm (for bundlers)

```bash
npm install gemfyi-embed
```

```javascript
import 'gemfyi-embed';
```

## Technical Details

- **Shadow DOM**: Complete style isolation — no CSS conflicts with your site
- **Zero dependencies**: No jQuery, React, or any external library
- **2 styles**: Modern (accent gradients) and Technical (monospace, lab aesthetic)
- **4 themes**: Light, Dark, Sepia, Auto (OS preference detection)
- **CORS**: GemFYI API has CORS enabled for all origins
- **MutationObserver**: Works with dynamically added elements (SPAs)
- **IntersectionObserver**: Lazy loading — widgets only fetch when entering viewport (200px margin)
- **Rich Snippets**: DefinedTerm JSON-LD injected for glossary widgets
- **Bundle size**: Tree-shaken per site — only includes tools available on GemFYI

## Learn More About Gems

Visit [gemfyi.com](https://gemfyi.com) — GemFYI is a comprehensive gems reference with interactive tools, guides, and developer resources.

- **API docs**: [gemfyi.com/developers/](https://gemfyi.com/developers/)
- **Widget builder**: [widget.gemfyi.com](https://widget.gemfyi.com)
- **npm package**: [npmjs.com/package/gemfyi-embed](https://www.npmjs.com/package/gemfyi-embed)
- **GitHub**: [github.com/fyipedia/gemfyi-embed](https://github.com/fyipedia/gemfyi-embed)

## Science FYI Family

Part of [FYIPedia](https://fyipedia.com) — open-source developer tools ecosystem. Science FYI covers chemistry, geology, astronomy, and materials science. Hub: [labfyi.com](https://labfyi.com).

| Site | Domain | Focus | Package |
|------|--------|-------|---------|
| ChemFYI | [chemfyi.com](https://chemfyi.com) | Periodic table, elements, compounds, reactions | [npm](https://www.npmjs.com/package/chemfyi-embed) |
| AlloyFYI | [alloyfyi.com](https://alloyfyi.com) | Metal alloys, compositions, properties, 6-axis ratings | [npm](https://www.npmjs.com/package/alloyfyi-embed) |
| **GemFYI** | [gemfyi.com](https://gemfyi.com) | Gemstones, Mohs hardness, optical properties, origins | **[npm](https://www.npmjs.com/package/gemfyi-embed)** |
| StarFYI | [starfyi.com](https://starfyi.com) | Stars, constellations, spectral classification, magnitudes | [npm](https://www.npmjs.com/package/starfyi-embed) |
| MineralFYI | [mineralfyi.com](https://mineralfyi.com) | 6,215 minerals, crystal systems, Mohs hardness | [npm](https://www.npmjs.com/package/mineralfyi-embed) |

## License

MIT — see [LICENSE](./LICENSE).

Built with care by [FYIPedia](https://fyipedia.com).
