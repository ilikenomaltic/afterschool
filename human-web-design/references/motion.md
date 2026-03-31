# Motion & Animation Reference — Human Web Design

## The AI Motion Problem

AI tools either add no animation (flat and lifeless) or add the same fade-in-up to every element
(repetitive and meaningless). Real motion design is about choreography — a few intentional
moments that guide attention and add character.

---

## Rule #1: Animate Moments, Not Everything

Pick 2-3 key moments per page to animate. Everything else can be static.

**Good moments to animate:**
- Page load / hero reveal (first impression)
- Key CTA or conversion point (draws attention)
- State changes (hover, active, toggle)
- Section transitions with scroll (if they serve a narrative)

**Skip animation on:**
- Body text paragraphs
- Every list item individually
- Generic cards with no hierarchy
- Navigation (unless it transforms on scroll)

---

## Page Load Sequence

The most impactful animation is the initial page load. Orchestrate it as a sequence, not a
simultaneous explosion.

### CSS-Only Staggered Reveal
```css
@keyframes revealUp {
  from {
    opacity: 0;
    transform: translateY(24px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes revealScale {
  from {
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

/* Orchestrate the sequence */
.hero-subtitle {
  opacity: 0;
  animation: revealUp 0.6s var(--ease-out-expo) 0.1s forwards;
}

.hero-title {
  opacity: 0;
  animation: revealUp 0.7s var(--ease-out-expo) 0.2s forwards;
}

.hero-description {
  opacity: 0;
  animation: revealUp 0.6s var(--ease-out-expo) 0.4s forwards;
}

.hero-cta {
  opacity: 0;
  animation: revealScale 0.5s var(--ease-out-back) 0.6s forwards;
  /* Back easing gives a subtle bounce — feels more alive */
}

.hero-image {
  opacity: 0;
  animation: revealScale 0.8s var(--ease-out-expo) 0.3s forwards;
}
```

### React / Framer Motion Version
```jsx
import { motion } from 'framer-motion';

const container = {
  hidden: {},
  show: {
    transition: {
      staggerChildren: 0.12,
      delayChildren: 0.1,
    }
  }
};

const item = {
  hidden: { opacity: 0, y: 24 },
  show: {
    opacity: 1,
    y: 0,
    transition: {
      duration: 0.6,
      ease: [0.16, 1, 0.3, 1], // expo out
    }
  }
};

function Hero() {
  return (
    <motion.div variants={container} initial="hidden" animate="show">
      <motion.span variants={item} className="subtitle">Subtitle</motion.span>
      <motion.h1 variants={item}>Big Title Here</motion.h1>
      <motion.p variants={item}>Description text.</motion.p>
      <motion.button variants={item}>Call to Action</motion.button>
    </motion.div>
  );
}
```

---

## Easing — The Secret Ingredient

Default `ease-in-out` feels mechanical. Custom easing curves feel human.

```css
:root {
  /* Smooth deceleration — for entrances */
  --ease-out-expo: cubic-bezier(0.16, 1, 0.3, 1);

  /* Slight overshoot — for buttons, interactive elements */
  --ease-out-back: cubic-bezier(0.34, 1.56, 0.64, 1);

  /* Quick start, slow end — for exits */
  --ease-in-expo: cubic-bezier(0.7, 0, 0.84, 0);

  /* Springy — for playful UI */
  --ease-spring: cubic-bezier(0.175, 0.885, 0.32, 1.275);

  /* Smooth and natural — for general transitions */
  --ease-smooth: cubic-bezier(0.25, 0.1, 0.25, 1);
}
```

### When to use each:
- **Entrance animations:** `ease-out-expo` — fast start, graceful stop
- **Button interactions:** `ease-out-back` — slight overshoot feels tactile
- **Exit/collapse:** `ease-in-expo` — slow start, quick finish
- **Toggle/switch:** `ease-spring` — playful bounce
- **Color/opacity transitions:** `ease-smooth` — subtle, not distracting

