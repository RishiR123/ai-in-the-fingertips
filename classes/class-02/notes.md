# Class 2 Notes: The AI Product Landscape — Inside OpenAI's Ecosystem

---

## 1. Who Is OpenAI?

- Founded in **2015** as a non-profit AI research lab by Sam Altman, Greg Brockman, Ilya Sutskever, Elon Musk, and others.
- Mission: *"Ensure that artificial general intelligence benefits all of humanity."*
- **2019**: Restructured into a "capped-profit" company — investors can earn returns up to 100x, after which profits go back to the non-profit. This allowed them to raise capital while keeping the mission intact.
- **2023**: Microsoft invested a cumulative **$13 billion** — making OpenAI one of the most well-funded AI companies in history.
- **2024 valuation**: ~$80–157 billion, making it one of the most valuable private companies ever.

> **Why does OpenAI's structure matter?** Because it shapes every product decision they make — they are not purely optimizing for revenue, but they also cannot ignore it.

---

## 2. The Model Family — OpenAI's Core Technology

OpenAI's products are built on a series of increasingly powerful models. Understanding the model lineup is the foundation for understanding everything else.

### The GPT Series (Text + Reasoning)

| Model | Released | Key Capability |
|-------|----------|---------------|
| GPT-1 | 2018 | Proof of concept — 117M parameters |
| GPT-2 | 2019 | Generated coherent paragraphs — initially withheld as "too dangerous" |
| GPT-3 | 2020 | 175B parameters — first API release, developers went wild |
| GPT-3.5 | 2022 | Faster, cheaper — the model behind the original ChatGPT |
| GPT-4 | 2023 | Multimodal (text + images), dramatically more capable |
| GPT-4o | 2024 | "Omni" — text, image, audio in real-time, much faster |
| o1 / o3 | 2024–25 | "Reasoning models" — thinks step-by-step before answering |

**Key insight**: Each generation is not just an upgrade — it unlocks entirely new use cases. GPT-4 made reliable coding assistance possible. GPT-4o made real-time voice conversation possible.

### DALL-E (Image Generation)
- DALL-E 1 (2021), DALL-E 2 (2022), DALL-E 3 (2023)
- Text-to-image: you describe what you want, the model generates it
- DALL-E 3 is integrated directly into ChatGPT

### Whisper (Speech-to-Text)
- Open-source model (2022) that transcribes audio to text
- Powers the voice input in ChatGPT
- Widely used by developers to add transcription to their own apps

### Sora (Video Generation)
- Released early 2024 — generates realistic videos from text prompts
- Still limited in availability but signals OpenAI's move into all media types

### Embeddings Models
- Less talked about, but critical for enterprise AI
- Convert text into numbers (vectors) that capture meaning
- Power: search, recommendation, document Q&A, and RAG (Retrieval Augmented Generation) systems

---

## 3. The Three Layers of OpenAI's Ecosystem

Think of OpenAI's ecosystem in three layers:

```
┌─────────────────────────────────────────────┐
│           CONSUMER PRODUCTS                  │
│   ChatGPT  |  ChatGPT Plus  |  ChatGPT Team │
├─────────────────────────────────────────────┤
│           DEVELOPER PLATFORM                 │
│     API  |  Assistants API  |  Fine-tuning  │
├─────────────────────────────────────────────┤
│           FOUNDATION MODELS                  │
│   GPT-4o  |  o1  |  DALL-E  |  Whisper     │
└─────────────────────────────────────────────┘
```

### Layer 1: Foundation Models
The raw intelligence — trained at enormous cost on massive datasets. This is where OpenAI's deepest competitive advantage lives.

### Layer 2: Developer Platform (The API)
- Developers pay per token (unit of text) to use OpenAI's models in their own apps
- The **Assistants API** lets developers build AI assistants with memory, file search, and code execution
- **Fine-tuning**: developers can train GPT-3.5 or GPT-4o on their own data to specialise the model
- This layer is what made OpenAI a *platform* rather than just a product company

### Layer 3: Consumer Products
- **ChatGPT Free**: GPT-3.5 / limited GPT-4o access
- **ChatGPT Plus** ($20/month): Full GPT-4o, image generation, web browsing, Advanced Data Analysis
- **ChatGPT Team / Enterprise**: Shared workspaces, admin controls, no data training
- **ChatGPT Edu**: Tailored for universities

---

## 4. Products Built ON TOP of OpenAI's API

This is where the ecosystem explodes. OpenAI's API powers thousands of third-party products:

| Product | What It Does | Uses OpenAI For |
|---------|-------------|-----------------|
| **GitHub Copilot** | AI code completion inside VS Code | GPT-4 for code generation |
| **Notion AI** | Writing assistant inside Notion | Summarise, rewrite, generate content |
| **Grammarly** | Writing corrections and suggestions | Tone, clarity, rewrite suggestions |
| **Cursor** | AI-first code editor | GPT-4o + Claude for coding |
| **Perplexity** | AI-powered search engine | GPT-4 for answer synthesis |
| **Khan Academy Khanmigo** | AI tutor for students | GPT-4 with strict educational guardrails |
| **Duolingo Max** | AI language tutor | GPT-4 to explain mistakes and roleplay |
| **Harvey AI** | Legal AI platform | GPT-4 fine-tuned on legal documents |

