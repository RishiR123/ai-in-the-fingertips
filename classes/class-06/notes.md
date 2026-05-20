# Class 6 Notes: Landing Page Development — Hero Sections and Techniques

---

## 1. What Is a Landing Page?

A **landing page** is a standalone web page built for one specific purpose — to get a visitor to take a single action.

That action could be:
- Sign up for a product
- Download an app
- Join a waitlist
- Book a call
- Buy something

Unlike a full website with many pages and goals, a landing page is laser-focused. Everything on it — the headline, the design, the button — exists to drive that one action.

### Why Landing Pages Matter in the AI Era
- Every AI product launches with a landing page before it has a working product
- Vibe coding (from Class 4) lets you build one in hours
- A good landing page is how you validate an idea before spending months building it
- Investors, users, and collaborators all judge your idea from the landing page first

---

## 2. Anatomy of a Landing Page

A standard landing page has these sections in order:

```
┌─────────────────────────────────┐
│           NAVBAR                │  ← Logo + navigation links
├─────────────────────────────────┤
│                                 │
│         HERO SECTION            │  ← The most important part
│                                 │
├─────────────────────────────────┤
│       SOCIAL PROOF              │  ← Logos, testimonials, numbers
├─────────────────────────────────┤
│       FEATURES / HOW IT WORKS   │  ← What your product does
├─────────────────────────────────┤
│       TESTIMONIALS              │  ← Real user quotes
├─────────────────────────────────┤
│       PRICING                   │  ← Optional
├─────────────────────────────────┤
│       FINAL CTA                 │  ← Last push to convert
├─────────────────────────────────┤
│           FOOTER                │  ← Links, legal, socials
└─────────────────────────────────┘
```

Today's class focuses entirely on the **Hero Section** — because it is where you win or lose the visitor.

---

## 3. The Hero Section — Why It Is Everything

**The hero section** is the first thing a visitor sees when they land on your page — before they scroll.

You have approximately **3–5 seconds** before a visitor decides to stay or leave. In that time, they need to instantly understand:
1. What is this?
2. Is this for me?
3. What should I do next?

If your hero does not answer all three questions immediately, they are gone.

### The 5 Elements of a Hero Section

| Element | Purpose | Example |
|---------|---------|---------|
| **Headline** | One-line answer to "what is this?" | *"The AI writing tool for busy founders"* |
| **Subheadline** | One-line expansion — who it is for and what it does | *"Write emails, proposals, and posts 10x faster with AI that learns your voice"* |
| **CTA Button** | The one action you want them to take | *"Start for free"* / *"Join the waitlist"* |
| **Visual** | Image, illustration, screenshot, or video that makes it concrete | A product screenshot or a person using it |
| **Social proof** | A quick trust signal near the top | *"Trusted by 10,000+ founders"* or 5-star reviews |

---

## 4. Writing a Great Hero Headline

The headline is the hardest and most important thing to get right. Here are the patterns that work:

### Pattern 1: The Outcome
Tell them what they will achieve, not what the product does.

| Weak (feature-focused) | Strong (outcome-focused) |
|------------------------|--------------------------|
| "AI-powered writing assistant" | "Write 10x faster without sounding like a robot" |
| "Automated invoice software" | "Get paid faster — invoicing that takes 30 seconds" |
| "Smart calendar tool" | "Never miss a meeting or double-book again" |

### Pattern 2: The Specific Promise
The more specific, the more believable.

- *"Go from idea to published blog post in under 10 minutes"*
- *"Cut your customer support tickets by 40% with one integration"*

### Pattern 3: The Contrast
Name the old way vs the new way:

- *"Spreadsheets are dead. Here is how modern teams track inventory."*
- *"Stop guessing. Start knowing."*

### Pattern 4: The Direct Statement
Simple and bold works when your product is already well known:

- *"Think different."* (Apple)
- *"Move fast."* (generic startup cliché — avoid this)

---

## 5. CTA (Call to Action) Design

The CTA button is the only thing that matters at the end of the hero. Everything else exists to justify clicking it.

### CTA Writing Rules
- Be specific: *"Start building for free"* beats *"Get started"*
- State the value: *"Try free for 14 days"* beats *"Sign up"*
- Remove risk: *"No credit card required"* as small text below the button dramatically increases clicks
- One CTA only — two buttons create confusion

