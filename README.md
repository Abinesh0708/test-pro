# APEX Logistics — Freight & Supply Chain Website Template

A responsive, editorial landing page template built for global freight forwarders, 3PL providers, cargo carriers, and supply chain platforms. Delivered as a self-contained HTML5, CSS3, and vanilla JavaScript package with **zero build tools or runtime framework dependencies**.

---

## Key Features

- **Zero-Build Architecture**: All markup, design tokens, responsive CSS, and interactive JavaScript live in [`index.html`](index.html) alongside local static assets in [`assets/`](assets/). Open, edit, and deploy to any static host immediately.
- **Swiss-Editorial Design System**: High-contrast monochrome palette (`#ffffff` / `#f4f4f4` / `#111111`) paired with cobalt blue accents (`#1a4be0`), fluid typography (`clamp()`), and **Hanken Grotesk** via Google Fonts.
- **Mobile-First Responsive Layout**: Progressive enhancement across mobile (default), tablet (`min-width: 641px`), and desktop (`min-width: 1024px`), complete with an accessible slide-out mobile navigation drawer (`#navToggle`, `#navDrawer`).
- **Hero Video & Animated World Route Map**:
  - Full-bleed looping WebM port timelapse (`assets/hamburg-timelapse-test.webm`) with poster fallback (`assets/hamburg-timelapse-test-poster.jpg`).
  - Masked two-line headline animation and an interactive-style SVG route overlay layered over `assets/world-map.svg` with 6 animated great-circle route arcs and 8 pulsing global hub nodes.
- **Asymmetric Capabilities Mosaic (`#features`)**: 7-tile layout combining service summaries, KPI highlights, and scroll-animated photography tiles (`.photo-drift`).
- **Interactive Freight Operations Pipeline (`#how`)**: Scenario switcher (`#howVisualizer`) toggling between *High-tech electronics*, *Pharma cold-chain*, and *Automotive assembly* across three operational stages (**Collect**, **Consolidate**, **Deliver**) with dynamic manifest lists, container load bars, and terminal dispatch statuses.
- **Simulated Shipment Tracker (`#tracker`)**: Interactive tracking lookup (`#trackForm`) with input validation (minimum 6 characters), deterministic demo route matching, and an animated 7-step milestone pipeline (vertical timeline on mobile, horizontal stepped progress bar on tablet/desktop).
- **Network Stats & Scroll Counters (`#stats`)**: Split photo/metric mosaic and 4-column numeric roll-up counters triggered once via `IntersectionObserver`.
- **Lane Rate Estimator & Lead Capture (`#quote`)**: Client-side freight cost calculator (`#estForm`) supporting *Air freight*, *Ocean FCL*, *Ocean LCL*, and *Ground trucking* modes, paired with a validated inline quote conversion form (`#leadSubmit`).
- **Accessibility & Reduced Motion**: Semantic landmarks, `aria-expanded` / `aria-controls` attributes, `:focus-visible` outlines, and full `prefers-reduced-motion: reduce` support (pauses hero video playback and disables entrance/hover motion).

---

## Project Structure

```text
.
├── index.html          # Complete single-page template (HTML, CSS tokens/styles, Vanilla JS)
├── package.json        # Lists dotted-map (^3.1.0) utility dependency (not needed at runtime)
├── package-lock.json
└── assets/
    ├── credits.json                                       # Attribution & license metadata for bundled media
    ├── world-map.svg                                      # Dotted world map background SVG (158x80 viewBox)
    ├── hamburg-timelapse-test.webm                        # Hero timelapse video (854x480)
    ├── hamburg-timelapse-test-poster.jpg                  # Hero video poster frame
    ├── singapore-port-panorama.jpg                        # Capabilities mosaic image (1920x354)
    ├── maersk-hanoi-container-ship-port-koper-sikop.jpg   # Capabilities mosaic image (1920x1439)
    ├── port-of-singapore-keppel-terminal.jpg              # Stats & CTA strip image (1920x1440)
    ├── the-new-container-ship-oocl-singapore-on.jpg       # CTA strip image (1920x1522)
    ├── arabistan-wa-bahr-ahmar-arabian-peninsula-and.jpg  # CTA strip archival map image (1920x1614)
    └── air-cargo-freighter-loading.jpg                    # Extra freight image included in assets/ (unused in index.html)
```

---

## Quick Start

Because no build step or bundler is required, you can preview the site directly with any local static server:

```bash
# Option 1: Node.js (one-liner)
npx serve .

# Option 2: Python 3
python -m http.server 8000
```

Or open `index.html` with the **Live Server** extension in VS Code.

> **Note:** Running `npm install` is **not** required to run or deploy the website. `package.json` only includes `dotted-map` (`^3.1.0`) in case you want to regenerate or restyle `assets/world-map.svg`.

---

## Customization Guide

All customization can be done directly in [`index.html`](index.html):

### 1. Colors, Typography & Spacing Tokens

Edit the CSS custom properties at the top of `<style>` in `index.html`:

```css
:root {
  --bg: #ffffff;
  --surface: #f4f4f4;
  --ink: #111111;
  --muted: #6b6b6b;
  --accent: #1a4be0;
  --accent-ink: #ffffff;
  --field: #111111;
  --field-ink: #ffffff;
  --ts: 1rem;
  --tb: clamp(1.0625rem, 1rem + .25vw, 1.1875rem);
  --th: clamp(2rem, 1.3rem + 3.2vw, 4rem);
  --td: clamp(5.5rem, 9.8vw, 9.375rem);
}
```