**Pattern**: None of these companies built a model. They built a *product experience* on top of OpenAI's model. The model is an ingredient, not the product.

---

## 5. The API Economy — How It Actually Works

When a developer uses the OpenAI API:

1. They send text (a **prompt**) to OpenAI's servers
2. The model processes it and returns a response
3. They are charged per **token** (roughly 4 characters = 1 token)

### Current pricing (approximate, GPT-4o):
- Input: ~$5 per million tokens
- Output: ~$15 per million tokens
- A typical ChatGPT conversation = a few thousand tokens = fractions of a cent

**Why this matters for product thinking**:
- Cost per query directly affects the business model of every app built on it
- High-volume apps (search, customer support) need cheap models
- High-value apps (legal, medical) can afford expensive models because each query is worth more

---

## 6. ChatGPT — The Product That Changed Everything

**November 30, 2022**: ChatGPT launches. It reaches:
- 1 million users in **5 days**
- 100 million users in **2 months** (fastest consumer product ever)
- 200 million weekly active users by 2024

### Why did it work when the underlying technology already existed?

| Before ChatGPT | After ChatGPT |
|----------------|---------------|
| API access — you needed to be a developer | Free chat interface — anyone could use it |
| You had to write prompts carefully | Conversational interface felt natural |
| GPT-3 had no memory within a session | ChatGPT remembered your conversation |
| No persona | "Assistant" persona made it feel approachable |

**The insight**: The model was not new. The *product wrapper* was what unlocked mass adoption.

---

## 7. OpenAI's Business Model

| Revenue Stream | Description |
|----------------|-------------|
| ChatGPT Plus/Team/Enterprise subscriptions | Monthly recurring revenue from end users |
| API usage | Pay-per-token from developers and businesses |
| Microsoft Azure OpenAI Service | Microsoft pays OpenAI to offer models through Azure |
| Custom enterprise deals | Large contracts with Fortune 500 companies |

**2024 revenue**: ~$3.4 billion (projected $11.6B for 2025)
**Burn rate**: Still spending more than it earns — training frontier models is extraordinarily expensive.

---

## 8. Competitors Challenging OpenAI's Ecosystem

OpenAI does not operate in a vacuum. Key challengers:

| Company | Model | Key Differentiator |
|---------|-------|--------------------|
| **Anthropic** | Claude | Safety-focused, longer context window |
| **Google DeepMind** | Gemini | Integrated into Google Search, Workspace |
| **Meta** | LLaMA 3 | Open-source — free to use and modify |
| **Mistral** | Mistral / Mixtral | Efficient, open-source, European |
| **xAI** | Grok | Integrated into X (Twitter) |

**The threat to OpenAI**: Meta's LLaMA is free. If it becomes good enough, companies will stop paying for the API and run models locally.

---

## Product Lens

**Why did Microsoft invest $13 billion in OpenAI instead of building their own model?**

- Microsoft had already tried (and failed) to build competitive AI internally
- GPT-4 was already better than anything Microsoft could build in a comparable timeframe
- By investing, Microsoft gets: exclusive cloud partnership (Azure), early model access, and integration rights into all Microsoft products (Office, GitHub, Bing)
- This gave rise to **Copilot** — Microsoft's AI brand across Word, Excel, Teams, GitHub, Windows
- For Microsoft, $13B bought them an AI transformation of their entire product portfolio

**The lesson**: Sometimes the right product decision is to partner, not build.

---

## Career Lens

Understanding the OpenAI ecosystem helps you position yourself in the job market:

- **Model layer**: Requires deep ML research skills — very few roles, very competitive
- **Platform/API layer**: Requires software engineering + understanding of AI capabilities — large and growing
- **Application layer**: Requires product thinking + domain expertise + ability to prompt and integrate — the biggest opportunity for most CS graduates

Most AI jobs being created right now are at the **application layer** — people who can take these models and build reliable, useful products with them.

---

## Key Terms to Remember

| Term | Meaning |
|------|---------|
| **Token** | Unit of text processed by a language model (~4 characters) |
| **API** | Application Programming Interface — lets developers use a model in their own code |
| **Fine-tuning** | Training a pre-existing model further on your own data |
| **RAG** | Retrieval-Augmented Generation — giving a model access to your documents at query time |
| **Embeddings** | Numerical representations of text that capture semantic meaning |
| **System prompt** | Hidden instructions that shape how a model behaves in a product |
| **Assistants API** | OpenAI's framework for building AI agents with memory and tools |

---

[Back to Class 2](README.md) | [Back to Course Index](../../README.md)