### CTA Button Design
```css
.cta-button {
  background-color: #6366f1;       /* Strong, confident colour */
  color: white;
  padding: 16px 36px;              /* Generous padding — easy to click */
  border-radius: 8px;              /* Slightly rounded, not a pill */
  font-size: 1.1rem;
  font-weight: 600;
  border: none;
  cursor: pointer;
  transition: background-color 0.2s ease, transform 0.2s ease;
}

.cta-button:hover {
  background-color: #4f46e5;
  transform: translateY(-2px);     /* Subtle lift on hover */
}
```

---

## 6. Hero Layout Techniques

### Technique 1: Centred Hero (Most Common)
Everything centred on the page. Clean, simple, works for almost any product.

```html
<section class="hero">
  <div class="hero-content">
    <h1>Your headline goes here</h1>
    <p>Your subheadline — one or two lines explaining who this is for.</p>
    <button class="cta-button">Start for free</button>
    <p class="trust">No credit card required · Free forever plan</p>
  </div>
</section>
```

```css
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 0 24px;
  background: #0f0f0f;
  color: white;
}

.hero-content {
  max-width: 720px;
}

.hero h1 {
  font-size: clamp(2rem, 5vw, 4rem);  /* Responsive font size */
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 24px;
}

.hero p {
  font-size: 1.2rem;
  color: #a1a1aa;
  margin-bottom: 40px;
  line-height: 1.6;
}

.trust {
  font-size: 0.875rem;
  color: #71717a;
  margin-top: 16px;
}
```

### Technique 2: Split Hero (Text Left, Visual Right)
Works well when you have a strong product screenshot or illustration.

```css
.hero {
  min-height: 100vh;
  display: grid;
  grid-template-columns: 1fr 1fr;   /* Two equal columns */
  align-items: center;
  gap: 60px;
  padding: 0 80px;
}

@media (max-width: 768px) {
  .hero {
    grid-template-columns: 1fr;     /* Stack on mobile */
    padding: 80px 24px;
    text-align: center;
  }
}
```

### Technique 3: Full-Screen Video Background
A looping video behind the hero content. High impact, high attention.

```html
<section class="hero-video">
  <video autoplay muted loop playsinline class="bg-video">
    <source src="background.mp4" type="video/mp4">
  </video>
  <div class="hero-overlay"></div>
  <div class="hero-content">
    <h1>Your headline</h1>
    <button class="cta-button">Get started</button>
  </div>
</section>
```

```css
.hero-video {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.bg-video {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  min-width: 100%;
  min-height: 100%;
  object-fit: cover;
  z-index: 0;
}

.hero-overlay {
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.6);  /* Dark overlay so text is readable */
  z-index: 1;
}

.hero-content {
  position: relative;
  z-index: 2;
  text-align: center;
  color: white;
}
```

### Technique 4: Gradient Background
No image needed — a well-crafted gradient looks modern and professional.

```css
/* Option A: Linear gradient */
.hero {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

/* Option B: Radial glow (popular with AI/tech startups) */
.hero {
  background: #050505;
  background-image: radial-gradient(
    ellipse 80% 50% at 50% -20%,
    rgba(120, 80, 255, 0.3),
    transparent
  );
}

/* Option C: Mesh gradient (very modern) */
.hero {
  background-color: #0a0a0a;
  background-image:
    radial-gradient(at 40% 20%, rgba(99, 102, 241, 0.15) 0px, transparent 50%),
    radial-gradient(at 80% 0%, rgba(168, 85, 247, 0.1) 0px, transparent 50%),
    radial-gradient(at 0% 50%, rgba(59, 130, 246, 0.1) 0px, transparent 50%);
}
```

---

## 7. Typography Techniques for Hero Sections

Typography is the biggest visual difference between an amateur and a professional landing page.

### Responsive Font Sizing with clamp()
`clamp(min, preferred, max)` — the font scales with the screen but never goes too small or too big.

```css
h1 {
  font-size: clamp(2rem, 5vw, 5rem);
}
```

### Gradient Text — The Modern Tech Headline Look
```css
.gradient-headline {
  background: linear-gradient(135deg, #fff 30%, #a78bfa);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
```

### Highlighted Word — Draw Attention to One Word
```html
<h1>Build AI products <span class="highlight">10x faster</span></h1>
```
```css
.highlight {
  color: #6366f1;
  position: relative;
}
```

### Letter Spacing and Line Height
```css
h1 {
  letter-spacing: -0.03em;  /* Tight tracking on large headings looks modern */
  line-height: 1.05;
}

p {
  line-height: 1.7;          /* Loose line height on body text improves readability */
  letter-spacing: 0.01em;
}
```

---

## 8. Animation Techniques for the Hero

