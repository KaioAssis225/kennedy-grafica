# Design — Kennedy Gráfica

<!-- impeccable:design-schema 1 -->

Visual world: **Amostra de Papel** (paper-swatch / guillotine-stack). Direction #3, seed `cd96b739`. Documented from the built `index.html` + `style.css` — ground truth, not intention.

## Thesis

A print shop shown in its own material — the paper-sample fan and the trimmed stack — replacing the category-default logo-hero + photo-card grid. Warm paper ground, brand green owning whole fields, and every service rendered as a paper "swatch" with its own stock-color chip.

Mode: **Persuade**. The visitor must understand what the shop does, that it's fast and local, and act via WhatsApp or a store visit.

## Color

Committed strategy: brand **green owns whole regions** (hero, pitch band, footer), paper carries the reading areas. Never the cream-plus-serif AI default.

| Token | Value | Role |
|---|---|---|
| `--paper` | `#F4EEE1` | Warm paper ground (body, service/local sections) |
| `--paper-card` | `#FBF7EE` | Lighter stock for swatch cards |
| `--ink` | `#1A1712` | Primary text on paper |
| `--ink-soft` | `#524B3B` | Secondary text (warm-tinted, never gray) |
| `--line` | `rgba(26,23,18,0.14)` | Hairlines on paper |
| `--green` | `#168249` | Brand green (accents, chip marks) |
| `--green-700` | `#0E6438` | Interactive green |
| `--green-800` | `#0C5230` | Hero field |
| `--green-900` | `#063A20` | Footer field |
| `--green-deep` | `#073A21` | Hero/pitch gradient base |
| `--on-green` | `#F6F1E5` | Text on green fields |
| `--on-green-soft` | `rgba(246,241,229,0.74)` | Secondary text on green |
| `--wa` / `--wa-hover` / `--wa-ink` | `#1FA355` / `#23B75F` / `#06251A` | WhatsApp button (dark ink on vivid green) |
| `--wa-float` | `#25D366` | Floating WhatsApp bubble |

Per-swatch stock-chip colors are set inline via `--chip` (green, red `#C0392B`, amber `#E8A33D`, mustard `#B8902A`, ink `#1B1712`, magenta `#C0397A`, teal `#127D6E`, violet `#6D5AA6`, cyan `#1E7FA8`) — read as a paper sample fan. Chip labels sit in a paper tag for contrast on any chip.

## Typography

- **Display:** `Bricolage Grotesque` (600–800), tracking down to `-0.045em` on the hero wordmark. Used for the wordmark, section/band titles, group titles, swatch names, pitch headline.
- **Text:** `Archivo` (400–700). Body, specs, facts, buttons, legal.
- Both self-served from Google Fonts. No system display face; no serif.
- Hero wordmark: `clamp(3.75rem, 14vw, 9.5rem)`, line-height `0.86`. Band titles `clamp(1.9rem, 4.6vw, 3.1rem)`. Headings use `text-wrap: balance`.
- Spec/label text: uppercase, `0.06–0.16em` tracking, `tabular-nums` for sizes.

## Space, radius, elevation

- Container `--wrap: 1180px`, side padding `clamp(18px, 4vw, 40px)`.
- Radii: `--radius: 10px`, `--radius-sm: 6px`.
- Shadows carry offset + blur: `--shadow-sm/md/lg` tinted green-black. No zero-blur block shadows.
- Rhythm: more space above a heading than below; section padding `clamp(56px, 9vw, 100px)`.

## Components

- **Nav** (`.nav`): fixed, transparent over the green hero with paper text; gains `.is-solid` (paper bg, frosted blur, ink text, hairline) past 60px scroll. WhatsApp link is a vivid-green pill in both states.
- **Mobile sheet** (`.sheet`): right-slide drawer + overlay, `aria-hidden`/`aria-expanded` wired, Esc-to-close, closes on link tap. Hamburger appears ≤720px.
- **Buttons** (`.btn`): `--wa` (dark ink on vivid green, primary), `--paper` (paper on green fields), `--ghost` (outline on green), `--outline` (outline on paper). `--lg` size for hero/pitch.
- **Crop marks** (`.crop--tl/tr/bl/br`): L-shaped corner registration marks on green fields.
- **Cutline** (`.cutline`): dashed guillotine "corte aqui" divider with a drawn scissors SVG, opening the services section.
- **Swatch** (`.swatch`): paper card = colored stock chip (with paper stock-name tag) + name + description + spec tags. Grid: `--n4` group (4-up) and `--n5` group (5-up), collapsing to 2/1 columns. This uniform sample-sheet grid is intentional to the world.
- **Hero / Pitch**: green fields with radial highlight; pitch is centered with a paper CTA.
- **Map** (`.map-box`): Leaflet + OpenStreetMap, green-framed, soft shadow, `scrollWheelZoom` off, branded popup.
- **WhatsApp float** (`.wa-float`): fixed bubble, bottom-right.

## Motion

One authored moment: `.reveal` elements fade + rise on scroll via IntersectionObserver, exponential ease-out from an already-laid-out default, staggered across swatches. Fully disabled under `prefers-reduced-motion`.

## Responsive

Mobile-first. Breakpoints: swatches 1→2→(3/4/5) cols; hero facts stack ≤720px; local grid stacks ≤860px (map first); nav collapses to the sheet ≤720px; footer stacks ≤720px.

## Accessibility

`lang="pt-BR"`, skip link, semantic landmarks (`header`/`nav`/`main`/`footer`), drawn SVG icons (no emoji), visible `:focus-visible` outline, decorative marks `aria-hidden`, reduced-motion honored. Text/paper and text/green contrasts clear ≥4.5:1.

## Do / Don't

- Keep green fields owning whole regions; don't dilute to green accents on neutral.
- Services stay paper swatches with stock chips; don't reintroduce photo-over-title cards.
- No gradient text, glassmorphism decoration, colored left-borders, block shadows, emoji icons, or eyebrow labels of the vague-category kind.
- All business facts (address, hours, CNPJ, WhatsApp) are real — see [PRODUCT.md]; never fabricate reviews, pricing, or claims.
