# Class 1 Notes: The Big Picture — 100 Years of AI in 45 Minutes

---

## 1. The 1950s–1980s: Where It All Began

- **1950 — Alan Turing** asks "Can machines think?" and proposes the **Turing Test**: if a machine can hold a conversation indistinguishable from a human, it passes as intelligent.
- **1956 — Dartmouth Conference**: The term *Artificial Intelligence* is coined. Researchers predict human-level AI within a generation. (They were off by several generations.)
- **1960s–70s**: Early AI programs like ELIZA (a simple chatbot) and chess-playing algorithms showed promise in narrow tasks.
- **Key insight**: Early AI was *rule-based* — humans wrote explicit rules for every situation. It could not learn from data.

---

## 2. The AI Winters — Why Progress Stalled Twice

### First Winter (1974–1980)
- Funding dried up after AI failed to deliver on its overpromised goals.
- Computers were too slow and memory too limited.
- Rule-based systems could not handle the complexity of real-world problems.

### Second Winter (1987–1993)
- "Expert systems" — AI that mimicked human experts using hand-coded rules — collapsed commercially.
- They were expensive to build and brittle: change one rule and the whole system broke.

**The lesson**: Hype cycles in AI are not new. The difference today is that the underlying technology has genuinely changed.

---

## 3. The Deep Learning Revolution (2012 Onwards)

- **2012 — AlexNet**: A neural network trained on GPUs won the ImageNet competition by a massive margin. It was the proof-of-concept that *deep learning* works at scale.
- **Why 2012?** Three things came together:
  1. **More data** — the internet generated massive labeled datasets
  2. **More compute** — GPUs (originally built for gaming) could run parallel matrix math
  3. **Better algorithms** — backpropagation and new architectures like CNNs

- Deep learning is different from rule-based AI: **the machine learns the rules from examples** rather than being told them explicitly.

---

## 4. The Transformer — The Architecture That Powers Everything Today

- **2017 — "Attention is All You Need"**: A paper from Google introduced the **Transformer architecture**.
- Before transformers, language models processed text word by word (slow, lost context).
- Transformers process all words simultaneously and learn which words are most *relevant* to each other — this is called **attention**.
- Every major AI model today — GPT-4, Gemini, Claude, LLaMA — is built on this architecture.

> **Product moment**: This one research paper, published in 2017, is the direct ancestor of ChatGPT (2022), GitHub Copilot, Midjourney, and virtually every AI product you use today.

---

## 5. Current Frontier Models

| Model | Company | What It Does |
|-------|---------|--------------|
| GPT-4 / GPT-4o | OpenAI | Text, code, image understanding, voice |
| Gemini Ultra | Google DeepMind | Multimodal — text, image, video, audio |
| Claude | Anthropic | Text, code — focused on safety and reliability |
| LLaMA 3 | Meta | Open-source — anyone can run it locally |
| Mistral | Mistral AI | Efficient open-source European model |

**Key pattern**: The gap between research paper and consumer product is now measured in *months*, not decades.

---

## 6. Why This Moment Is Different

| Era | What Changed |
|-----|-------------|
| 1950s–80s | Ideas, no compute or data |
| 1990s–2000s | More compute, still limited data |
| 2010s | Data explosion (internet, smartphones), GPU compute |
| 2020s | Scale + transformers = emergent capabilities nobody predicted |

**Emergent capabilities** = abilities that appear suddenly at large scale that were not present at smaller scale. Nobody programmed GPT-4 to write poetry or debug code — it learned these from data.

---

## Product Lens

**How did OpenAI turn a research paper into a product used by 200 million people?**

- 2015: OpenAI founded as a non-profit research lab (backed by Elon Musk, Sam Altman)
- 2019: Became "capped-profit" and took $1B from Microsoft
- 2020: Released GPT-3 via API — developers could build on it
- Nov 2022: Launched **ChatGPT** — the fastest consumer product to 100 million users in history (2 months)
- The insight: Making the model *conversational* and *free to try* removed every barrier to adoption

---

## Career Lens

AI literacy is now a **baseline expectation** across every engineering role — not just ML engineers.

- A backend engineer needs to know when to use an LLM API vs. build a rule-based system
- A product manager needs to know what AI can and cannot do reliably
- A founder needs to know why their data strategy is their moat

You do not need to build AI. You need to understand it well enough to make good decisions with it.

---

## Key Terms to Remember

| Term | Meaning |
|------|---------|
| **Turing Test** | A benchmark for machine intelligence based on conversation |
| **Neural Network** | A mathematical system loosely inspired by the brain, learns from examples |
| **Deep Learning** | Neural networks with many layers, trained on large data |
| **Transformer** | The architecture (2017) that powers all major LLMs today |
| **Emergent capabilities** | Abilities that appear at large scale without being explicitly programmed |
| **LLM** | Large Language Model — a transformer trained on massive text data |

---

[Back to Class 1](README.md) | [Back to Course Index](../../README.md)