Subtle animation makes a hero feel alive. These are the three most used patterns:

### Technique 1: Fade-In on Load
Elements appear smoothly when the page loads — draws the eye to key content.

```css
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.hero h1 {
  animation: fadeInUp 0.7s ease forwards;
}

.hero p {
  animation: fadeInUp 0.7s ease 0.15s forwards;  /* 0.15s delay — staggers after h1 */
  opacity: 0;
}

.hero .cta-button {
  animation: fadeInUp 0.7s ease 0.3s forwards;   /* Staggers after p */
  opacity: 0;
}
```

### Technique 2: Floating / Pulsing Element
A gentle floating animation on an image or badge adds life without being distracting.

```css
@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50%       { transform: translateY(-12px); }
}

.hero-image {
  animation: float 4s ease-in-out infinite;
}
```

### Technique 3: Typewriter Effect on the Headline
The headline types itself out — works well for AI product demos.

```html
<h1>Build <span class="typewriter" id="typewriter"></span></h1>
```

```javascript
const words = ['faster.', 'smarter.', 'with AI.'];
let wordIndex = 0;
let charIndex = 0;
let isDeleting = false;
const el = document.getElementById('typewriter');

function type() {
  const currentWord = words[wordIndex];

  if (!isDeleting) {
    el.textContent = currentWord.slice(0, charIndex + 1);
    charIndex++;
    if (charIndex === currentWord.length) {
      isDeleting = true;
      setTimeout(type, 1500);   // Pause before deleting
      return;
    }
  } else {
    el.textContent = currentWord.slice(0, charIndex - 1);
    charIndex--;
    if (charIndex === 0) {
      isDeleting = false;
      wordIndex = (wordIndex + 1) % words.length;
    }
  }
  setTimeout(type, isDeleting ? 60 : 100);
}

type();
```

```css
.typewriter {
  color: #6366f1;
  border-right: 3px solid #6366f1;  /* Blinking cursor */
  animation: blink 0.7s step-end infinite;
}

@keyframes blink {
  50% { border-color: transparent; }
}
```

---

## 9. The Navbar

Every landing page hero starts with a navbar. Keep it minimal.

```html
<nav class="navbar">
  <div class="nav-logo">YourBrand</div>
  <ul class="nav-links">
    <li><a href="#features">Features</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#" class="nav-cta">Get started</a></li>
  </ul>
</nav>
```

```css
.navbar {
  position: fixed;           /* Stays at top when scrolling */
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 60px;
  background: rgba(5, 5, 5, 0.8);
  backdrop-filter: blur(12px);   /* Frosted glass effect */
  border-bottom: 1px solid rgba(255,255,255,0.05);
}

.nav-links {
  display: flex;
  gap: 32px;
  list-style: none;
  align-items: center;
}

.nav-links a {
  color: #a1a1aa;
  text-decoration: none;
  font-size: 0.95rem;
  transition: color 0.2s;
}

.nav-links a:hover {
  color: white;
}

.nav-cta {
  background: #6366f1;
  color: white !important;
  padding: 10px 22px;
  border-radius: 8px;
  font-weight: 600;
}
```

**Frosted glass navbar** (`backdrop-filter: blur`) is the dominant style on modern landing pages in 2024–25. You see it on Vercel, Linear, Loom, and most AI startups.

---

## 10. Real Landing Pages to Study

These are landing pages worth dissecting — open each one and ask: what is the headline, what is the CTA, what visual technique are they using?

| Product | What to Notice |
|---------|---------------|
| **linear.app** | Minimal, fast, confident headline. No clutter. |
| **vercel.com** | Dark background, gradient text headline, product screenshot |
| **notion.so** | Simple split layout, very plain language |
| **elevenlabs.io** | Audio waveform animation in the hero |
| **perplexity.ai** | The search bar IS the hero — product-first design |
| **cursor.com** | The editor screenshot is the hero — no explanation needed |

**Pattern you will notice**: The best AI startup landing pages use dark backgrounds, gradient or white headlines, one clear CTA, and show the product immediately. They do not over-explain.

---

## 11. Putting It All Together — Full Hero Template

