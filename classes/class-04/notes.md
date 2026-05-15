# Class 4 Notes: Google's AI Ecosystem + Vibe Coding a Scroll-Animated Site

---

## PART 1: Google's AI Ecosystem

---

## 1. Google's Complicated Relationship with AI

Google is arguably the company most responsible for the current AI era — and yet it was caught off guard by it.

### What Google Invented
- **2017**: Google researchers published *"Attention is All You Need"* — the transformer paper that every modern LLM is built on
- **2014**: Google acquired DeepMind for ~$600M
- **2015**: Google Brain was already one of the world's top AI research labs
- **2016**: AlphaGo (DeepMind) beat the world champion at Go — a landmark AI moment

### The ChatGPT Problem
- **November 2022**: ChatGPT launches and becomes the fastest-growing consumer product ever
- Google reportedly issued an internal **"code red"** — their core Search business was suddenly threatened
- **February 2023**: Google rushed out **Bard** (their ChatGPT competitor) — it made a factual error in the demo, and Google's stock dropped 9% in one day ($100B wiped in hours)
- **The lesson**: Having the best research does not automatically translate into the best product. Google had LaMDA (the model behind Bard) for years but never turned it into a consumer product.

### The Reorganisation
- In 2023, Google merged **Google Brain** and **DeepMind** into a single unit: **Google DeepMind**
- This was an acknowledgment that the previous structure was creating duplication and slowing product delivery
- Demis Hassabis (DeepMind founder) became CEO of the combined organisation

---

## 2. The Gemini Model Family

Bard was rebranded as **Gemini** in February 2024 — a signal that Google was getting serious about competing at the frontier.

### The Three Tiers (mirrors Anthropic's approach)

| Model | Best For | Key Strength |
|-------|----------|-------------|
| **Gemini Flash** | Fast, high-volume tasks | Cheapest, quickest response |
| **Gemini Pro** | Everyday tasks, balanced performance | The workhorse model |
| **Gemini Ultra** | Complex reasoning, research | Most capable |

### What Makes Gemini Different — Native Multimodality

Most early LLMs were text-first. Vision and audio were added later as bolt-ons.

Gemini was designed from the ground up to handle **text, images, audio, video, and code simultaneously** — not as separate capabilities but as a unified model.

- You can show Gemini a photo and ask it a question about what's in it
- You can give it a video and ask it to summarise what happened at the 3-minute mark
- You can give it a chart and ask it to reason about the data

### Gemini 1.5 Pro — The Context Window Record
- Launched with a **1 million token context window** (later extended to 2 million)
- To put that in perspective: Claude 3 has 200K, GPT-4 has 128K
- 1 million tokens = roughly 700,000 words = an entire library shelf of documents
- Use case: give Gemini an entire codebase and ask it to find bugs across all files simultaneously

### Gemini 2.0 and 2.5
- **2.0**: Introduced "agentic" capabilities — Gemini can take actions, not just answer questions
- **2.5 Pro**: As of early 2025, ranks #1 on most coding benchmarks; "thinking" mode lets it reason step-by-step before answering — competing directly with OpenAI's o1

---

## 3. Google's AI Product Ecosystem — The Full Map

Google's AI ecosystem is different from OpenAI's or Anthropic's because it is woven into products that billions of people already use.

### Consumer Products

#### Gemini App (formerly Bard)
- Google's direct answer to ChatGPT
- Available at gemini.google.com and as a mobile app
- **Gemini Advanced** ($19.99/month, included in Google One AI Premium): Access to the most capable Gemini models
- Deep integration with Google services: can access your Gmail, Google Drive, Google Docs, Calendar

#### Google Search — AI Overviews
- **AI Overviews** (previously "Search Generative Experience"): AI-generated summaries appear at the top of search results
- This is the highest-stakes AI product deployment in history — Google Search handles ~8.5 billion queries per day
- Challenge: AI Overviews have produced embarrassing errors (suggesting people eat rocks, use glue in pizza), showing that deploying AI at search scale is genuinely hard

#### NotebookLM
- One of Google's most interesting and underrated AI products
- You upload your own documents (PDFs, Google Docs, YouTube links, audio files) and NotebookLM becomes an expert on *your specific documents*
- Key feature: **Audio Overviews** — it generates a podcast-style conversation between two AI hosts summarising your documents
- Use case for students: upload your lecture notes and textbooks, then ask questions or generate a podcast to study from

### Productivity — Gemini in Google Workspace
Google has embedded AI across its entire productivity suite:

| Product | What Gemini Does |
|---------|-----------------|
| **Gmail** | Summarise email threads, draft replies, suggest responses |
| **Google Docs** | Write first drafts, rewrite sections, summarise long documents |
| **Google Sheets** | Generate formulas, analyse data, create charts from descriptions |
| **Google Slides** | Generate full presentations from a prompt |
| **Google Meet** | Real-time transcription, meeting summaries, action items |
| **Google Drive** | Ask questions across all files in your Drive |

