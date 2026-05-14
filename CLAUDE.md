# Jay Polra's Academic Portfolio — Project Guide

> This document is the single source of truth for any AI agent, LLM, or collaborator working on jaypolra.github.io. Read this first before making any changes.

---

## Who Is This For?

**Jay Polra** — Graduate Research Assistant at CIVS (Center for Innovation through Visualization and Simulation), Purdue University Northwest. Researching computer vision, spatial audio, and vision-language models. Advised by Prof. Yang Ni and Prof. Chen Zhou.

The portfolio targets professors, recruiters, fellow researchers, and students. The design philosophy is: **professional, clean, impressive through simplicity** — not flashy. Every design decision should serve readability, credibility, and visual clarity.

---

## Tech Stack

| Layer | Technology | Notes |
|-------|-----------|-------|
| Static site generator | Hugo | Config in `config/_default/` |
| Theme framework | Hugo Blox Builder v0.6.1 | Tailwind CSS v4, NOT Bootstrap |
| CSS pipeline | `css.TailwindCSS` | Processes `assets/css/main.css`. Does NOT compile SCSS. |
| Modules | `blox-plugin-netlify` + `blox-tailwind` | Defined in `config/_default/module.yaml` |
| Hosting | GitHub Pages | Auto-deploys from `main` branch |
| Package manager | pnpm 10.14.0 | `package.json` at root |

### Critical Architecture Facts

1. **`assets/scss/custom.scss` is DEAD.** Tailwind v4 does not compile SCSS files. All custom CSS must go in `<style>` tags inside hook files. This file was removed.

2. **Hook file path has an underscore.** Hugo Blox loads hooks from `layouts/_partials/hooks/`, NOT `layouts/partials/hooks/`. The `get_hook.html` function uses `os.ReadDir` on the underscore path. Files in the non-underscore path are invisible to Hugo.

3. **CSS `:has()` selector scopes the sidebar layout.** The two-column grid is applied only via `.page-body:has(.resume-biography)`, so it only activates on the homepage. Inner pages (project detail, publication detail) are unaffected.

4. **`buildFuture: true`** is set in `hugo.yaml` because the CVPR 2026 paper has a future date (2026-06-01). Removing this flag will hide that publication.

---

## Repository Structure

```
jaypolra.github.io/
├── config/_default/
│   ├── hugo.yaml              # Site title, baseURL, buildFuture
│   ├── params.yaml            # Appearance, header, footer, SEO
│   ├── menus.yaml             # Navigation menu
│   └── module.yaml            # Hugo Blox module imports
├── content/
│   ├── _index.md              # Homepage — section blocks definition
│   ├── authors/admin/_index.md # Profile: bio, education, work, awards, interests
│   ├── project/               # 5 project page bundles
│   │   ├── geometry-grounded-nvas/
│   │   ├── ai-hazard-recognition/
│   │   ├── vlm-explainer/
│   │   ├── vlm-hazard-reasoning/
│   │   └── candidate-matcher/
│   └── publication/           # 3 publication entries
│       ├── nvas-cvpr-2026/
│       ├── aistch-2026/
│       └── tms-2025/
├── layouts/
│   └── _partials/hooks/head-end/
│       └── custom-styles.html # ALL custom CSS + JS (the only customization file)
├── assets/
│   ├── media/
│   │   ├── avatar.jpg         # Profile photo
│   │   ├── icon.png           # Favicon source (navy JP monogram)
│   │   └── stacked-peaks.svg  # Decorative asset
│   └── css/main.css           # Tailwind entry point (do not edit)
├── static/
│   ├── favicon.ico            # Browser favicon
│   └── uploads/resume.pdf     # Download CV target (PENDING — user will upload)
└── package.json               # pnpm, tailwindcss v4
```

---

## Homepage Layout (Desktop, >= 1024px)

The homepage uses a **32/68 two-column CSS Grid** layout:

