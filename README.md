# The AI Field Map

An interactive survey map of the AI and ML landscape. Seven territories drawn to scale by scope, 224 tagged terms, and one reading-level switch so the same page serves a newcomer and a practitioner.

**Live:** https://deepusnath.github.io/ai-field-map/

An instrument of [Capability Commons](https://capabilitycommons.com): knowledge, tools and vocabulary held in common, so that reading the AI landscape is not gated by where you happened to study.

## What it does

Click any territory on the map and the gazetteer panel fills with a framing paragraph, worked examples, and the vocabulary that belongs to that region.

| Region | Role | Terms |
| --- | --- | --- |
| Artificial Intelligence | Outer scope | 24 |
| Machine Learning | Inner scope | 22 |
| Deep Learning | Innermost scope | 39 |
| Types of Learning | Method | 36 |
| Building Blocks | Infrastructure | 41 |
| Real-World Applications | Practice | 38 |
| Your Route In | Route | 26 |

The three scope regions are drawn nested, because that containment is the single most misunderstood thing about the field: deep learning sits inside machine learning, which sits inside AI.

## Two reading levels, one page

The **Newcomer / Practitioner** switch is the core mechanism, not a cosmetic toggle:

| | Newcomer | Practitioner |
| --- | --- | --- |
| Region framing | plain language | technically precise |
| Frontier-tier terms | hidden | shown |
| Per-term detail | definition only | definition plus an "In practice" note, a gotcha or a when-to-reach-for-this |

Every term carries a tier (foundation, working, frontier), a home region, and cross-links, so an expert can skim straight to what they do not already know. Press `/` to search all 224 terms.

## Capability Commons

This map is an Access-stage instrument in the Capability Commons pathway:

**Access** (shared ground) to **Agency** (human choice) to **Capability** (real freedom) to **Contribution** (public value)

- Framework concept model: [open Figma community file](https://www.figma.com/community/file/1666559229722530695/capability-commons-an-open-framework-for-turning-access-into-contribution)
- Background reading: [The Fishbowl Is Not the Future](https://medium.com/@deepusnath/the-fishbowl-is-not-the-future-62bcfc661246)
- First instance: [μLearn](https://mulearn.org)

## Running and editing it

There is no build step and no package manager. `index.html` is the whole application: markup, styles, the term data, and the interaction logic in one file.

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000. Opening the file directly with `file://` works too.

To add or change a term, edit the `T` object near the top of the `<script>` block:

```js
"cnn":{n:"CNN", f:"Convolutional neural network", t:1, r:"dl",
       d:"What it is, in one or two sentences.",
       x:"Optional practitioner note: a gotcha, or when to reach for it.",
       k:["convolution","pooling"]}
```

`t` is the tier (1 foundation, 2 working, 3 frontier), `r` is the home region id, `k` is the list of related term slugs. Add the slug to a cluster in the matching entry of the `R` array to make it appear on the page.

## Design notes

- Cartographic treatment: chart-paper ground, contour lines, a graticule, and map-plate lettering. Survey orange is spent only on selection state and the route.
- Type: Zilla Slab for map plates and headings, Source Sans 3 for reading, IBM Plex Mono for codes and tiers.
- Both light and dark themes are defined at token level and were checked for WCAG AA contrast; every measured text pair clears 4.5:1.
- The map is a real SVG, not an image with hotspots, so it is keyboard navigable (regions are tabbable, Enter or Space selects), searchable, and responsive.
- No external scripts. Google Fonts is the only network request, and every face has a real fallback stack.

## Credits

Built as an explorable companion to the poster "The Landscape of AI & ML".

MIT licensed. See [LICENSE](LICENSE).