This is Google's advantage over OpenAI: they do not need to convince people to use a new product. They embed AI into tools people use every day.

### Developer Platform

#### Google AI Studio
- Free web interface for developers to experiment with Gemini models
- Write and test prompts, adjust parameters, export code directly
- The fastest way to get started building with Gemini — no setup required
- Supports: text, images, video, audio, documents, code

#### Vertex AI
- Google Cloud's enterprise AI platform
- Hosts Gemini alongside other models (including Claude, Meta's LLaMA, and others)
- Adds enterprise features: data governance, model monitoring, fine-tuning, deployment pipelines
- Target customer: large companies that already use Google Cloud and need AI with compliance controls

#### Gemini API
- Direct API access to Gemini models for developers
- Free tier available (with rate limits) — making it one of the most accessible frontier model APIs
- Supports multimodal inputs: text, image, audio, video, PDF

### Google's AI in Search Infrastructure — TPUs
- Google designed its own AI chips: **Tensor Processing Units (TPUs)**
- TPUs are specifically optimised for the matrix operations at the core of neural network training and inference
- Google has been using TPUs since 2016 — years before Nvidia's GPUs became the industry standard for AI
- This gives Google a cost and performance advantage for running its own models at scale

---

## 4. DeepMind — The Research Engine

Google DeepMind is one of the most impactful AI research labs in history, separate from the consumer product teams.

### Key Breakthroughs

| Project | What It Did | Why It Matters |
|---------|------------|----------------|
| **AlphaGo** (2016) | Beat world champion at Go | Proved deep reinforcement learning could master complex strategy |
| **AlphaFold 2** (2020) | Solved the protein folding problem | 50-year unsolved biology problem — predicted 3D structure of 200M proteins |
| **AlphaCode** | Writes competitive programming solutions | Among the top 50% of human programmers on Codeforces |
| **Gemini** | Frontier multimodal model | DeepMind's research now directly feeds Google's product roadmap |
| **AlphaGeometry** (2024) | Solves Olympiad geometry problems | Performs at the level of a gold medallist |

**AlphaFold's impact**: Drug companies are using AlphaFold's protein structure predictions to accelerate drug discovery. This is AI creating direct, measurable value in the real world — not just answering chat questions.

---

## 5. Google vs OpenAI vs Anthropic — The Competitive Picture

| Dimension | Google | OpenAI | Anthropic |
|-----------|--------|--------|-----------|
| Flagship model | Gemini 2.5 Pro | GPT-4o / o3 | Claude 3.7 / Claude 4 |
| Consumer product | Gemini App | ChatGPT | Claude.ai |
| Key advantage | Distribution (billions of users), TPU infrastructure, data | Brand, developer ecosystem, ChatGPT scale | Safety, enterprise trust, long context |
| Cloud platform | Google Cloud / Vertex AI | Azure (Microsoft) | AWS (Amazon) + Google Cloud |
| Open source stance | Gemma (open weights model) | Closed | Closed (open MCP standard) |
| Research arm | Google DeepMind | OpenAI Research | Anthropic Research |
| Revenue model | Workspace AI subs + API + Cloud | ChatGPT subs + API | Claude subs + API + Cloud partnerships |

---

## PART 2: Vibe Coding

---

## 6. What Is Vibe Coding?

The term **"vibe coding"** was coined by Andrej Karpathy (co-founder of OpenAI, former Tesla AI director) in early 2025:

> *"There's a new kind of coding I call 'vibe coding', where you fully give in to the vibes, embrace exponentials, and forget that the code even exists."*

In plain terms: **you describe what you want to build in natural language, and AI writes the code**. You iterate through conversation — asking for changes, additions, fixes — without manually writing code yourself.

### Why Is This a Big Deal?

Previously, building software required:
- Learning a programming language (months to years)
- Understanding frameworks, libraries, debugging tools
- Writing every line by hand

With vibe coding:
- You describe the outcome, not the implementation
- The AI handles syntax, structure, and boilerplate
- You stay focused on *what* you want, not *how* to build it

**The implication**: The barrier between having an idea and having a working prototype has collapsed. A student with zero coding experience can build a functional web app in an afternoon.

---

## 7. Tools for Vibe Coding

| Tool | Best For | How to Access |
|------|----------|---------------|
| **Cursor** | Full coding projects — reads your whole codebase | cursor.com (free tier available) |
| **Bolt.new** | Full-stack web apps from a prompt | bolt.new (browser-based) |
| **v0 by Vercel** | React UI components and web interfaces | v0.dev |
| **Lovable** | Full apps with backend and database | lovable.dev |
| **Claude / ChatGPT** | Code generation in chat — copy-paste into files | claude.ai / chatgpt.com |
| **Replit AI** | Code + run + deploy in one browser environment | replit.com |

---

## 8. Hands-On: Building a Scroll-Animated Site with Vibe Coding

### What We Are Building
A single-page website with:
- A fixed navigation bar
- A hero section with a headline and subheading
- Sections that animate in as you scroll down (fade in, slide up)
- Smooth scroll behaviour
- Clean, modern design

### Step 1: The First Prompt

Open Claude, ChatGPT, or Cursor and paste this prompt:

```
Create a single-page HTML website with the following:
- A sticky navbar with 3 links: Home, About, Contact
- A full-screen hero section with a headline "AI Is in the Fingertips" and a subheading
- Three content sections below the hero, each with a title and paragraph
- Smooth scroll-triggered animations: each section fades in and slides up when it enters the viewport
- Use only HTML, CSS, and vanilla JavaScript — no external libraries
- Modern, clean design with a dark background and white text
- Make it mobile-friendly
```

### Step 2: What the AI Generates

The AI will produce a complete HTML file. The scroll animations typically use the **Intersection Observer API** — a browser feature that detects when an element enters the viewport.

Key JavaScript pattern (you do not need to memorise this — just recognise it):

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
    }
  });
});

