# Color & Theme Reference — Human Web Design

## The Problem with AI Color

AI tools gravitate toward purple-to-blue gradients because they appear most frequently in SaaS
landing pages. The result is thousands of sites with identical color energy. Breaking free from
this means committing to a specific mood, not a "safe" palette.

---

## Color Strategy: Dominant + Accent

Instead of 5 equal colors, structure your palette as:

- **1 Dominant color** — used on 60-70% of colored elements
- **1 Sharp accent** — used sparingly for CTAs, highlights, key interactions
- **Neutrals** — warm or cool, but never pure black/white
- **Optional supporting color** — used for secondary UI states only

### Example: Warm Earth Palette
```css
:root {
  --dominant: #C45D2C;        /* burnt sienna — hero, headings */
  --accent: #2D5A3D;          /* forest green — CTAs, links */
  --neutral-bg: #FAF7F2;      /* warm cream — background */
  --neutral-text: #2C2520;    /* warm dark brown — body text */
  --neutral-muted: #9B8E82;   /* warm gray — secondary text */
  --border: rgba(44, 37, 32, 0.1);
}
```

### Example: Cool Night Palette
```css
:root {
  --dominant: #1B2838;         /* deep navy — backgrounds, headers */
  --accent: #FF6B35;           /* vibrant orange — CTAs, highlights */
  --neutral-bg: #0F1923;       /* near-black blue — dark mode bg */
  --neutral-text: #E8E0D6;    /* warm off-white — body text */
  --neutral-muted: #6B7C8F;   /* slate blue — secondary text */
  --border: rgba(232, 224, 214, 0.1);
}
```

### Example: Monochrome + Pop
```css
:root {
  --dominant: #1A1A1A;         /* near-black — everything */
  --accent: #E63946;           /* vivid red — single pop color */
  --neutral-bg: #FAFAF8;      /* warm white */
  --neutral-text: #1A1A1A;
  --neutral-muted: #888888;
  --border: rgba(0, 0, 0, 0.06);
}
```

### Example: Muted Pastel (Warm)
```css
:root {
  --dominant: #D4A574;         /* soft caramel */
  --accent: #7B6BA3;           /* dusty purple (NOT the gradient kind) */
  --neutral-bg: #FDF8F3;      /* creamy white */
  --neutral-text: #3D3428;    /* warm espresso */
  --neutral-muted: #A89B8C;
  --border: rgba(61, 52, 40, 0.08);
}
```

### Example: Bold Contrast (Dark)
```css
:root {
  --dominant: #0A0A0A;         /* true dark */
  --accent: #C8FF00;           /* electric lime */
  --neutral-bg: #0A0A0A;
  --neutral-text: #F5F5F0;
  --neutral-muted: #666666;
  --border: rgba(255, 255, 255, 0.08);
}
```

---

## Neutrals: Never Pure

The biggest tell of AI-generated design is pure #FFFFFF backgrounds with pure #000000 text.
Real designers warm or cool their neutrals.

### Warm Neutrals
```css
--white: #FAFAF8;    /* slight yellow warmth */
--light: #F5F2EB;    /* cream */
--medium: #E8E3D9;   /* sand */
--dark: #2C2520;     /* warm near-black */
--black: #1A1714;    /* chocolate black */
```

### Cool Neutrals
```css
--white: #F8F9FC;    /* slight blue cool */
--light: #EEF0F6;    /* lavender gray */
--medium: #D5D9E2;   /* steel */
--dark: #1E2128;     /* cool near-black */
--black: #12141A;    /* midnight */
```

---

## Gradient Rules (When You Must Use Them)

Gradients aren't banned — just the generic ones. If you use a gradient, follow these rules:

1. **Avoid purple-to-blue** — it's the single most overused AI pattern
2. **Use subtle gradients** — small color shifts, not dramatic rainbow sweeps
3. **Limit to backgrounds** — don't put gradients on buttons (use solid accent instead)
4. **Try non-obvious combos:**

```css
/* Subtle warm gradient — barely noticeable but adds depth */
background: linear-gradient(160deg, #FAF7F2 0%, #F2EDE4 50%, #F8F0E8 100%);

/* Dark mode ambient glow */
background: radial-gradient(ellipse at 20% 50%, rgba(200, 80, 40, 0.08) 0%, transparent 60%),
            radial-gradient(ellipse at 80% 20%, rgba(40, 80, 160, 0.05) 0%, transparent 50%),
            #0A0A0A;

/* Mesh-like subtle gradient */
background: conic-gradient(from 45deg at 40% 60%, #FAF7F2, #F0EBE0, #F5F0E8, #FAF7F2);
```

---

## Themed Design Approaches

Instead of "pick nice colors," commit to a theme. This forces unique choices.

### Solarpunk
- Greens, golds, warm earth tones
- Organic shapes + technical grid contrast
- Nature-inspired textures (leaf patterns, wood grain)
- Optimistic, future-positive mood

### Tokyo Night
- Deep navies, electric neons (cyan, magenta, yellow-green)
- High contrast: very dark backgrounds with glowing accents
- Monospace typography emphasis
- Urban, technical, developer-friendly

### Scandinavian
- Muted sage greens, pale blues, warm beiges
- Lots of white space with sparse, intentional color
- Minimal decoration, maximum clarity
- Clean, calm, functional

### Vintage / Retro
- Desaturated warm tones: mustard, rust, olive, burgundy
- Paper-like backgrounds with subtle grain texture
- Serif or slab-serif typography
- Nostalgic, crafted, artisanal feel

### Brutalist
- Raw primary colors or strict monochrome
- High contrast borders, no gradients
- System fonts or deliberately ugly choices
- Honest, anti-design, functional

---

## Dark Mode — Do It Right

Dark mode isn't just inverting colors. Common AI mistakes in dark mode:

- Pure black (#000000) backgrounds — too harsh. Use #0A0A0A to #141414
- White text on dark — use slightly warm off-white (#F5F2EB, #E8E0D6)
- Keeping the same accent color — often needs to be lighter/brighter in dark mode
- Flat dark backgrounds — add subtle texture or ambient color glow

```css
/* Good dark mode foundation */
[data-theme="dark"] {
  --color-bg: #0D0D0C;
  --color-bg-elevated: #1A1918;
  --color-bg-hover: #242320;
  --color-text: #E8E3D9;
  --color-text-muted: #8A8278;
  --color-primary: #E8734A;       /* slightly lighter than light mode */
  --color-accent: #4CAF6E;        /* brighter green for visibility */
  --color-border: rgba(232, 227, 217, 0.08);
}
```

---

## Color Accessibility Quick Check

Regardless of aesthetic choices, ensure:
- Body text contrast ratio: minimum 4.5:1 against background
- Large text (24px+): minimum 3:1
- Interactive elements: clearly distinguishable from non-interactive
- Don't rely on color alone to convey meaning