```
┌─────────────────┬──────────────────────────────────┐
│  LEFT SIDEBAR   │  RIGHT CONTENT (scrollable)      │
│  (32%, sticky)  │                                   │
│                 │  Publications                     │
│  Profile Photo  │  ├── CVPR Workshop 2026           │
│  Name & Role    │  ├── AISTech 2026                 │
│  Organization   │  └── TMS/AIM 2025                 │
│  Social Links   │                                   │
│  Professional   │  Projects (3-column grid)         │
│  Summary        │  ├── Geometry-Grounded NVAS       │
│  Download CV    │  ├── AI Hazard Recognition        │
│                 │  ├── VLM Explainer                 │
│                 │  ├── VLM-Based Hazard Reasoning    │
│  (NO scroll)    │  └── Candidate Matcher             │
│                 │                                   │
│                 │  Work Experience                   │
│                 │  ├── GRA @ CIVS Purdue (2025-)     │
│                 │  └── SRE @ Asite (2023-2024)       │
│                 │                                   │
│                 │  Accomplishments                    │
│                 │  Interests (moved from sidebar)    │
└─────────────────┴──────────────────────────────────┘
```

### Key Layout Mechanics

- **Sidebar is sticky and does NOT scroll.** `position: sticky; top: 52px; height: calc(100vh - 52px); overflow: hidden;`
- **`zoom: 0.78`** on `.resume-biography` scales the sidebar to fit at 100% browser zoom (replicates the look of 80% zoom).
- **Education stays in the sidebar only** (not duplicated to right side).
- **Interests are cloned** from the biography block to the right content area via JavaScript. The original is hidden with CSS (`display: none`). This JS only runs on desktop (>= 1024px).
- **On mobile (< 1024px)** the grid collapses to single column; everything stays in the biography block naturally.
- **Hugo Blox footer branding** ("Made with Hugo Blox") is hidden via `.powered-by:not(:first-child) { display: none }`. The copyright line stays.

---

## Color Palette

| Element | Light Mode | Dark Mode |
|---------|-----------|-----------|
| Primary (navy) | `#14285A` | — |
| Accent (purple) | `#5B3FA0` | `#B8A5E0` |
| Links | `#5B3FA0` | `#B8A5E0` |
| Link hover | `#14285A` | `#D4C8F0` |
| Section headings (right) | `#14285A` | `#E8E4F0` |
| Download CV button | `#14285A` bg | `#5B3FA0` bg |
| Download CV hover | `#6B4FBB` bg | `#7B5FC0` bg |
| Social icons | theme default | `#ffffff` (forced white) |
| Favicon | Navy `#14285A` bg, white "JP" | Same |

---

## Content Sections (in `content/_index.md` order)

### 1. Biography (`resume-biography-3` block)
- Data source: `content/authors/admin/_index.md`
- Contains: photo, name, role, org, social links, professional summary, education, interests, awards
- Download CV button points to `uploads/resume.pdf`
- Education stays in sidebar only (not duplicated). Interests are moved to right side on desktop via JS

### 2. Publications (`collection` block, folder: `publication`)
- View: `citation`
- Currently 3 entries:
  - **CVPR Workshop 2026** — Visual Geometry Grounded Novel-View Acoustic Synthesis (featured: true)
  - **AISTech 2026** — Trailing Image Detection for Melt Shop Safety (featured: true)
  - **TMS/AIM 2025** — Dual-Model Industrial Safety (featured: false)
- `exclude_featured: false` means ALL publications show (featured and non-featured)

### 3. Projects (`collection` block, folder: `project`)
- View: `article-grid`, 3 columns, `fill_image: false`
- Each project is a page bundle: `content/project/{slug}/index.md` + `featured.jpg` or `featured.png`
- 5 projects currently:

