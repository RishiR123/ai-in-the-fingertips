# Class 7 Notes: AI Agents — Concepts and Building a Minimal Agent

---

# PART 1: AI Agents — Concepts and Landscape

---

## 1. What Is an AI Agent?

A **chatbot** answers your question and stops.

An **AI agent** receives a goal and keeps working — planning steps, using tools, checking results, and trying again — until the task is done.

| | Chatbot | AI Agent |
|---|---------|----------|
| **Input** | A question | A goal |
| **Output** | An answer | A completed task |
| **Tools** | None | Web search, code execution, file access, APIs |
| **Memory** | Single conversation | Can persist across steps |
| **Autonomy** | Zero — waits for you | Takes actions on its own |
| **Example** | "What is the weather?" | "Find the latest ISL standings and save them to a file" |

> **The key shift**: Moving from *answering* to *doing*.

---

## 2. The Agent Loop

Every AI agent runs the same basic loop:

```
1. PERCEIVE  →  Read the goal and current state
      ↓
2. THINK     →  Decide what to do next
      ↓
3. ACT       →  Use a tool or take an action
      ↓
4. OBSERVE   →  Read the result
      ↓
5. REPEAT    →  Until the goal is achieved
```

---

## 3. Tools — What Give Agents Their Power

A tool is a function the model can choose to call. The model does not run the tool itself — it decides to call it, and your code actually executes it.

| Tool | What It Does |
|------|-------------|
| `wikipedia` | Fetch summaries of any topic |
| `get_current_time` | Return the current date and time |
| `web_search` | Search the internet for live information |
| `run_code` | Execute code and return the result |
| `github` | Create repos, commit files, push code |
| `browser` | Navigate and interact with websites |

---

# PART 2: Building the Agent — TypeScript + LangChain + Gemini

---

## 4. Tech Stack Chosen

| Component | Choice | Why |
|-----------|--------|-----|
| **Language** | TypeScript | Strong for application development; growing AI ecosystem |
| **Framework** | LangChain | Handles LLM interaction, tool parsing, and memory — so you write less boilerplate |
| **LLM** | Gemini 1.5 Flash | Free-tier accessible via Google AI Studio; fast and capable |
| **UI** | React | Standard frontend framework |
| **Desktop (optional)** | Electron | Wraps a web app into a desktop app with file system access |

---

## 5. Step 1 — Environment Setup

### Create a TypeScript + React project

```bash
npm create vite@latest my-agent -- --template react-ts
cd my-agent
npm install
```

### Install dependencies

```bash
# LangChain core + Google Gemini integration
npm install langchain @langchain/google-genai

# LangChain community tools (Wikipedia, etc.)
npm install @langchain/community
```