- **Accent color**: Change `--accent` (`#1a4be0`) to rebrand buttons, highlights, active pipeline nodes, and SVG route lines. Note that `.world-map-svg` also uses `#1a4be0` inline in its SVG `<stop>`, `<path>`, and `<circle>` attributes—update those inline hex values to match if you change `--accent`.
- **Font family**: Replace the Google Fonts `<link>` in `<head>` and update `font-family` on `body`.

### 2. Brand Copy, Contact Details & Links

Search `index.html` and replace placeholder brand details with your own:

- `<title>` and `<meta name="description">` in `<head>`
- Header `.wordmark` (`APEX LOGISTICS`)
- CTA email link (`mailto:quotes@apex-logistics.example`)
- Footer `.footer-name` (`APEX`), contact info (`hello@apex-logistics.example`, `+65 6000 0000`, `12 Marina Boulevard, Singapore`), copyright line, and placeholder `#` links under **Primary Gateways**, **Company**, and **Resources**.

### 3. Hero Video & Animated Route Map

- **Hero video**: Swap `assets/hamburg-timelapse-test.webm` and `assets/hamburg-timelapse-test-poster.jpg` inside `.hero-media` (consider adding an MP4 `<source>` alongside WebM if broad Safari/older iOS compatibility is required).
- **World map & routes**: Inside `.world-map-svg` (`viewBox="0 0 800 400"`), each lane consists of a base `<path>` and an animated `.aceternity-arc` `<path>`, paired with pulsing hub `<g transform="translate(x, y)">` markers. Adjust coordinates to highlight your own shipping corridors.

### 4. Operations Pipeline Scenarios (`#howVisualizer`)

In the inline `<script>`, the `scenarios` object defines the three interactive freight streams (`electronics`, `pharma`, `automotive`). Update the `stream`, `manifests`, `container`, and `dispatches` fields to reflect your verticals.

> **Implementation note:** `renderScenario(key)` maps the container load-bar labels (`PVG`, `SIN`, `HAM` vs. `FRA`, `BSL`, `AMS` vs. `MUC`, `PUS`, `NGO`) based on `key`. If you rename scenario keys or container origin codes, update those conditional labels inside `renderScenario()` as well.

### 5. Connecting Live APIs (Demo Behavior Notice)

By default, the interactive forms operate entirely client-side for demonstration purposes:

- **Shipment Tracker (`doTrack(ref)`)**: Validates that the input is at least 6 characters, hashes the reference string (`hashCode(ref)`) to pick one of 4 sample lanes, and animates progress along the 7 stages in `stepsDef`. Replace `doTrack()` with a `fetch()` request to your tracking endpoint.
- **Rate Estimator & Quote Lead Form (`#estForm` / `#leadSubmit`)**: Calculates an indicative price from the `rates` object (`air`, `ocean`, `lcl`, `road`) using `base + perKg * weight`, then validates name/email client-side and displays `#leadOk`. Wire `#leadSubmit` to your backend API, CRM webhook, or form service (such as Formspree or Netlify Forms) to capture real leads.

---

## Deployment

Upload `index.html` and the `assets/` folder to any static hosting provider:

- **Netlify / Vercel / Cloudflare Pages**: Deploy the repository root directly with no build command and output directory set to `.`.
- **GitHub Pages**: Serve directly from the `main` branch root.
- **Traditional Hosting (Nginx / Apache / S3)**: Copy `index.html` and `assets/` to your web root while preserving the relative `assets/...` paths.

---

## Bundled Media & Attribution

Sample photos and video in [`assets/`](assets/) are sourced from Wikimedia Commons and documented in [`assets/credits.json`](assets/credits.json) as well as the footer `.credits` block of [`index.html`](index.html):

| File | License | Attribution Required |
| --- | --- | --- |
| `singapore-port-panorama.jpg` | CC BY-SA 3.0 | Yes (`Kroisenbrunner`) |
| `port-of-singapore-keppel-terminal.jpg` | CC BY-SA 2.5 | Yes (`Calvin Teo`) |
| `maersk-hanoi-container-ship-port-koper-sikop.jpg` | CC BY-SA 4.0 | Yes (`Petar Milošević`) |
| `the-new-container-ship-oocl-singapore-on.jpg` | CC BY-SA 3.0 | Yes (`Buonasera`) |
| `hamburg-timelapse-test.webm` | CC BY 3.0 | Yes (`Christian Andersen`) |
| `arabistan-wa-bahr-ahmar-arabian-peninsula-and.jpg` | Public Domain | No |

- **If you keep the bundled Wikimedia Commons media**: Retain the attribution links in the footer and follow Share-Alike (`CC BY-SA`) terms if you alter or remix those photographs.
- **If you publish a commercial client site**: We recommend replacing the sample images and video in `assets/` with your own licensed photography/footage and removing the unused sample files.

---

## Template License

> **Seller Note:** Add your chosen template license terms here (for example, Standard / Commercial Single-Site License, Extended License, or MIT) along with support contact details before publishing your template package.