| Project | Image | Tags |
|---------|-------|------|
| Geometry-Grounded NVAS | `featured.jpg` (132KB) | PyTorch, VGGT, Transformers, Spatial Audio, CVPR 2026 |
| AI Hazard Recognition | `featured.png` (722KB) | Python, YOLO, DeepSORT, FastAPI, React, AISTech 2026 |
| VLM Explainer | `featured.jpg` (100KB) | PyTorch, BLIP, CLIP, Grad-CAM, Explainable AI, Streamlit |
| VLM-Based Hazard Reasoning | `featured.png` (549KB) | Vision-Language Models, Prompt Engineering, Industrial AI |
| Candidate Matcher | `featured.png` (188KB) | Python, MiniLM, Sentence Transformers, NLP, Streamlit |

### 4. Work Experience (`resume-experience` block)
- Data source: `content/authors/admin/_index.md` → `work:` field
- 2 positions: GRA at Purdue (current), SRE at Asite (past)

### 5. Accomplishments (`resume-awards` block)
- Data source: `content/authors/admin/_index.md` → `awards:` field
- 3 entries: Graduate Research Grant, 1st Runner-up Poster Competition, Full Tuition Waiver

### 6. Education (sidebar only)
- Data source: `content/authors/admin/_index.md` → `education:` field
- MSc Computer Science @ Purdue (2024-2026), BE IT @ LJ Institute (2019-2023)
- Stays in left sidebar, NOT duplicated to right side

### 7. Interests (moved section)
- Cloned from biography to right content via JS
- 6 tags: Computer Vision, Spatial Audio, VLMs, XAI, Industrial AI Safety, Multimodal Learning

---

## The Single Customization File

**`layouts/_partials/hooks/head-end/custom-styles.html`** is the ONLY file containing custom CSS and JavaScript. Everything is here — no external stylesheets, no other hook files.

Structure:
1. `<style>` tag containing:
   - Color palette (light + dark)
   - Dark mode overrides (social icons, headings, buttons)
   - Sidebar grid layout (scoped to homepage via `:has(.resume-biography)`, desktop only via `@media (min-width: 1024px)`)
   - Global typography (body, headings, citations, nav, bio elements)
   - Global spacing (section padding, inner page max-width)
   - Footer branding hide
2. `<script>` tag containing:
   - Education/Interests mover (finds by h3 text, tags with classes, clones to right side)

---

## Rules for Future Changes

### Adding a New Publication
1. Create `content/publication/{slug}/index.md`
2. Follow the existing frontmatter pattern (title, authors, date, publication_types, publication, abstract, tags, summary)
3. Set `featured: true` if it's a highlight paper
4. If the date is in the future, `buildFuture: true` is already set — it will show
5. No other files need to change

### Adding a New Project
1. Create `content/project/{slug}/index.md` with frontmatter (title, summary, tags, date, links)
2. Add a `featured.jpg` or `featured.png` in the same folder
3. **Image guidelines:** Keep under 300KB. Max 1200px wide. JPEG for photos/renders, PNG for diagrams/UI. Hugo auto-detects `featured.*` files.
4. The project card appears automatically in the 3-column grid
5. Write the project description in the same research-storytelling voice: what's the problem, what did you build, what's the key insight, what are the results

### Adding a New Work Experience Entry
1. Edit `content/authors/admin/_index.md` → `work:` array
2. Add a new entry with: position, company_name, company_url, date_start, date_end, summary
3. Use `date_end: ''` for current positions

### Adding a New Section to the Homepage
1. Edit `content/_index.md` → `sections:` array
2. Add a new block entry (see Hugo Blox docs for block types)
3. The section will appear in the right content column automatically (CSS grid assigns `grid-column: 2` to all non-first children)
4. Section headings will auto-center with navy color on desktop

### Changing the Sidebar Content
- The sidebar shows whatever is in the `resume-biography-3` block (first child of `.page-body`)
- To add/remove items from the sidebar, edit `content/authors/admin/_index.md`
- **WARNING:** If you add too much content, it may overflow the sticky sidebar. The `zoom: 0.78` scaling helps, but test at 100% browser zoom
- Education and Interests are hidden from sidebar on desktop (moved to right) — if you add a new h3 section to the bio block and want it moved too, update the JS in `custom-styles.html`