### Get your Gemini API key
1. Go to [aistudio.google.com](https://aistudio.google.com)
2. Click **Get API Key** → **Create API key**
3. Copy it — you will use it in the next step

---

## 6. Step 2 — Build the Chat UI

Create a simple chat interface in React. The goal is a message list and an input box — keep it minimal.

```tsx
// src/App.tsx
import { useState } from 'react'
import './App.css'

interface Message {
  role: 'user' | 'agent'
  content: string
}

function App() {
  const [messages, setMessages] = useState<Message[]>([])
  const [input, setInput] = useState('')
  const [loading, setLoading] = useState(false)

  const sendMessage = async () => {
    if (!input.trim()) return
    const userMessage = input
    setInput('')
    setMessages(prev => [...prev, { role: 'user', content: userMessage }])
    setLoading(true)

    try {
      const response = await runAgent(userMessage)  // Agent function (Step 3)
      setMessages(prev => [...prev, { role: 'agent', content: response }])
    } catch (e) {
      setMessages(prev => [...prev, { role: 'agent', content: 'Error running agent.' }])
    } finally {
      setLoading(false)
    }
  }

  return (
    <div className="chat-container">
      <div className="messages">
        {messages.map((m, i) => (
          <div key={i} className={`message ${m.role}`}>
            <span className="label">{m.role === 'user' ? 'You' : 'Agent'}</span>
            <p>{m.content}</p>
          </div>
        ))}
        {loading && <div className="message agent"><p>Thinking...</p></div>}
      </div>
      <div className="input-row">
        <input
          value={input}
          onChange={e => setInput(e.target.value)}
          onKeyDown={e => e.key === 'Enter' && sendMessage()}
          placeholder="Ask the agent anything..."
        />
        <button onClick={sendMessage}>Send</button>
      </div>
    </div>
  )
}

export default App
```

---

## 7. Step 3 — Wire Up LangChain and Gemini

This is where the chatbot becomes an agent. LangChain handles the tool-calling loop so you do not have to write it manually.

```typescript
// src/agent.ts
import { ChatGoogleGenerativeAI } from '@langchain/google-genai'
import { AgentExecutor, createToolCallingAgent } from 'langchain/agents'
import { ChatPromptTemplate } from '@langchain/core/prompts'
import { WikipediaQueryRun } from '@langchain/community/tools/wikipedia_query_run'
import { DynamicTool } from '@langchain/core/tools'

// 1. The LLM
const llm = new ChatGoogleGenerativeAI({
  model: 'gemini-1.5-flash',
  apiKey: import.meta.env.VITE_GEMINI_API_KEY,
  temperature: 0
})

// 2. The Tools
const wikipediaTool = new WikipediaQueryRun({
  topKResults: 1,
  maxDocContentLength: 800
})

const timeTool = new DynamicTool({
  name: 'get_current_time',
  description: 'Returns the current date and time. Use this when the user asks what time or date it is.',
  func: async () => new Date().toLocaleString('en-IN', { timeZone: 'Asia/Kolkata' })
})

const tools = [wikipediaTool, timeTool]

// 3. The Prompt — tells the agent how to behave
const prompt = ChatPromptTemplate.fromMessages([
  ['system', 'You are a helpful AI assistant with access to tools. Use them when needed.'],
  ['human', '{input}'],
  ['placeholder', '{agent_scratchpad}']  // LangChain uses this for tool call history
])

// 4. Build the agent
const agent = createToolCallingAgent({ llm, tools, prompt })

// 5. The executor runs the agent loop
const agentExecutor = new AgentExecutor({
  agent,
  tools,
  verbose: true   // Set to true to see the agent's thinking in the console
})

// 6. Exported function used by the UI
export async function runAgent(input: string): Promise<string> {
  const result = await agentExecutor.invoke({ input })
  return result.output
}
```

Add your API key to `.env`:
```
VITE_GEMINI_API_KEY=your_key_here
```

---

## 8. What LangChain Is Doing For You

Without LangChain, you would have to write the tool-calling loop yourself (like in the Python example). LangChain handles:

| What LangChain handles | What you would otherwise write |
|-----------------------|-------------------------------|
| Formatting tool schemas for the LLM | Manual JSON schema writing |
| Detecting when the model wants to call a tool | Parsing `stop_reason === "tool_use"` |
| Running the tool and sending results back | The message loop |
| Looping until the model gives a final answer | `for step in range(max_steps)` |
| Memory across turns | Managing the message history array |

LangChain is an abstraction layer — useful for getting started quickly. As you go deeper, you may want to drop it and write the loop yourself for more control.

---

## 9. Demonstrating the Agent

### Test 1 — Wikipedia Tool
```
You: What is the Indian Super League?
```
The agent calls `wikipedia("Indian Super League")`, gets the article summary, and answers with real information.

### Test 2 — Time Tool
```
You: What time is it right now?
```
The agent calls `get_current_time()` and returns the current IST time.

### Test 3 — Reasoning Without Tools
```
You: What is 15% of 8400?
```
The model answers directly — it does not need a tool for simple maths.

You will see in the console (with `verbose: true`) exactly which tools were called and what they returned.

---

## 10. Pushing the Project to GitHub with the Agent

One of the demos in class: having the agent push its own code to GitHub.

To add a GitHub tool, install the Octokit SDK:
```bash
npm install @octokit/rest
```

Create a custom tool:
```typescript
import { Octokit } from '@octokit/rest'
import { DynamicStructuredTool } from '@langchain/core/tools'
import { z } from 'zod'

const octokit = new Octokit({ auth: process.env.GITHUB_TOKEN })

const githubTool = new DynamicStructuredTool({
  name: 'create_github_repo',
  description: 'Creates a new GitHub repository and pushes a file to it',
  schema: z.object({
    repoName: z.string().describe('Name of the repository'),
    fileName: z.string().describe('Name of the file to create'),
    content: z.string().describe('Content of the file')
  }),
  func: async ({ repoName, fileName, content }) => {
    // Create repo
    await octokit.repos.createForAuthenticatedUser({ name: repoName, auto_init: true })

    // Encode content to base64
    const encoded = Buffer.from(content).toString('base64')

    // Push file
    await octokit.repos.createOrUpdateFileContents({
      owner: 'your-username',
      repo: repoName,
      path: fileName,
      message: `Add ${fileName}`,
      content: encoded
    })

    return `Repository '${repoName}' created and '${fileName}' pushed successfully.`
  }
})
```

---

## 11. Converting to a Desktop App with Electron

If you want the agent to access local files or run terminal commands, wrap the web app in **Electron** — a framework that turns any web app into a native desktop application.

```bash
npm install --save-dev electron electron-builder
```

Add to `package.json`:
```json
{
  "main": "electron/main.js",
  "scripts": {
    "electron": "electron .",
    "build:desktop": "vite build && electron-builder"
  }
}
```

Create `electron/main.js`:
```javascript
const { app, BrowserWindow } = require('electron')
const path = require('path')

app.whenReady().then(() => {
  const win = new BrowserWindow({
    width: 1200,
    height: 800,
    webPreferences: { nodeIntegration: true }
  })
  win.loadURL('http://localhost:5173')  // Your Vite dev server
})
```

Run it:
```bash
npm run dev        # Start Vite
npm run electron   # Open in Electron
```

Now the agent runs as a desktop app and can, in principle, access the file system and run system commands through Node.js.

---

## 12. Using Claude Code / Codex During Development

As shown in class — you do not have to write all this code manually. Use AI coding tools to generate and debug it:

- **Claude Code** (used in the demo): runs in the terminal, reads your project files, and writes code based on your instructions
- **Codex (OpenAI)**: similar capability through ChatGPT
- **Cursor**: AI-first code editor that understands your full codebase

**Workflow used in class**:
1. Describe what you want: *"Set up a TypeScript React project with LangChain and Gemini"*
2. AI generates the boilerplate
3. Describe the next step: *"Add a Wikipedia tool and wire it to the agent executor"*
4. AI adds it
5. Run, see the error, paste it back to the AI, repeat

This is vibe coding (Class 4) applied to agent development.

---

## Key Terms to Remember

| Term | Meaning |
|------|---------|
| **AI Agent** | A system that takes a goal and acts autonomously using tools |
| **LangChain** | A framework that handles the LLM loop, tool parsing, and memory |
| **AgentExecutor** | LangChain's class that runs the think → act → observe loop |
| **DynamicTool** | A LangChain tool defined with a custom function |
| **Gemini 1.5 Flash** | Google's fast, free-tier accessible LLM used in this project |
| **Tool calling** | The model's ability to request that a function be run |
| **agent_scratchpad** | LangChain's placeholder where tool call history is tracked |
| **Electron** | Framework to wrap a web app into a desktop application |
| **verbose mode** | Setting that prints the agent's step-by-step reasoning to the console |

---

[Back to Class 7](README.md) | [Back to Course Index](../../README.md)