document.querySelectorAll('.animate-on-scroll').forEach(el => {
  observer.observe(el);
});
```

And the CSS that makes it animate:

```css
.animate-on-scroll {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}

.animate-on-scroll.visible {
  opacity: 1;
  transform: translateY(0);
}
```

### Step 3: Iterating with Follow-Up Prompts

Once you have a base site, iterate by prompting:

- *"Change the hero background to a gradient from deep blue to purple"*
- *"Add a 0.2 second delay between each section animating in, so they stagger"*
- *"Add a smooth parallax effect to the hero image as I scroll"*
- *"Make the navbar shrink and add a shadow when I scroll past the hero section"*
- *"Add a scroll progress bar at the top of the page"*

Each of these is a single follow-up message. The AI rewrites only the relevant part.

### Step 4: Deploying for Free

Once your site is ready:
1. Copy the HTML into a file called `index.html`
2. Go to **Netlify Drop** (netlify.com/drop) or **GitHub Pages**
3. Drag and drop the file — it is live on the internet in 30 seconds, for free

---

## 9. The Limits of Vibe Coding

Vibe coding is powerful but has real constraints you need to understand:

| Limitation | What It Means |
|-----------|---------------|
| **No understanding** | The AI can produce code that looks right but has subtle bugs — especially in logic-heavy or security-sensitive areas |
| **Context limits** | For large projects, the AI loses track of earlier code and starts contradicting itself |
| **Debugging is harder** | If you did not write the code, you may not understand it well enough to fix it when something breaks |
| **Security risks** | AI-generated code may have vulnerabilities (SQL injection, XSS) if you are not careful about what you deploy |
| **Maintenance** | Code that was vibed into existence is often harder to maintain as requirements change |

**The balance**: Vibe coding is excellent for prototypes, demos, personal projects, and learning. For production systems, you still need engineers who understand the code deeply.

---

## Product Lens

**How did Google's distribution advantage and engineering culture both help and hurt it in the AI race?**

- **Helped**: Google could embed Gemini into Gmail, Search, and Docs overnight and reach billions — something OpenAI cannot do
- **Hurt**: Google's existing Search business was so profitable ($200B+ revenue) that they were afraid to cannibalise it with AI. This is a classic **innovator's dilemma** — the biggest risk to Google's dominance was not a competitor; it was their own reluctance to disrupt their core product
- **Result**: OpenAI, a company that was irrelevant three years ago, now defines what "AI assistant" means to the public — while Google plays catch-up in the product that it invented the technology for

---

## Career Lens

Vibe coding is not just a trick — it is reshaping the skills that matter in software engineering.

- **What is declining in value**: Writing boilerplate code, syntax memorisation, basic CRUD operations
- **What is increasing in value**: System design, knowing *what* to build and *why*, debugging AI-generated code, security review, understanding user needs
- **The new skill**: Prompt engineering for code — knowing how to describe a system precisely enough that the AI builds what you actually want
- **For students**: You can now build a working portfolio project in a weekend that would have taken a month before. The bar for what counts as "impressive" has risen — but so has your ability to meet it.

---

## Key Terms to Remember

| Term | Meaning |
|------|---------|
| **Gemini** | Google's flagship AI model family (Flash / Pro / Ultra) |
| **Google DeepMind** | Google's combined AI research organisation |
| **Vertex AI** | Google Cloud's enterprise AI platform |
| **Google AI Studio** | Free browser tool for experimenting with Gemini |
| **NotebookLM** | Google's AI that becomes an expert on your uploaded documents |
| **TPU** | Tensor Processing Unit — Google's custom AI chip |
| **Vibe coding** | Building software by describing what you want to an AI in plain English |
| **Intersection Observer** | Browser API that detects when elements enter the viewport — used for scroll animations |
| **Bolt.new / Cursor / v0** | Popular vibe coding tools for building web apps and UIs |

---

[Back to Class 4](README.md) | [Back to Course Index](../../README.md)
