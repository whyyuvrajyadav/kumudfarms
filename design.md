# KUMUD Farms — Design System & Style Guide

This document defines the complete visual and architectural design system for **KUMUD Farms** (`kumudfarms.in`), established from the homepage layout redesign. Every page on the website adheres to this design specification to ensure a coherent, premium, and trustworthy user experience.

---

## 1. Brand Philosophy & Identity

- **Essence:** Small-batch, pure desi buffalo ghee handmade from fresh cream on our family dairy farm in Lucknow.
- **Tone:** Honest, rooted, artisanal, premium yet welcoming.
- **Visual Motif:** Traditional Indian dairy heritage blended with modern editorial craftsmanship. Arch curves, warm cream paper textures, deep farm greens, and celebratory gold accents.
- **Lotus Symbol:** *Kumud* is the Sanskrit word for the night-blooming water lily / lotus. The lotus petals icon in `#C8A24A` is the official brand mark.

---

## 2. Color Palette & Tokens

All colors are declared as CSS variables on `:root`:

```css
:root {
  /* Brand Core */
  --forest:   #1F3D2B; /* Primary Brand Forest Green */
  --deep:     #142A1E; /* Header / Footer Deep Night Green */
  --gold:     #C8A24A; /* Warm Harvest Gold Accent */
  --gold-lt:  #E8D49A; /* Light Gold for Hover / Subheads */

  /* Neutrals & Surfaces */
  --cream:    #F7F1E1; /* Secondary Warm Cream Surface */
  --paper:    #FFFCF4; /* Primary Page Background */
  --ink:      #1B241E; /* High-contrast Body Slate Text */
  --mute:     #55604F; /* Secondary / Caption / Meta Text */

  /* Legacy Aliases */
  --g: var(--forest);
  --d: var(--deep);
  --o: var(--gold);
  --c: var(--cream);
  --p: var(--paper);
  --i: var(--ink);

  /* Typography */
  --serif: "Young Serif", Georgia, serif;
  --sans:  "Hind", system-ui, -apple-system, "Segoe UI", sans-serif;
}
```

### Color Usage Guidelines:
| Color | Hex | Role / Application |
|---|---|---|
| **Deep Green** | `#142A1E` | Sticky header background, footer background, dark containers (`.made`) |
| **Forest Green** | `#1F3D2B` | Hero section, review carousel, dark buttons, primary accents |
| **Warm Gold** | `#C8A24A` | Brand logo mark, primary CTA button, active borders, arch borders, stars |
| **Light Gold** | `#E8D49A` | CTA hover states, subheadings over dark backgrounds |
| **Cream** | `#F7F1E1` | Secondary alternating section backgrounds (`.sizes`, `.say`), tag pills |
| **Paper** | `#FFFCF4` | Primary page canvas background |
| **Ink** | `#1B241E` | Primary body typography for high legibility |
| **Mute** | `#55604F` | Subtitles, specifications, metadata, breadcrumbs |

---

## 3. Typography

Fonts are imported from Google Fonts on every page:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Hind:wght@400;500;600&family=Young+Serif&display=swap" rel="stylesheet">
```

### Type Hierarchy:
- **Display Headings (`h1`):** `font-family: var(--serif); font-size: clamp(2.1rem, 5.5vw, 3.6rem); line-height: 1.15;`
- **Section Headings (`h2`):** `font-family: var(--serif); font-size: clamp(1.6rem, 3.6vw, 2.4rem); line-height: 1.2;`
- **Sub-headings (`h3`):** `font-family: var(--serif); font-size: 1.2rem;`
- **Body (`p`, `li`, `dd`):** `font-family: var(--sans); font-size: 1.0625rem (17px); line-height: 1.65; max-width: 62ch;`
- **Meta / Notes (`small`, `.mute`):** `font-size: 0.9rem; color: var(--mute);`

---

## 4. Layout & Container System

- **Max Width Container (`.wrap` / `.w`):**
  ```css
  .wrap, .w {
    width: min(1120px, 100% - 2.5rem);
    margin-inline: auto;
  }
  ```
- **Section Spacing:**
  ```css
  section {
    padding: clamp(3rem, 7vw, 5.5rem) 0;
  }
  ```
- **Alternating Section Surfaces:**
  - Default: Light paper `--paper` (`#FFFCF4`)
  - Alternating Band: Cream `--cream` (`#F7F1E1`) or Dark Forest `--forest` (`#1F3D2B`) / Deep `--deep` (`#142A1E`)

---

## 5. Header & Navigation System

Every page shares the unified sticky dark header:

```html
<header>
  <div class="wrap">
    <a class="logo" href="index.html" aria-label="KUMUD home">
      <svg width="30" height="30" viewBox="0 0 40 40" fill="#C8A24A" aria-hidden="true">
        <ellipse cx="20" cy="14" rx="5" ry="11"/>
        <ellipse cx="20" cy="14" rx="5" ry="11" transform="rotate(-38 20 32)"/>
        <ellipse cx="20" cy="14" rx="5" ry="11" transform="rotate(38 20 32)"/>
        <ellipse cx="20" cy="14" rx="5" ry="11" transform="rotate(-72 20 32)" opacity=".6"/>
        <ellipse cx="20" cy="14" rx="5" ry="11" transform="rotate(72 20 32)" opacity=".6"/>
      </svg>
      KUMUD
    </a>
    <nav aria-label="Main">
      <a href="product.html">Products</a>
      <a href="about.html">Our story</a>
      <a href="blog.html">Journal</a>
      <a href="https://review.kumudfarms.in/" target="_blank" rel="noopener">Reviews</a>
      <a href="contact.html">Contact</a>
    </nav>
    <a class="btn gold" href="https://wa.me/917318023488?text=Hi%20KUMUD%2C%20I%20would%20like%20to%20order%20ghee" target="_blank" rel="noopener">Order on WhatsApp</a>
  </div>
</header>
```

