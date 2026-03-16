# Courtify Site — CLAUDE.md

Περίληψη του project και όλων των αλλαγών που έχουν γίνει.

## Project Overview

Στατικό single-page website για την **Courtify**, εταιρεία κατασκευής γηπέδων padel στην Ελλάδα.

- **Stack**: Pure HTML/CSS/JS — χωρίς framework, χωρίς build tool
- **Αρχεία**: `index.html`, `hero-bg.mov`
- **Γλώσσα**: Ελληνικά
- **Repo**: https://github.com/1kostaskak/courtify-site

## Design System

| Token | Τιμή | Χρήση |
|-------|------|-------|
| `--black` | `#0c0c0c` | Hero background |
| `--white` | `#ffffff` | Base background |
| `--offwhite` | `#f8f6f2` | Section backgrounds |
| `--green` | `#1e5c1e` | Primary brand color |
| `--green2` | `#2d7a2d` | Hover state |
| `--lime` | `#7db83a` | Accent, icons, highlights |
| `--gray` | `#888` | Body text secondary |
| `--border` | `#e0dbd2` | Card borders |
| `--ink` | `#1a1a1a` | Primary text |

**Font**: Inter (Google Fonts) — weights 300/400/500/600/700/800/900

## Sections (με σειρά)

1. **Nav** — Fixed, glassmorphism (backdrop-filter blur), hamburger menu για mobile
2. **Hero** — Full-viewport, background video, overlay, animated text, stats bar
3. **Why Courtify** (`#why`) — 2×2 grid με premium cards
4. **Services** (`#services`) — 2×2 grid με numbered cards
5. **Counters** — Animated number counters, πράσινο background
6. **Process** — 4-step grid
7. **Portfolio** (`#portfolio`) — Masonry-style grid με SVG court illustrations
8. **Testimonials** — 3-col grid, dark background
9. **CTA Banner** — Full-width call-to-action
10. **Contact** (`#contact`) — 2-col: info + form
11. **Footer**

---

## Ιστορικό Αλλαγών

### Hero Background Video
- Αντικαταστάθηκαν τα decorative elements (grid pattern + green blob) με `<video>` element
- `autoplay loop muted playsinline` attributes
- Αρχείο: `hero-bg.mov` (αντιγράφηκε από Downloads στον φάκελο του project)
- Overlay: `linear-gradient` για αναγνωσιμότητα κειμένου
- Video CSS: `height: 120%; top: -10%` για να δίνει χώρο στο parallax effect

### Animations & Mobile Responsive
**Scroll Reveal System:**
- 4 variants: `.reveal` (fade up), `.reveal-left` (slide from left), `.reveal-right` (slide from right), `.reveal-scale` (scale in)
- Cubic-bezier easing: `cubic-bezier(.22,.61,.36,1)`
- Delay classes: `.reveal-d1` (80ms) → `.reveal-d4` (320ms)
- `IntersectionObserver` με `rootMargin: '0px 0px -40px 0px'` και `unobserve` μετά το animation

**Parallax Hero Video:**
- `requestAnimationFrame` + passive scroll listener
- `translateY(scrollY * 0.25)` μόνο εντός hero height
- Disabled αυτόματα σε touch devices (`@media (hover: none)`)

**Mobile Breakpoints:**
- `1024px`: Portfolio 2-col, testimonials 2-col
- `900px`: Ήδη υπήρχε — nav hamburger, stats/counters/grid fixes
- `540px`: Single-column layouts, direction fixes
- `400px`: Font size reductions (hero h1: 2.4rem, counter-n: 2.2rem, κλπ)

### Why Courtify Redesign
**SVG Icons** (Lucide-style, stroke-based, 22×22):
- Παραγωγή → Package/cube icon
- Εμβέλεια → Globe icon
- Πιστοποίηση → Shield + checkmark icon
- Υποστήριξη → Wrench/tool icon

**Card Design:**
- `.why-icon-wrap`: 52×52px, lime-tinted background (`rgba(125,184,58,.08)`), rounded border
- Base shadow από default: `0 1px 3px rgba(0,0,0,.04), 0 4px 20px rgba(0,0,0,.05)`
- Hover: `translateY(-5px)` + stronger shadow + green border
- Animated lime top-bar: `::after` pseudo-element με `scaleX` transition
- Typography: titles `font-weight: 800`, `letter-spacing: -.3px`

---

## Κανόνες για Μελλοντικές Αλλαγές

- **Μην αλλάζεις** χρώματα, fonts, ή CSS variables χωρίς ρητή εντολή
- **Μην αλλάζεις** το υπάρχον design — μόνο βελτιώσεις/προσθήκες
- Το git remote έχει ήδη ρυθμιστεί με token authentication
- Push πάντα στο `main` branch
