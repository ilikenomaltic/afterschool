# Typography Reference — Human Web Design

## Why Typography is the #1 Differentiator

AI tools default to Inter because it's the most statistically "safe" choice. The moment you replace
Inter with a typeface that carries personality, your site stops looking AI-generated. Typography is
the single fastest way to escape AI slop.

---

## Font Pairing Recipes

Each recipe below is a tested combination. Pick one and customize from there.

### 1. Editorial / Magazine Feel
- **Display:** Playfair Display (serif, elegant)
- **Body:** Source Sans 3 (clean, readable)
- **Accent:** JetBrains Mono (for labels, metadata)
- **Vibe:** Sophisticated, content-driven, timeless

### 2. Modern Tech / Startup
- **Display:** Space Grotesk (geometric, distinctive)
- **Body:** IBM Plex Sans (humanist, professional)
- **Accent:** IBM Plex Mono (technical details)
- **Vibe:** Smart, clean, but not generic

### 3. Bold / Creative Agency
- **Display:** Clash Display (strong, opinionated)
- **Body:** Satoshi (contemporary, friendly)
- **Accent:** Space Mono (contrast)
- **Vibe:** Confident, creative, memorable

### 4. Warm / Approachable
- **Display:** Fraunces (organic, quirky serif)
- **Body:** Cabinet Grotesk (warm geometric)
- **Accent:** Fira Code (playful mono)
- **Vibe:** Human, friendly, personal

### 5. Minimal / Luxury
- **Display:** Cormorant Garamond (refined serif)
- **Body:** Outfit (modern geometric)
- **Accent:** DM Mono (subtle technical)
- **Vibe:** Elegant, restrained, premium

### 6. Brutalist / Experimental
- **Display:** Bricolage Grotesque (variable, expressive)
- **Body:** Work Sans (solid, grounded)
- **Accent:** Courier Prime (raw, typewriter)
- **Vibe:** Raw, intentional, anti-corporate

---

## Korean (한글) Font Recommendations

Don't default to Pretendard for everything. Match your English display font mood.

### For Modern / Clean Projects
- **Wanted Sans** — contemporary, sharp, great for tech
- **SUIT** — versatile, slightly warmer than Pretendard
- **Pretendard** — only if paired with distinctive English display font

### For Warm / Friendly Projects
- **Noto Sans KR** (weight 300-400) — soft, approachable
- **Spoqa Han Sans Neo** — rounded, friendly
- **KoPubWorld Dotum** — warm, official but not cold

### For Editorial / Premium Projects
- **Noto Serif KR** — elegant, editorial, great for long-form content
- **KoPubWorld Batang** — traditional, refined, literary feel
- **Maruburi** — unique, modern serif with Korean character

### Loading Strategy
```html
<!-- Preload Korean fonts for performance -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://cdn.jsdelivr.net" crossorigin>

<!-- Example: Wanted Sans + Space Grotesk combo -->
<link href="https://cdn.jsdelivr.net/gh/niceplugin/Wanted-Sans@main/packages/wanted-sans/fonts/webfonts/variable/split/WantedSansVariable.min.css" rel="stylesheet">
```

---

## Size Scale — Dramatic Contrasts

AI tools generate timid size scales. Use dramatic jumps instead.

### Bad (AI default — too timid):
```css
/* DON'T — every step is barely noticeable */
h1 { font-size: 2rem; }      /* 32px */
h2 { font-size: 1.5rem; }    /* 24px */
h3 { font-size: 1.25rem; }   /* 20px */
body { font-size: 1rem; }    /* 16px */
```

### Good (dramatic, intentional):
```css
/* DO — clear visual hierarchy */
.display { font-size: clamp(3rem, 8vw, 6rem); font-weight: 900; letter-spacing: -0.03em; }
h1 { font-size: clamp(2.5rem, 5vw, 4rem); font-weight: 800; letter-spacing: -0.02em; }
h2 { font-size: clamp(1.75rem, 3vw, 2.5rem); font-weight: 700; }
h3 { font-size: 1.25rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.05em; }
body { font-size: 1.125rem; font-weight: 400; line-height: 1.7; }
small { font-size: 0.8rem; font-weight: 500; letter-spacing: 0.02em; }
```

### The Rule of 3x
Between your smallest and largest text, aim for at least a 3x size difference.
- Body: 18px → Display: 64px+ (3.5x ratio)
- Not: Body: 16px → Display: 32px (only 2x — too flat)

---

## Weight Pairing

Use extreme weight contrasts to create visual drama.

```css
/* Thin vs Heavy pairing */
.hero-subtitle {
  font-weight: 200;       /* ultra light */
  font-size: 1.5rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.hero-title {
  font-weight: 900;       /* ultra heavy */
  font-size: clamp(3rem, 8vw, 6rem);
  letter-spacing: -0.03em;
  line-height: 0.95;
}
```

The contrast between 200 and 900 weight creates visual tension that no AI default will generate.

---

## Letter-Spacing Rules

- **Large display text (>40px):** Tighten letter-spacing (-0.02em to -0.04em)
- **Body text:** Leave at default or slightly open (0 to 0.01em)
- **Small caps / labels:** Open up (0.05em to 0.1em)
- **Uppercase text:** Always add letter-spacing (0.04em to 0.1em)

AI tools almost never adjust letter-spacing. This alone adds a "designed" feel.

---

## Line Height Guide

- **Display/hero text:** 0.9 - 1.0 (tight, dramatic)
- **Headings:** 1.1 - 1.3 (compact but readable)
- **Body text:** 1.6 - 1.8 (comfortable reading)
- **Korean body text:** 1.7 - 1.9 (slightly more room for 한글 character density)

---

## Variable Fonts — The Power Move

Variable fonts give you infinite weight/width options from a single file.
Use them for smooth hover transitions and responsive weight changes.

```css
@font-face {
  font-family: 'Space Grotesk';
  src: url('SpaceGrotesk-Variable.woff2') format('woff2');
  font-weight: 300 700;
}

.nav-link {
  font-variation-settings: 'wght' 400;
  transition: font-variation-settings 0.3s var(--ease-out-expo);
}

.nav-link:hover {
  font-variation-settings: 'wght' 700;
}
```

This creates a smooth weight transition on hover that feels incredibly polished.
