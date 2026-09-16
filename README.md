# WEDE_POE_-PART-2-ST10442162 (Mpshadi Mahlatse Mokabane)
#  Brew & Bean Artisan Coffee — Project README

A warm, community-focused website for **Brew & Bean Artisan Coffee**, a fictional artisan coffee shop founded in 2018. This project showcases a fully responsive, multi-page café website with a consistent design system, soft coffee-inspired colour palette, embedded Google Map, and interactive menu filtering.

---

##  Project Structure

```
brewandbean/
│
├── index.html          # Homepage – hero, mission highlights
├── menu.html           # Menu page – filterable coffee, tea & food items
├── about.html          # About Us – story, mission, vision, gallery
├── events.html         # Events & Workshops – calendar + enquiry CTA
├── contact.html        # Contact & Enquiries – form, map, newsletter
│
├── style.css           # Main external stylesheet (global styles)
├── script.js           # JavaScript (menu filter, mobile nav, active states)
│
└── README.md           # This file
```

>  **Note:** There are also two standalone/experimental files — `CSS Style.html` (self-contained demo with inline styles + map embed) and `menu (2).html` (menu page with inline styles). The production pages above use `style.css` + `script.js`.

---

##  Design System

### Colour Palette

| Name | Hex | Usage |
|------|-----|-------|
| Cream | `#faf7f2` | Base page background |
| Latte | `#f3ede4` | Alt sections, hero background |
| Warm Beige | `#ece4d9` | Page heroes, event date badges |
| Coffee Tint | `#e8dfd3` | Events section, tags |
| Soft White | `#fffcf9` | Cards, menu panels |
| Espresso Brown | `#2c221c` | Footer, body text |
| Coffee Accent | `#b45f3b` | Buttons, links, eyebrows, prices |
| Muted Brown | `#4f3d32` | Secondary body text |
| Border Sand | `#ddd1c2` | Inputs, dividers |

### Typography

