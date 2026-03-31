---
name: human-web-design
description: >
  Anti-AI-slop frontend design skill for creating websites that look human-crafted, not machine-generated.
  Use this skill whenever the user asks to create a website, landing page, web app, React component,
  HTML page, portfolio, SaaS landing page, or any frontend UI. Also trigger when the user mentions
  "사이트 만들어줘", "웹사이트", "랜딩페이지", "프론트엔드", "UI 만들어", "홈페이지", "웹 디자인",
  "React", "HTML page", "web design", "landing page", "portfolio site", or any request involving
  frontend code generation (HTML/CSS/JS/React/Vue/Svelte). This skill ensures every generated site
  has distinctive character and avoids the generic "AI slop" aesthetic. MANDATORY for all frontend
  and web design tasks — even simple ones benefit from these principles.
---

# Human Web Design — Anti-AI-Slop Frontend Skill

## Purpose

AI-generated websites share a recognizable "slop" aesthetic: Inter font, purple-blue gradients,
identical card layouts, and cookie-cutter hero sections. This skill exists to break that pattern.
Every site you build should feel like a human designer spent time on it — with intentional choices
in typography, color, layout, motion, and texture.

## The Golden Rule

**Before writing any frontend code, make three intentional design decisions:**

1. **A typeface that isn't Inter/Roboto/Open Sans** — this single choice transforms everything
2. **A color palette with personality** — not the safe purple-blue gradient
3. **One layout choice that breaks the grid** — asymmetry, overlap, unexpected spacing

If you can't articulate these three decisions, you're not ready to write code yet.

---

## Phase 1: Kill the AI Slop — What to NEVER Do

These are the patterns that instantly scream "AI made this." Avoid them all.

### Typography Anti-Patterns
- Inter, Roboto, Open Sans, Lato, Arial, or system-ui as the primary font
- Font weight variations that are too subtle (400 vs 600) — use extreme contrasts (200 vs 900)
- Size jumps that are too small (16px → 20px → 24px) — use dramatic jumps (16px → 32px → 64px)
- Everything in the same font family with no pairing

