
# 🗺️ Barcelona — Interactive Districts & Neighbourhoods Map

**An interactive map of Barcelona's administrative divisions** — 10 districts (*districtes*) and 73 neighbourhoods (*barris*). Shows name etymology, historical background, points of interest, and links to official sources in three languages: **Spanish (ES)**, **Catalan (CA)**, and **Russian (RU)**.

🔗 **Live demo:** [hollleden.github.io/barcelona-map](https://hollleden.github.io/barcelona-map/)

---

## ✨ Features

- **Vector SVG map** — no tiles, no external services, loads instantly
- **10 districts** with colour coding, boundaries, and labels
- **73 neighbourhoods** numbered according to the official city catalogue
- **Three languages** with instant switching, no page reload
- **Sidebar** — collapsible catalogue of districts and neighbourhoods
- **Detail card** — when you pick a district or neighbourhood:
  - Name etymology
  - Historical background
  - Points of interest with links
  - Wikipedia and Google Maps links
- **Modal window** — quick neighbourhood info preview
- **Tooltip** — on hover over a neighbourhood on the map
- **Responsive** — works on desktop and mobile

---

## 🛠 Tech Stack

- **Vanilla JS** — no frameworks, no build step
- **SVG map** — vector boundaries embedded directly in HTML
- **CSS** — custom properties, responsive layout
- **Fonts** — Source Sans Pro, JetBrains Mono, Open Sans (Google Fonts)

---

## 📂 Structure

```
barcelona-map/
├── index.html                          ← main file (all-in-one)
├── README.md
└── data/                               ← optional, if you extract data
    ├── barcelona-districts-research.json
    ├── barcelona-districts-full-historia.json
    └── barcelona-content-review.json
```

The whole app is a **single HTML file**. District and neighbourhood data is embedded in a `<script>` block as the `DATA` object.

---

## 🚀 Getting Started

### Local

```bash
# Just open the file in a browser
open index.html
```

Or via a local server (useful for testing on mobile):

```bash
python3 -m http.server 8000
# then open http://<your-IP>:8000/
```

### GitHub Pages

```bash
git init -b main
git add index.html README.md
git commit -m "Initial commit"
gh repo create barcelona-map --public --source=. --push
gh api repos/:owner/barcelona-map/pages -X POST \
  -f "source[branch]=main" -f "source[path]=/"
```

Live in 1–2 minutes at: `https://<your-username>.github.io/barcelona-map/`

---

## 📊 Data Sources

- **District and neighbourhood geometry** — [Open Data BCN](https://opendata-ajuntament.barcelona.cat/data/dataset/20170706-districtes-barris)
- **Etymology and history** — [Ajuntament de Barcelona](https://ajuntament.barcelona.cat/) and [Viquipèdia](https://ca.wikipedia.org/)
- **Neighbourhood list** — [Fitxes dels barris](https://ajuntament.barcelona.cat/)
- **Points of interest** — official district pages of the Barcelona City Council

---

## 🌍 Languages

Interface and content are available in:

| Language | Code | Source of etymology |
|---|---|---|
| Español | ES | Ajuntament de Barcelona |
| Català | CA | Viquipèdia |
| Русский | RU | Community translation |

Language switcher is in the top-right corner.

---

## 🎨 Design

- **Palette** — paper atlas: warm cream background, muted earthy tones, terracotta accent
- **Typography** — Source Sans Pro for body text, JetBrains Mono for service labels
- **Map** — vector shapes with semi-transparent fill and white borders
- **Highlight** — the active district / neighbourhood is highlighted in the accent colour

---

## 📱 Mobile Version

- Sidebar slides in as a drawer
- Hamburger button to open the catalogue
- Map scales to screen width
- Touch targets optimised for fingers

---

## 🔧 Customisation

### Change district colours

In the `DATA.districts` object:

```js
"d1": {
  "num": 1,
  "color": "#C17A5D",  // ← district colour
  ...
}
```

### Add a neighbourhood

In the `DATA.barris` object:

```js
"74": {
  "num": 74,
  "district": "d1",
  "name": "Name",
  "cx": 400, "cy": 500,  // label coordinates on the map
  "es": { "trans": "...", "etym": "..." },
  "ca": { "trans": "...", "etym": "..." },
  "ru": { "trans": "...", "etym": "..." }
}
```

And add a `<path class="barri" data-barri-id="74" ...>` element to the SVG.

---

## 📄 License

- **Code** — MIT
- **Geodata** — Open Data BCN (CC BY 4.0)
- **Texts** — © Ajuntament de Barcelona / authors, translations by the community

---

## 🙏 Credits

- [Open Data BCN](https://opendata-ajuntament.barcelona.cat/) — geodata
- [Ajuntament de Barcelona](https://ajuntament.barcelona.cat/) — historical texts
- [Viquipèdia](https://ca.wikipedia.org/) — etymology