- **Font:** [Inter](https://fonts.google.com/specimen/Inter) (weights 400–700) via Google Fonts
- Headings use tight letter-spacing (`-0.02em` to `-0.03em`)
- Body text uses a warm brown (`#4f3d32`) for readability on cream backgrounds

### Backgrounds

Every major section is assigned a distinct soft background colour to create visual rhythm and separation:
- `.bg-cream` — base sections
- `.bg-latte` — hero + alternate sections
- `.bg-warm-beige` — page heroes / menu
- `.bg-coffee-tint` — events
- `.bg-soft-white` — cards

---

## Page Breakdown

### `index.html` — Home
- **Hero:** "Good coffee. Great community." with two CTAs (Explore menu / See events)
- **Why Brew & Bean:** Three feature cards — Ethical sourcing , Community first , Made for the moment 
- `data-page="home"` on `<body>` for active nav highlighting

### `menu.html` — Menu
- Filter buttons: **All · Coffee & Espresso · Tea · Food · Seasonal**
- Menu items with thumbnail images, tags (`VG` vegan, `V` vegetarian), and prices in ZAR (R)
- Items marked with `data-cat` attributes for JavaScript filtering
- Prices: R28 – R55

### `about.html` — About Us
- Story of founders **Mia & James Peterson** (est. 2018 farmers' market cart → 2020 brick-and-mortar)
- **Mission** & **Vision** cards
- Quote block with brand statement
- 3-image gallery of the café interior

### `events.html` — Events & Workshops
- Four upcoming events with date badges:
  - **18 SEP** — Single-Origin Coffee Tasting
  - **26 SEP** — Latte Art Workshop
  - **10 OCT** — Community Coffee Morning
  - **24 OCT** — Sustainability Talk
- CTA section linking to contact form for bookings

### `contact.html` — Contact & Enquiries
- Visit info card (address, hours, phone, email)
- **Embedded Google Map** (Cape Town City Centre) using responsive `iframe`
- Enquiry form with fields: Name, Email, Enquiry Type, Message
- Newsletter subscription section

---

##  Map Integration

The contact page (`contact.html`) includes a live **Google Maps embed**:

```html
<iframe
  src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3308.68...
       !2sCape%20Town%20City%20Centre..."
  allowfullscreen=""
  loading="lazy"
  referrerpolicy="no-referrer-when-downgrade"
  title="Brew & Bean location on Google Maps">
</iframe>
```

Styled with `.map-wrapper` (rounded corners, shadow, responsive height 200–240px).

>  **To update the location:** Replace the `src` URL with your own address using [Google Maps → Share → Embed a map](https://www.google.com/maps).

---

## ⚙️ JavaScript Features (`script.js`)

| Feature | Description |
|---------|-------------|
| **Mobile menu toggle** | ☰ button opens/closes nav on screens < 700px |
| **Menu filtering** | Click category buttons to filter `.menu-item` elements by `data-cat` |
| **Active nav state** | Reads `body[data-page]` and highlights matching nav link |

Example filtering logic:
```js
filterBtn.addEventListener('click', () => {
  const cat = filterBtn.dataset.cat;
  document.querySelectorAll('.menu-item').forEach(item => {
    item.style.display = (cat === 'all' || item.dataset.cat === cat) ? 'block' : 'none';
  });
});
```

---

## Responsive Design

| Breakpoint | Behaviour |
|------------|-----------|
| **≤ 900px** | Grids drop from 3 → 2 columns; gallery 3 → 2 columns; hero text shrinks |
| **≤ 700px** | Hamburger nav activates; all grids → 1 column; gallery → 1 column; menu thumbnails shrink to 70px; map height reduces to 200px |

Grid system:
```css
.grid-2 { grid-template-columns: 1fr 1fr; }
.grid-3 { grid-template-columns: repeat(3, 1fr); }
/* collapses to 1fr on mobile */
```

---

##  Reusable Components

- **`.card`** — rounded white container with soft shadow + hover lift
- **`.btn-primary`** / **`.btn-secondary`** — pill-shaped CTAs in coffee accent
- **`.tag`** — small pill badges (VG / V / spaces left)
- **`.eyebrow`** — uppercase accent label above headings
- **`.quote`** — left-bordered italic callout
- **`.date`** — event date badge with large day number
- **`.menu-photo`** — circular-ish thumbnail with `object-fit: cover`

---

Getting Started

1. **Clone / download** the project folder.
2. Ensure all files are in the same directory:
   ```
   index.html, menu.html, about.html, events.html, contact.html,
   style.css, script.js
   ```
3. Open `index.html` in any modern browser — no build step required.
4. For live preview with auto-reload, use VS Code + **Live Server** extension.

---

 Customisation Guide

| Want to change… | Edit… |
|-----------------|-------|
| Brand colours | `:root` variables or hex values in `style.css` |
| Menu items / prices | `menu.html` (add `.menu-item` blocks with `data-cat`) |
| Events | `events.html` (duplicate `.card.event` articles) |
| Address & map | `contact.html` — visit card text + `iframe` `src` |
| Social links | Footer sections across all pages |
| Opening hours | Footer + contact page visit card |

---

Browser Support

-  Chrome / Edge (latest)
-  Firefox (latest)
-  Safari (latest, including iOS)
- Mobile browsers (responsive down to 320px)

Uses `backdrop-filter` (header blur) — gracefully degrades on older browsers.

---

Known Notes

- The **footer on `index.html`** is intentionally left as a placeholder comment (`<!-- Footer content -->`) — copy the footer block from any other page to complete it.
- Placeholder contact details (`+27 00 000 0000`, `hello@brewandbeancoffee.com`, "Your local neighbourhood café") should be replaced with real business info before publishing.
- Images are loaded from **Unsplash** — replace with licensed/own photography for production.

---


---

**© 2026 Brew & Bean Artisan Coffee. Crafted with care.** ☕
