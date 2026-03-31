# Layout Patterns Reference — Human Web Design

## The AI Layout Problem

AI tools produce the same structure every time:
Hero → 3-column features → testimonials → pricing → CTA footer.

Every card is identical. Every section has equal padding. Everything is perfectly centered.
Real designers break this monotony with intentional asymmetry and rhythm changes.

---

## The First Viewport Rule

The first viewport (what users see before scrolling) must read as ONE cohesive composition.
Not a dashboard of competing elements.

### Bad (AI default):
```
┌─────────────────────────────────┐
│  Logo    Nav    Nav    Nav  CTA │  ← generic navbar
│                                 │
│     Big Generic Headline        │  ← centered, boring
│     Subtitle that repeats it    │
│     [Primary CTA] [Ghost CTA]  │  ← two buttons always
│                                 │
│  ┌───┐  ┌───┐  ┌───┐  ┌───┐   │  ← stat strip / pills
│  │ 10K│  │ 99%│  │ 50+│  │ 24/7│ │
│  └───┘  └───┘  └───┘  └───┘   │
└─────────────────────────────────┘
```

### Good (intentional):
```
┌─────────────────────────────────┐
│  Logo              Nav    Nav   │  ← minimal nav
│                                 │
│  Very                           │
│  Large     ┌──────────────────┐ │  ← text + image overlap
│  Title     │                  │ │
│            │   Hero Image     │ │
│  Small     │   or Visual      │ │
│  context   │                  │ │
│  text      └──────────────────┘ │
│                          [CTA]  │  ← single action
└─────────────────────────────────┘
```

---

## Grid-Breaking Techniques

### 1. Asymmetric Split
Instead of 50/50 or equal thirds, use unequal divisions.

```css
.hero-grid {
  display: grid;
  grid-template-columns: 1fr 1.618fr; /* golden ratio split */
  gap: var(--space-xl);
  align-items: end; /* bottom-align, not center */
}

/* Or wider split */
.content-layout {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: var(--space-2xl);
}
```

### 2. Offset/Overlapping Elements
Let elements break out of their containers.

```css
.featured-card {
  position: relative;
  margin-left: -2rem;  /* break left edge */
  margin-top: -4rem;   /* overlap section above */
  z-index: 2;
}

.section-image {
  width: calc(100% + 4rem); /* wider than container */
  margin-left: -2rem;
  margin-right: -2rem;
}
```

### 3. Staggered Grid
Cards at different vertical positions create visual movement.

```css
.staggered-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-lg);
}

.staggered-grid > :nth-child(2) {
  transform: translateY(3rem); /* offset middle column */
}

.staggered-grid > :nth-child(3n) {
  transform: translateY(1.5rem); /* offset third column slightly */
}
```

### 4. Mixed Section Widths
Alternate between full-bleed and narrow contained sections.

```css
.section-full { padding: var(--space-2xl) 0; }
.section-narrow { max-width: 680px; margin: 0 auto; padding: var(--space-2xl); }
.section-wide { max-width: 1200px; margin: 0 auto; padding: var(--space-2xl); }
.section-bleed { width: 100vw; position: relative; left: 50%; right: 50%; margin-left: -50vw; }
```

### 5. Editorial / Magazine Layout
Use grid-template-areas for complex, editorial layouts.

```css
.editorial-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: auto;
  gap: var(--space-md);
}

.editorial-hero {
  grid-column: 1 / 8;    /* span 7 of 12 columns */
  grid-row: 1 / 3;       /* span 2 rows */
}

.editorial-sidebar {
  grid-column: 9 / 13;   /* right side, with gap */
  grid-row: 1 / 2;
}

.editorial-callout {
  grid-column: 8 / 13;
  grid-row: 2 / 3;
  align-self: end;
}
```

### 6. Bento Grid
Popularized by Apple — mixed-size tiles that feel curated.

```css
.bento-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(3, 200px);
  gap: var(--space-md);
}

.bento-grid > .large {
  grid-column: span 2;
  grid-row: span 2;
}

.bento-grid > .tall {
  grid-row: span 2;
}

.bento-grid > .wide {
  grid-column: span 2;
}
```

---

## Spacing Rhythm

AI tools use uniform spacing. Human designs use intentional rhythm changes.

### The Spacing Scale
Use a non-linear scale. Jump sizes should feel deliberate:

```
4px → 8px → 16px → 32px → 64px → 128px
```

NOT:

```
8px → 12px → 16px → 20px → 24px → 28px  (too linear, no drama)
```

### Section Spacing Pattern
Vary padding between sections to create rhythm:

```css
.section-hero    { padding: 8rem 0 6rem; }    /* extra top for breathing */
.section-intro   { padding: 4rem 0; }          /* tight, connected to hero */
.section-feature { padding: 8rem 0; }          /* generous, important content */
.section-cta     { padding: 6rem 0 4rem; }     /* moderate, driving action */
.section-footer  { padding: 3rem 0; }          /* compact, utilitarian */
```

### Internal Spacing
Within sections, vary spacing to show relationships:

```css
.card-group {
  display: flex;
  gap: var(--space-lg);  /* 2rem between cards */
}

.card h3 {
  margin-bottom: var(--space-xs); /* 0.25rem — title tight to description */
}

.card p {
  margin-bottom: var(--space-md); /* 1rem — space before link */
}
```

---

## Navigation Patterns That Don't Look AI

### Minimal Top Nav
```css
.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--space-md) var(--space-xl);
  /* No background, no border, no shadow — just floating content */
}

.nav-links {
  display: flex;
  gap: var(--space-lg);
  font-size: 0.875rem;
  font-weight: 500;
  letter-spacing: 0.02em;
}
```

### Side-Anchored Nav (unique feel)
```css
.nav-side {
  position: fixed;
  left: var(--space-lg);
  top: 50%;
  transform: translateY(-50%);
  writing-mode: vertical-rl;
  display: flex;
  gap: var(--space-lg);
  font-size: 0.75rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}
```

---

## Card Design — Beyond the Box

### Instead of identical cards, vary them:
```css
/* Card 1: simple text-only */
.card-text { padding: var(--space-xl); }

/* Card 2: image-heavy with overlay text */
.card-visual {
  position: relative;
  overflow: hidden;
  aspect-ratio: 4/3;
}
.card-visual .content {
  position: absolute;
  bottom: 0;
  padding: var(--space-lg);
  background: linear-gradient(transparent, rgba(0,0,0,0.7));
}

/* Card 3: bordered, no background */
.card-outlined {
  border: 1px solid var(--color-border);
  padding: var(--space-lg);
  background: transparent;
}
```

### Different sizes in the same grid signal curation, not automation:
```css
.cards-curated {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-lg);
}

.cards-curated > :first-child {
  grid-column: span 2;  /* featured item is wider */
}
```

---

## Responsive Strategy

Don't just stack columns. Rethink the layout at each breakpoint:

```css
/* Mobile: single column, but with interesting choices */
@media (max-width: 768px) {
  .hero-grid {
    grid-template-columns: 1fr;
    text-align: left;  /* NOT center — left-aligned text on mobile feels more intentional */
  }

  .section-feature {
    padding: 4rem var(--space-md); /* tighter but still generous */
  }

  /* Let images go full-bleed on mobile */
  .feature-image {
    width: 100vw;
    margin-left: calc(-1 * var(--space-md));
  }
}
```
