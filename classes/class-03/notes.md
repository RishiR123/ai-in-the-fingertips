# Class 3 Notes: The AI Product Landscape — Inside Anthropic's Ecosystem

---

## 1. Who Is Anthropic?

- Founded in **2021** by **Dario Amodei** (CEO) and **Daniela Amodei** (President), along with several senior researchers who left OpenAI.
- Why did they leave? They had growing concerns about whether OpenAI was moving too fast without sufficient focus on AI safety.
- Mission: *"The responsible development and maintenance of advanced AI for the long-term benefit of humanity."*
- Headquartered in San Francisco.
- As of 2024, valued at approximately **$18 billion**.

### The Founding Team's Background
Most of Anthropic's founding team came directly from OpenAI, where they had worked on GPT-2, GPT-3, and RLHF (the technique that made ChatGPT possible). They did not leave because they thought AI was not important — they left because they thought it was *too* important to rush.

> **Key idea**: Anthropic is not anti-AI. It is a bet that the safest AI company will also eventually be the most trusted — and therefore the most successful.

---

## 2. The Big Investors — Amazon and Google

Anthropic has received investment from two of the largest technology companies in the world — and the deals reveal a lot about how the AI industry is being structured.

### Amazon — Up to $4 Billion
- Amazon Web Services (AWS) committed up to **$4 billion** to Anthropic in 2023.
- In return: Claude models are available on **Amazon Bedrock** (AWS's managed AI service).
- Anthropic agreed to use AWS as its primary cloud provider and to train models on AWS's custom AI chips (**Trainium**, **Inferentia**).
- This is significant: training frontier AI models requires tens of thousands of GPUs and costs hundreds of millions of dollars. AWS provides that infrastructure.

### Google — Up to $2 Billion
- Google (through Google Cloud) invested up to **$2 billion**.
- Claude is available on **Google Cloud Vertex AI**.
- Google also provides compute through its TPUs (Tensor Processing Units).

### Why both?
- Anthropic needed compute — training Claude costs enormous amounts of money and infrastructure.
- Amazon and Google both needed a frontier model to compete with Microsoft's OpenAI partnership on their own cloud platforms.
- For Anthropic, having two cloud giants as both investors and distribution partners is a significant strategic advantage.

---

## 3. The Claude Model Family

Claude is Anthropic's AI model — named after Claude Shannon, the mathematician who founded information theory.

### The Three Tiers (as of Claude 3 onwards)

Anthropic introduced a three-tier model structure that has become their signature approach:

| Tier | Model | Best For | Speed | Cost |
|------|-------|----------|-------|------|
| **Fastest** | Claude Haiku | High-volume tasks, quick responses, lightweight apps | Very fast | Cheapest |
| **Balanced** | Claude Sonnet | Most everyday tasks — the sweet spot of capability and cost | Fast | Mid-range |
| **Most Capable** | Claude Opus | Complex reasoning, research, nuanced writing | Slower | Most expensive |

This tiered approach is a deliberate product strategy: developers can choose the right model for their use case rather than paying for the most expensive model for every task.

### Model Timeline

| Model | Released | Notable |
|-------|----------|---------|
| Claude 1 | 2023 | First public release — positioned as safer and more honest than GPT |
| Claude 2 | 2023 | 100K token context window — could read entire books in one prompt |
| Claude 2.1 | 2023 | 200K context window, reduced hallucinations |
| Claude 3 (Haiku / Sonnet / Opus) | March 2024 | Opus outperformed GPT-4 on many benchmarks; introduced the 3-tier structure |
| Claude 3.5 Sonnet | June 2024 | Outperformed Opus at Sonnet's price — a breakthrough in efficiency |
| Claude 3.5 Haiku | Nov 2024 | Fastest tier upgraded — better than previous Sonnet |
| Claude 3.7 Sonnet | 2025 | Extended thinking — the model can reason through problems step by step before answering |
| Claude 4 (Sonnet / Opus) | 2025 | Current frontier — significant capability leap |

### The Context Window Advantage
- Context window = how much text a model can read and remember in one conversation
- GPT-3 had ~4K tokens. GPT-4 launched with 8K–32K.
- Claude 2 launched with **100K tokens** — enough to read an entire novel
- Claude 3 supports **200K tokens** — roughly 150,000 words or 500 pages

This was a deliberate differentiation strategy. Long context is critical for enterprise use cases: reading entire legal contracts, analysing full codebases, processing large research reports.

---

## 4. What Makes Claude Different — The Technical Approach

### Constitutional AI (CAI)
- Anthropic invented a training technique called **Constitutional AI**.
- Instead of only relying on human labellers to judge whether a response is good or bad, they gave the AI a written *constitution* — a set of principles — and had the AI critique and revise its own outputs according to those principles.
- This makes safety training more scalable: you do not need a human to review every single output.
- The principles include things like: be honest, avoid harm, respect human autonomy, acknowledge uncertainty.

### RLHF (Reinforcement Learning from Human Feedback)
- Both OpenAI and Anthropic use this technique — Anthropic's founders actually pioneered it at OpenAI.
- The model generates responses, humans rate which responses are better, and the model is trained to produce more of the highly-rated responses.
- Anthropic's version is more heavily focused on *harmlessness* and *honesty* in addition to *helpfulness*.

### The HHH Framework
Anthropic trains Claude to be:
- **Helpful** — actually useful to the person asking
- **Harmless** — does not cause harm to users, third parties, or society
- **Honest** — does not deceive, does not pretend to know things it does not know

These three goals sometimes conflict. Anthropic spends significant research effort on how to balance them.

---

## 5. Anthropic's Product Ecosystem

### Claude.ai — The Consumer Product

- Anthropic's equivalent of ChatGPT — a web and mobile chat interface.
- **Free tier**: Access to Claude (limited usage)
- **Claude Pro** ($20/month): Higher usage limits, priority access to the latest models, Projects feature
- **Claude Team** ($25–30/user/month): Shared workspaces, admin controls, no data training on your conversations
- **Claude Enterprise**: Custom pricing, single sign-on, expanded context, dedicated support

#### Projects (launched 2024)
- A major product feature: create a "Project" with persistent instructions and uploaded files
- Example: create a "Marketing Project" where Claude always knows your brand guidelines and target audience
- This was Anthropic's answer to ChatGPT's custom instructions and memory features

### The API — For Developers

- Developers access Claude's models through Anthropic's API
- Same tiered pricing model: pay per input token and output token
- Supports: text, images (vision), documents, tool use (function calling), streaming

#### Tool Use / Function Calling
- Claude can be given *tools* — external functions it can call
- Example: give Claude a "search the web" tool and it can look up live information before answering
- This is the foundation for building AI agents with Claude

#### The Messages API
- Anthropic's API is built around a simple messages structure: you send a list of messages (user and assistant turns), and Claude responds
- Cleaner and more intuitive than some competing APIs

### Amazon Bedrock
- Claude is one of the featured models on AWS Bedrock
- Enterprise companies already using AWS can access Claude without leaving their existing cloud infrastructure
- This is how Anthropic reaches large enterprises that have compliance requirements about where their data lives

### Google Cloud Vertex AI
- Same story as Bedrock but for Google Cloud customers
- Claude can be accessed from within Google Cloud's AI platform

### Claude Code — AI for Software Engineering
- A command-line tool that runs Claude directly in a developer's terminal
- Can read files, edit code, run commands, and complete multi-step software engineering tasks autonomously
- Part of Anthropic's bet that software engineering is one of the highest-value use cases for frontier AI

---

## 6. The Model Context Protocol (MCP)

Announced in late 2024, **MCP** is one of Anthropic's most significant contributions to the broader AI ecosystem.

- MCP is an **open standard** — a universal way to connect AI models to external tools, data sources, and services.
- Think of it like a USB-C standard, but for AI integrations: instead of every developer building a custom connector to every tool, MCP provides one common interface.
- Examples: connect Claude to your company's database, your GitHub repositories, your calendar, Slack, or any other service — using the same standard.
- Because it is open-source, any company can build MCP connectors — and other AI providers can adopt the standard too.

> **Why this matters**: If MCP becomes the standard for AI tool integration (like HTTP became the standard for the web), Anthropic gains enormous influence over how the AI ecosystem evolves — even if other companies' models are being used.

---

## 7. Anthropic's Safety Research — Why It Matters for Products

Anthropic is unusual in that it publishes significant safety research and treats it as core to the company — not as an afterthought.

### Responsible Scaling Policy (RSP)
- A public commitment: Anthropic will not train or deploy AI models above certain capability thresholds unless they have safety measures in place to match.
- This is essentially a self-imposed regulatory framework.
- It signals to enterprise customers and governments that Anthropic is serious about governance.

### Interpretability Research
- Trying to understand *what is happening inside* a neural network — which features, which circuits, which patterns correspond to which concepts.
- Analogy: most AI training is like building a very complicated machine and not being able to look inside it. Anthropic is trying to build X-ray vision for AI.
- Practical outcome: if you can understand why a model makes a decision, you can fix it more reliably.

### Why Does Safety Research Matter for Product?
- Enterprise customers — especially in healthcare, finance, and government — will not use AI they cannot trust.
- Safety research is Anthropic's way of building that trust at a technical level, not just a marketing level.
- Regulatory bodies (EU AI Act, US executive orders) are increasingly requiring documentation of safety practices. Anthropic's research positions them well for compliance.

---

## 8. Anthropic vs OpenAI — A Direct Comparison

| Dimension | OpenAI | Anthropic |
|-----------|--------|-----------|
| Founded | 2015 | 2021 |
| Primary model | GPT-4o / o1 | Claude 3.5 / Claude 4 |
| Consumer product | ChatGPT (200M users) | Claude.ai (smaller but growing) |
| Key investor / partner | Microsoft | Amazon + Google |
| Cloud availability | Azure (primarily) | AWS + Google Cloud |
| Safety approach | RLHF + content moderation | Constitutional AI + Interpretability research |
| Open source stance | Closed (GPT), some open releases | Closed models, open MCP standard |
| Valuation (2024) | ~$157 billion | ~$18 billion |
| Revenue (2024) | ~$3.4 billion | ~$1 billion |

**Key takeaway**: OpenAI has a larger consumer footprint and more revenue today. Anthropic has a different strategic bet — that safety-focused, enterprise-trusted AI will win in the long run, especially as regulation increases.

---

## 9. Who Uses Claude? Real Products and Companies

| Company / Product | How They Use Claude |
|-------------------|---------------------|
| **Slack (Salesforce)** | Claude powers Slack AI — summarising channels, answering questions about conversation history |
| **Notion** | Claude integrated as an alternative to OpenAI for Notion AI features |
| **Quora (Poe)** | Claude available as one of multiple models on Poe's multi-model platform |
| **DuckDuckGo** | Claude powers AI answers in DuckDuckGo's privacy-focused AI chat |
| **Cursor** | The AI code editor uses Claude alongside GPT-4o for coding tasks |
| **Various legal, finance, healthcare firms** | Enterprise API access — often preferred over OpenAI for data privacy reasons |

---

## Product Lens

**Why did Dario Amodei leave a $1M+ salary at OpenAI — where he was VP of Research — to start a smaller, less-funded company?**

- Amodei and others believed that the pace of AI development was outrunning the safety research needed to make it reliable.
- At OpenAI, the pressure to ship products and raise capital was increasingly in tension with doing careful safety work.
- The bet: if AI systems become extremely powerful in the next 5–10 years, the company that understands them most deeply and has built the most trust will be the one that survives regulatory scrutiny and enterprise demand.
- Early signs this bet is working: Anthropic won the AWS partnership over OpenAI. Enterprise buyers increasingly evaluate Claude alongside GPT-4 as a first choice — not an alternative.

---

## Career Lens

Anthropic is smaller than OpenAI and Google but has one of the most respected research teams in the world. What roles exist there — and what do they teach us about where AI careers are heading?

| Role | What They Do |
|------|-------------|
| **Research Scientist** | Works on model training, safety, interpretability — requires PhD-level background |
| **Research Engineer** | Implements research ideas at scale — strong CS + ML engineering skills |
| **Product Engineer** | Builds Claude.ai, the API platform, Claude Code — standard product engineering |
| **Trust & Safety** | Reviews model outputs, builds evaluation systems, works on harm prevention |
| **Policy & Government Affairs** | Engages with regulators — lawyers, policy specialists |
| **Solutions Architect** | Helps enterprise customers integrate Claude — requires business + technical skills |

**The broader lesson**: Every AI company — not just Anthropic — is hiring for Trust & Safety, Policy, and Solutions roles that did not exist 5 years ago. Understanding AI deeply, even without building models, opens all of these doors.

---

## Key Terms to Remember

| Term | Meaning |
|------|---------|
| **Constitutional AI** | Anthropic's technique of training AI using a written set of principles for self-critique |
| **RLHF** | Reinforcement Learning from Human Feedback — using human ratings to improve model behaviour |
| **HHH** | Helpful, Harmless, Honest — Anthropic's three core training objectives for Claude |
| **Context window** | The maximum amount of text a model can process in a single conversation |
| **MCP** | Model Context Protocol — Anthropic's open standard for connecting AI to external tools |
| **Bedrock** | Amazon's managed AI service — one of Claude's primary distribution channels |
| **Responsible Scaling Policy** | Anthropic's self-imposed safety commitments tied to model capability levels |
| **Interpretability** | Research into understanding what is happening inside neural networks |

---

[Back to Class 3](README.md) | [Back to Course Index](../../README.md)