---

## 6. Buttons & Interactive Elements

```css
.btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: .75rem 1.4rem;
  border-radius: 999px;
  font-weight: 600;
  font-size: 1rem;
  text-decoration: none;
  border: 2px solid var(--gold);
  transition: all .2s ease;
  cursor: pointer;
}
.btn.gold {
  background: var(--gold);
  color: var(--deep);
  border-color: var(--gold);
}
.btn.gold:hover {
  background: var(--gold-lt);
  border-color: var(--gold-lt);
  transform: translateY(-1px);
}
.btn.dark {
  border-color: var(--forest);
  color: var(--forest);
  background: transparent;
}
.btn.dark:hover {
  background: var(--forest);
  color: var(--cream);
  transform: translateY(-1px);
}
.btn.line {
  color: var(--cream);
  border-color: var(--gold-lt);
  background: transparent;
}
.btn.line:hover {
  background: rgba(255,255,255,.1);
}
```

---

## 7. Signature Visual Elements

1. **Arch Containers (`.arch`):**
   - Top rounded arch `border-radius: 999px 999px 14px 14px;` with gold border `border: 2px solid var(--gold);`.
2. **Arch Photo Tiles (`.tile`):**
   - `aspect-ratio: 3/4; border-radius: 999px 999px 10px 10px; border: 2px solid var(--gold);` with dark gradient overlay and centered cream text.
3. **Numbered Process List (`.made ol`):**
   - 4-column numbered steps with gold counters `content: counter(s); font: 1.8rem var(--serif); color: var(--gold);`.
4. **FAQ Accordion (`.faq details`):**
   - Clean summary with gold `+` / `–` indicators.
5. **Customer Reviews Continuous Marquee (`.reviews-section`):**
   - Dark green background `#1F3D2B`, gold quote marks, 5.0 Google Badge, and continuous infinite auto-scrolling marquee across all devices.
   - Pauses on desktop hover and mobile touch so customers can read comfortably.
   - Every review card is clickable and redirects to Google Reviews (`https://review.kumudfarms.in/`) in a new tab.

---

## 8. Footer Specification

Unified 3-column dark footer on every page:

```html
<footer>
  <div class="wrap">
    <div>
      <h3>KUMUD Farms</h3>
      <p>Small-batch desi buffalo ghee, handmade from fresh cream on our family dairy farm in Lucknow.</p>
      <a href="mailto:info@kumudfarms.in">info@kumudfarms.in</a>
      <a href="tel:+917318023488">+91 73180 23488</a>
      <span>Lucknow, Uttar Pradesh</span>
    </div>
    <div>
      <h3>Explore</h3>
      <a href="product.html">Products</a>
      <a href="about.html">Our story</a>
      <a href="blog.html">Journal</a>
      <a href="https://review.kumudfarms.in/" target="_blank" rel="noopener">Reviews</a>
      <a href="contact.html">Contact</a>
    </div>
    <div>
      <h3>Follow</h3>
      <a href="https://www.instagram.com/kumudfarms" target="_blank" rel="noopener">Instagram</a>
      <a href="https://www.facebook.com/kumudfarms" target="_blank" rel="noopener">Facebook</a>
      <a href="https://www.youtube.com/@kumudfarms" target="_blank" rel="noopener">YouTube</a>
      <a href="https://share.google/rSbYHYBCwStKr4CTY" target="_blank" rel="noopener">Find us on Google Maps</a>
    </div>
    <div class="copy">© 2026 KUMUD Farms, Lucknow. All rights reserved. Handcrafted with care in India.</div>
  </div>
</footer>
```

---

## 9. Floating WhatsApp CTA

Included on every page right before `</body>`:

```html
<a class="wa" href="https://wa.me/917318023488?text=Hi%20KUMUD%2C%20I%20would%20like%20to%20order%20ghee" target="_blank" rel="noopener" aria-label="Order on WhatsApp">
  <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
    <path d="M17.472 14.382c-.301-.15-1.78-.878-2.056-.978-.276-.1-.477-.15-.678.15-.2.301-.778.978-.954 1.18-.176.2-.351.226-.653.076-.301-.15-1.272-.469-2.424-1.496-.895-.799-1.5-1.786-1.676-2.087-.176-.301-.019-.464.132-.614.136-.135.301-.351.452-.527.15-.176.2-.301.301-.502.101-.2.05-.376-.025-.526-.075-.15-.678-1.633-.929-2.239-.244-.59-.493-.51-.678-.52l-.578-.01c-.2 0-.527.075-.803.376s-1.054 1.03-1.054 2.51c0 1.48 1.08 2.908 1.23 3.109.15.2 2.126 3.246 5.15 4.553.72.31 1.282.496 1.72.635.723.23 1.381.197 1.902.12.58-.087 1.78-.727 2.03-1.43.25-.704.25-1.307.175-1.432-.075-.125-.276-.2-.577-.35zM12.04 2C6.516 2 2.022 6.478 2.022 12c0 1.848.502 3.654 1.456 5.239L2 22l4.89-1.433A9.972 9.972 0 0 0 12.04 22c5.523 0 10.017-4.478 10.017-10S17.563 2 12.04 2zm0 18.286c-1.597 0-3.158-.42-4.529-1.217l-.325-.188-2.901.85.875-2.813-.21-.334A8.257 8.257 0 0 1 3.766 12c0-4.562 3.712-8.273 8.274-8.273 4.562 0 8.273 3.711 8.273 8.273 0 4.562-3.711 8.286-8.273 8.286z"/>
  </svg>
  WhatsApp us
</a>
```