---

## Hover & Interaction States

### Buttons — Make Them Feel Pressable
```css
.btn {
  transition: all var(--duration-fast) var(--ease-out-back);
  transform-origin: center;
}

.btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.btn:active {
  transform: translateY(0px) scale(0.98);
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.1);
  transition-duration: 50ms;  /* snappy press feedback */
}
```

### Links — Underline Animations
```css
.text-link {
  position: relative;
  text-decoration: none;
}

.text-link::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0%;
  height: 1.5px;
  background: currentColor;
  transition: width 0.3s var(--ease-out-expo);
}

.text-link:hover::after {
  width: 100%;
}
```

### Cards — Subtle Lift
```css
.card {
  transition: transform var(--duration-normal) var(--ease-out-expo),
              box-shadow var(--duration-normal) var(--ease-out-expo);
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.08);
}

/* DON'T scale cards on hover — it looks AI-generated */
/* .card:hover { transform: scale(1.05); } ← avoid this */
```

### Images — Reveal on Hover
```css
.image-container {
  overflow: hidden;
  border-radius: var(--radius);
}

.image-container img {
  transition: transform 0.6s var(--ease-out-expo);
}

.image-container:hover img {
  transform: scale(1.05);
  /* Image scales INSIDE the container — contained, not overflowing */
}
```

---

## Scroll-Triggered Animations

Use sparingly. Max 2-3 scroll triggers per page.

### Intersection Observer (Vanilla JS)
```javascript
const observer = new IntersectionObserver(
  (entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('revealed');
        observer.unobserve(entry.target); // once only
      }
    });
  },
  { threshold: 0.2, rootMargin: '0px 0px -60px 0px' }
);

document.querySelectorAll('.scroll-reveal').forEach(el => observer.observe(el));
```

```css
.scroll-reveal {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s var(--ease-out-expo),
              transform 0.6s var(--ease-out-expo);
}

.scroll-reveal.revealed {
  opacity: 1;
  transform: translateY(0);
}

/* Stagger children */
.scroll-reveal.revealed > :nth-child(1) { transition-delay: 0s; }
.scroll-reveal.revealed > :nth-child(2) { transition-delay: 0.1s; }
.scroll-reveal.revealed > :nth-child(3) { transition-delay: 0.2s; }
```

### React Intersection Observer Hook
```jsx
function useInView(options = {}) {
  const ref = useRef(null);
  const [inView, setInView] = useState(false);

  useEffect(() => {
    const observer = new IntersectionObserver(([entry]) => {
      if (entry.isIntersecting) {
        setInView(true);
        observer.disconnect();
      }
    }, { threshold: 0.2, ...options });

    if (ref.current) observer.observe(ref.current);
    return () => observer.disconnect();
  }, []);

  return [ref, inView];
}
```

---

## Background Texture & Ambient Motion

Subtle background effects that add life without being distracting.

### CSS Noise Texture
```css
.textured-bg {
  background-color: var(--color-bg);
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
}
```

### Subtle Gradient Animation
```css
@keyframes gradientShift {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.ambient-bg {
  background: linear-gradient(
    -45deg,
    var(--color-bg),
    var(--color-bg-deep),
    var(--color-bg),
    var(--color-bg-deep)
  );
  background-size: 400% 400%;
  animation: gradientShift 20s ease infinite;
  /* 20s = barely perceptible movement. That's the point. */
}
```

---

## Duration Guidelines

| Context | Duration | Reason |
|---------|----------|--------|
| Color/opacity on hover | 100-200ms | Instant feedback |
| Transform on hover | 200-300ms | Noticeable but quick |
| Page element entrance | 400-700ms | Dramatic enough to notice |
| Full page load sequence | 800-1200ms total | Complete before user scrolls |
| Background ambient | 15-30s | Subliminal, not distracting |

**The key rule:** if a user has to wait for an animation to finish before they can do something,
it's too long.