### Changing Colors
- All colors are in the `<style>` tag in `custom-styles.html`
- The theme base is `indigo` (set in `params.yaml` → `appearance.color`)
- Custom colors override the theme. Primary navy is `#14285A`, accent purple is `#5B3FA0`
- Dark mode colors are in the `html.dark` selectors
- Favicon uses the navy color — regenerate `assets/media/icon.png` and `static/favicon.ico` if palette changes

### Changing Typography
- All font sizes are in the `GLOBAL TYPOGRAPHY` section of `custom-styles.html`
- Everything uses `!important` to override Tailwind utility classes
- Body: 1.1rem / 1.8 line-height. Headings: 1.85rem (h2), 1.3rem (h3)
- The design aims for readable, not text-heavy and not empty — a balanced middle ground

### CSS Pitfalls to Avoid
1. **Never put CSS in `assets/scss/custom.scss`** — it's not compiled. Always use the hook file.
2. **Never create files in `layouts/partials/hooks/`** (no underscore) — they won't load.
3. **Avoid broad selectors** like `div:first-child` or `[class*="rounded"]` — Hugo Blox uses many utility classes and you'll hit unintended elements. Always scope selectors to `.resume-biography`, `.page-body`, or specific `[href*="..."]` patterns.
4. **The `:has()` selector** is used for homepage scoping. It's supported in all modern browsers but NOT in Firefox < 121 (Dec 2023). Acceptable tradeoff for the target audience.
5. **`!important`** is necessary throughout because Tailwind utility classes have high specificity. This is by design, not sloppiness.
6. **The `mt-16` override** (`margin-top: 0.75rem !important`) reduces the gap between section headings and content lists. Hugo Blox adds large top margins by default.

### Deployment
- Push to `main` → GitHub Pages auto-deploys
- Build command: `hugo --minify` (defined in `package.json`)
- No CI config file needed — GitHub Pages detects Hugo automatically
- Build takes ~30 seconds, deployment propagation ~1-2 minutes

### Pending Items
- `static/uploads/resume.pdf` — Download CV button target. User will upload when ready.

---

## Research Narrative

Jay's work follows a consistent thread: **making AI systems work reliably outside controlled settings, and understanding why they work (or don't).**

Three research pillars:

1. **Spatial Audio & Novel-View Synthesis** — Removing expensive preprocessing (SfM/COLMAP) from audio-visual pipelines. The CVPR paper shows you can get geometry grounding through learned encoders instead.

2. **Industrial AI Safety** — Detection alone isn't enough when cameras have blind spots. The system maintains conservative safety state when visual evidence is unavailable. Real deployment constraints drive the architecture.

3. **VLM Explainability** — Vision-language models generate fluent text but don't explain themselves. Grad-CAM attribution + perturbation testing establishes causal (not correlational) influence of image regions on model outputs.

The connecting instinct across all work: **open the black box before building on top of it.** Every project page should reflect this — state the problem clearly, explain the architectural decision and why it matters, show the result.

---

## Voice & Tone

- **Research writing, not marketing.** State what the system does and why the design choice matters.
- **Problem-first.** Every project description starts with the gap or limitation being addressed.
- **Specific over general.** "10x faster preprocessing than COLMAP" beats "significantly faster."
- **No superlatives.** No "cutting-edge," "state-of-the-art" (unless citing a benchmark), "revolutionary."
- **Professional summary is personal but grounded.** Not a list of skills — it's about what drives the research.

---

## Quick Reference Commands

```bash
# Local development
pnpm dev                    # hugo server --disableFastRender

# Build
pnpm build                  # hugo --minify

# Deploy
git add <files>
git commit -m "description"
git push                    # GitHub Pages auto-deploys
```
