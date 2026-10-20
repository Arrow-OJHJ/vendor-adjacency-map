# Arrow ECS UK - Vendor Adjacency & Line Card Tool

A static HTML tool for Arrow ECS UK sales teams to explore the vendor portfolio, understand cross-sell opportunities, and find adjacent products across the line card.

Designed to be hosted on GitHub Pages or any static file host - no server, no build step, no dependencies.

---

## What's in here

```
vendor-adjacency-map/
├── index.html                  ← Main vendor grid (line card overview)
├── vendors/
│   ├── ibm.html                ← IBM vendor profile page
│   ├── opswat.html             ← OPSWAT vendor profile page
│   ├── f5.html                 ← F5 Networks vendor profile page (also used by F5 Networks Global Support tile)
│   ├── entrust.html            ← Entrust nShield vendor profile page
│   └── blackduck.html          ← Black Duck by Synopsys vendor profile page
├── vendor-sales-out/           ← 2025 sales-out reports (internal – not published)
├── .bob/                       ← Planning documents and working notes (internal)
├── arrow-enterprise-computing-solutions-uk-line-card-2026.pdf
├── README.md
└── project-history.md
```

---

## Pages

### `index.html` — Vendor Line Card

The main page. Shows all 84 vendors from the Arrow ECS UK Line Card 2026 as searchable, filterable tiles.

**Features:**
- **Search** — filter by vendor name in real time
- **Tag filters** — filter by any combination of the 9 Arrow categories:
  - Data Centre, Business Intelligence, Cloud, Mobility, Security, Networking, IoT & Edge, ArrowSphere, DevOps
- **Sort** — Popularity (default, IBM first), A–Z, or Z–A
- **Click-through** — vendors with a profile page show "View profile ›" and link through; others show "Profile coming soon"

**Data source:** Arrow ECS UK Line Card 2026 PDF (as of 1 July 2026)

---

### Vendor Profile Pages (`vendors/`)

Individual pages for each vendor, built to a consistent template. Currently live:

| Vendor | File | Status |
|--------|------|--------|
| IBM | `vendors/ibm.html` | ✅ Live |
| OPSWAT | `vendors/opswat.html` | ✅ Live |
| F5 Networks | `vendors/f5.html` | ✅ Live |
| F5 Networks Global Support | `vendors/f5.html` | ✅ Live (shared page) |
| Entrust | `vendors/entrust.html` | ✅ Live |
| Black Duck | `vendors/blackduck.html` | ✅ Live |

**Each page includes:**
1. **Overview** — plain-English description of what the vendor does and why it matters to Arrow sales teams
2. **Arrow-Carried Portfolio** — the specific product lines available through Arrow ECS UK, with descriptions
3. **Cross-sell & Expansion Opportunities** — other Arrow vendors that pair well, with a "why" explanation and a colour-coded relationship type (Complementary / Integration partner / Expansion)
4. **Competitive Landscape** — vendors a rep will encounter on the same shortlist, with positioning notes
5. **Ideal Customer Profile** — size, verticals, trigger events, and key personas
6. **Sidebar** — Arrow Advantage (accreditations, programmes), Key Facts, and Related Vendors links

---

## Design system

Built with [IBM Carbon Design System](https://carbondesignsystem.com/) principles:
- IBM Gray scale colour tokens (`#161616` → `#f4f4f4`)
- IBM Blue 60 (`#0f62fe`) as primary accent
- IBM Plex Sans font stack
- Square corners (Carbon convention — no border-radius on interactive elements)
- 1px gap grid layout for the vendor tile grid
- Sticky header and controls bar

Tag colours follow Carbon semantic colours:
| Tag | Colour |
|-----|--------|
| Data Centre | IBM Blue 60 `#0f62fe` |
| Business Intelligence | Purple 60 `#8a3ffc` |
| Cloud | Teal 50 `#009d9a` |
| Mobility | Green 50 `#198038` |
| Security | Red 60 `#da1e28` |
| Networking | Magenta 50 `#ee5396` |
| IoT and Edge | Orange 40 `#ff832b` |
| ArrowSphere | Blue 70 `#0043ce` |
| DevOps | Purple 70 `#6929c4` |

---

## Adding a new vendor page

1. Copy an existing vendor page (e.g. `vendors/ibm.html`) as a starting point
2. Update all content sections — overview, portfolio, cross-sells, competitors, ICP
3. Add the file to the `VENDOR_PAGES` map in `index.html`:

```js
const VENDOR_PAGES = {
  "IBM":                        "vendors/ibm.html",
  "F5 Networks":                "vendors/f5.html",
  "F5 Networks Global Support": "vendors/f5.html",
  "Entrust":                    "vendors/entrust.html",
  "BlackDuck":                  "vendors/blackduck.html",
  "Opswat":                     "vendors/opswat.html",
  "Nutanix": "vendors/nutanix.html",  // ← add new entries here
};
```

The vendor name must match **exactly** the `name` field in the `VENDORS` array in `index.html`.

---

## Hosting on GitHub Pages

1. Push the `vendor-adjacency-map/` folder to a GitHub repository
2. Go to **Settings → Pages**
3. Set source to the branch and folder containing `index.html`
4. GitHub will serve it at `https://<username>.github.io/<repo>/`

All paths are relative so the site works from any subdirectory.

---

## Source data

- Arrow ECS UK Line Card 2026 (PDF): `arrow-enterprise-computing-solutions-uk-line-card-2026.pdf`
- Arrow vendor portal: [arrow.com/globalecs/uk/products](https://www.arrow.com/globalecs/uk/products/)

---

## Project context

See `project-history.md` for the full reasoning, design decisions, and development history – useful context when picking this up in a new session.