Here is a complete, copy-paste ready hero section combining everything from this class:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Your Product</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
      background: #050505;
      color: white;
    }

    /* NAVBAR */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 20px 60px;
      background: rgba(5,5,5,0.8);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(255,255,255,0.06);
    }

    .logo { font-weight: 700; font-size: 1.1rem; }

    nav ul {
      display: flex; gap: 28px;
      list-style: none; align-items: center;
    }

    nav a {
      color: #a1a1aa; text-decoration: none;
      font-size: 0.9rem; transition: color 0.2s;
    }

    nav a:hover { color: white; }

    .nav-cta {
      background: #6366f1; color: white !important;
      padding: 9px 20px; border-radius: 7px; font-weight: 600;
    }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex; align-items: center; justify-content: center;
      text-align: center; padding: 120px 24px 80px;
      background-image: radial-gradient(
        ellipse 80% 50% at 50% -10%,
        rgba(99, 102, 241, 0.25),
        transparent
      );
    }

    .hero-content { max-width: 760px; }

    .badge {
      display: inline-flex; align-items: center; gap: 8px;
      background: rgba(99,102,241,0.1);
      border: 1px solid rgba(99,102,241,0.3);
      color: #a5b4fc; padding: 6px 16px; border-radius: 999px;
      font-size: 0.85rem; margin-bottom: 32px;
      animation: fadeInUp 0.6s ease forwards;
    }

    h1 {
      font-size: clamp(2.2rem, 5.5vw, 4.5rem);
      font-weight: 800; line-height: 1.08;
      letter-spacing: -0.03em; margin-bottom: 24px;
      animation: fadeInUp 0.6s ease 0.1s forwards; opacity: 0;
    }

    .gradient-text {
      background: linear-gradient(135deg, #fff 40%, #a78bfa);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .subheadline {
      font-size: 1.15rem; color: #a1a1aa; line-height: 1.65;
      max-width: 560px; margin: 0 auto 40px;
      animation: fadeInUp 0.6s ease 0.2s forwards; opacity: 0;
    }

    .cta-group {
      display: flex; gap: 12px; justify-content: center; flex-wrap: wrap;
      animation: fadeInUp 0.6s ease 0.3s forwards; opacity: 0;
    }

    .btn-primary {
      background: #6366f1; color: white;
      padding: 14px 32px; border-radius: 8px;
      font-size: 1rem; font-weight: 600; border: none;
      cursor: pointer; transition: background 0.2s, transform 0.2s;
    }

    .btn-primary:hover { background: #4f46e5; transform: translateY(-2px); }

    .btn-secondary {
      background: transparent; color: #d4d4d8;
      padding: 14px 32px; border-radius: 8px;
      font-size: 1rem; font-weight: 500;
      border: 1px solid rgba(255,255,255,0.12);
      cursor: pointer; transition: border-color 0.2s, color 0.2s;
    }

    .btn-secondary:hover { border-color: rgba(255,255,255,0.3); color: white; }

    .trust {
      margin-top: 20px; font-size: 0.82rem; color: #52525b;
      animation: fadeInUp 0.6s ease 0.4s forwards; opacity: 0;
    }

    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(24px); }
      to   { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

  <nav>
    <div class="logo">YourBrand</div>
    <ul>
      <li><a href="#">Features</a></li>
      <li><a href="#">Pricing</a></li>
      <li><a href="#" class="nav-cta">Get started</a></li>
    </ul>
  </nav>

  <section class="hero">
    <div class="hero-content">
      <div class="badge">✦ Now in public beta</div>
      <h1>
        Build AI products
        <span class="gradient-text">10x faster</span>
      </h1>
      <p class="subheadline">
        The platform that turns your ideas into working prototypes — 
        without writing a single line of ML code.
      </p>
      <div class="cta-group">
        <button class="btn-primary">Start building free</button>
        <button class="btn-secondary">See how it works →</button>
      </div>
      <p class="trust">No credit card required · Free forever plan · 2,400+ builders</p>
    </div>
  </section>

</body>
</html>
```

Save this as `index.html`, open it in a browser, and you have a production-quality hero section.

---

## Key Terms to Remember

| Term | Meaning |
|------|---------|
| **Hero section** | The first visible area of a webpage — above the fold |
| **CTA** | Call to Action — the button or link you want the visitor to click |
| **Above the fold** | Everything visible without scrolling |
| **clamp()** | CSS function for responsive font sizes: `clamp(min, preferred, max)` |
| **backdrop-filter** | CSS property for the frosted glass effect on navbars |
| **Gradient text** | CSS technique using `background-clip: text` to colour text with a gradient |
| **Typewriter effect** | JS animation that simulates text being typed in real time |
| **Staggered animation** | Delaying each element's animation so they appear one after another |
| **Social proof** | Trust signals — user counts, logos, testimonials — placed near the CTA |

---

[Back to Class 6](README.md) | [Back to Course Index](../../README.md)