### Color Anti-Patterns
- Purple-to-blue gradient hero sections (the #1 AI slop signal)
- Evenly distributed rainbow palettes where every color gets equal weight
- Pure white (#FFFFFF) backgrounds with pure black (#000000) text
- Generic blue (#3B82F6) or indigo (#6366F1) as the primary brand color
- Gradient buttons that look like they came from a Tailwind template

### Layout Anti-Patterns
- Hero → 3-column features → testimonials → CTA (the "SaaS template" structure)
- Perfectly centered everything with uniform padding
- Card grids where every card is identical in size and spacing
- Icon-in-circle + title + description repeated 3 or 6 times
- "pill cluster" tag displays, stat strips, icon rows all competing in the first viewport
- The exact same border-radius (rounded-xl) on every single element

### Copy Anti-Patterns
- "Build the future of [X]" / "Your all-in-one platform" / "Scale without limits"
- Headlines that say nothing about the actual product
- Subheadings that just rephrase the heading in more words

### Motion Anti-Patterns
- Identical fade-in-up on every single element
- Hover effects that are purely decorative with no information value
- Scroll-triggered animations on literally everything

---

## Phase 2: Build with Intention — What TO Do

Read the reference files in `references/` for detailed implementation. Below is the high-level strategy.

### Typography — The #1 Differentiator

Typography alone can save a design from looking AI-generated. For detailed font pairing recommendations
and implementation, read `references/typography.md`.

**Quick rules:**
- Pick one distinctive display font and one complementary body font
- Use 3x+ size jumps between heading levels (not 1.5x)
- Use extreme weight contrasts: light (100-300) vs heavy (700-900)
- For Korean (한글): go beyond Pretendard — try SUIT, Wanted Sans, Noto Sans KR with intentional weight choices
- For English display: Space Grotesk, Clash Display, Satoshi, Cabinet Grotesk, Bricolage Grotesque, Fraunces
- For English body: IBM Plex Sans, Source Serif 4, Crimson Pro

### Color — Commit to a Mood

Read `references/color-and-theme.md` for palette recipes and examples.

**Quick rules:**
- Choose ONE dominant color and ONE sharp accent — not five equal colors
- Warm your neutrals: use off-whites (#FAFAF8, #F5F2EB) instead of pure white
- Darken with warm blacks (#1A1A1A, #0D0D0C) instead of #000000
- Desaturate slightly for sophistication — don't use colors at full saturation
- Use CSS custom properties for theme consistency
- Consider an unexpected palette: earth tones, monochromatic, warm pastels, dark mode with colored accents

### Layout — Break the Template

Read `references/layout-patterns.md` for specific techniques.

**Quick rules:**
- The first viewport should read as ONE composition, not a dashboard
- Use asymmetric grids: 2/3 + 1/3, or offset columns
- Overlap elements: text over images, cards breaking out of containers
- Vary spacing intentionally — not everything needs the same padding
- Use negative space as a design element, not just "emptiness"
- Mix full-bleed sections with contained sections
- Consider bento grid, masonry, or editorial magazine layouts

### Motion — Purposeful, Not Decorative

Read `references/motion.md` for animation implementation details.

**Quick rules:**
- Design ONE hero animation sequence well, rather than animating everything
- Use staggered reveals with `animation-delay` for page load
- Hover states should communicate information (not just "I can hover")
- Scroll-triggered effects on max 2-3 key moments, not every section
- CSS-only for HTML; Framer Motion for React
- Easing matters: use custom cubic-bezier curves, not just `ease-in-out`

### Texture & Depth — The Human Touch

**Quick rules:**
- Add subtle background texture: noise overlay, grain, or geometric patterns
- Use layered gradients (multiple gradient layers) instead of flat colors
- Consider paper-like textures, halftone dots, or line patterns
- Subtle box-shadows with intentional offset and spread (not identical shadows everywhere)
- Border treatments: try 1px borders with low-opacity colors instead of heavy card shadows

---

## Phase 3: Site-Type Specific Guidance

### Landing Pages / Portfolios
- Lead with a strong typographic statement, not a generic hero image
- Show personality in the first 2 seconds — unusual color, bold type, unique layout
- Use real content, not placeholder ipsum (generate realistic content if needed)
- Navigation should feel custom, not like a component library default

### SaaS / Dashboard
- Sidebar and data-dense layouts benefit from tight typography and muted palettes
- Use a single accent color for interactive elements, everything else neutral
- White space between data groups matters more than decorative elements
- Consider dark mode as the default — it often looks more polished for dashboards

### E-commerce
- Product imagery should drive the design, not fight with it
- Typography should be clear and serve the product, not compete
- Use generous spacing around products, tight spacing for metadata
- Micro-interactions on add-to-cart and product hover that feel tactile

### Blog / Content
- Reading experience is king — optimize line-height (1.6-1.8), line-length (60-75ch), and font size (18-20px)
- Serif or semi-serif fonts for body text add warmth and readability
- Pull quotes and drop caps add editorial character
- Minimal navigation that doesn't compete with content

---

## Implementation Checklist

Before delivering any frontend code, verify:

- [ ] Primary font is NOT Inter/Roboto/Open Sans
- [ ] Color palette has a clear dominant + accent structure (not 5 equal colors)
- [ ] No purple-to-blue gradient hero section
- [ ] Layout has at least one asymmetric or unexpected element
- [ ] First viewport reads as one cohesive composition
- [ ] Typography has dramatic size/weight contrasts
- [ ] Background is not pure #FFFFFF — uses warm tones or texture
- [ ] Copy is specific and contextual, not generic AI filler
- [ ] Motion is purposeful and limited to key moments
- [ ] At least one "this was clearly a human choice" moment exists

---

## CSS Variables Template

Start every project with intentional design tokens:

```css
:root {
  /* Typography — ALWAYS customize these */
  --font-display: 'Space Grotesk', sans-serif;
  --font-body: 'IBM Plex Sans', sans-serif;
  --font-mono: 'JetBrains Mono', monospace;

  /* Color — commit to a mood */
  --color-bg: #FAFAF8;
  --color-bg-deep: #F0EDE6;
  --color-text: #1A1A1A;
  --color-text-muted: #6B6B6B;
  --color-primary: #D4530E;      /* NOT blue/purple */
  --color-accent: #2B5F3A;
  --color-border: rgba(0,0,0,0.08);

  /* Spacing — use intentional scale */
  --space-xs: 0.25rem;
  --space-sm: 0.5rem;
  --space-md: 1rem;
  --space-lg: 2rem;
  --space-xl: 4rem;
  --space-2xl: 8rem;

  /* Motion */
  --ease-out-expo: cubic-bezier(0.16, 1, 0.3, 1);
  --ease-out-back: cubic-bezier(0.34, 1.56, 0.64, 1);
  --duration-fast: 150ms;
  --duration-normal: 300ms;
  --duration-slow: 600ms;
}
```

This is a STARTING POINT — customize it for every project. Never use these exact values twice.

---

## Reference Files

For deeper implementation details, read these files in the `references/` directory:

- `references/typography.md` — Font pairing recipes, size scales, Korean/English recommendations
- `references/color-and-theme.md` — Palette construction, themed approaches, dark mode
- `references/layout-patterns.md` — Grid breaking techniques, asymmetric layouts, editorial patterns
- `references/motion.md` — Animation sequences, scroll effects, micro-interactions with code
