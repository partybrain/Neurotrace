# Neurotrace
# NeuroTrace | Agent Observability Dashboard

NeuroTrace is a lightweight, zero-dependency frontend prototype designed to visualize and monitor multi-step AI agent execution pipelines. Built entirely in vanilla HTML, CSS, and JavaScript, it demonstrates complex agentic architectures—such as ReAct loops, self-correction, and evaluation harnesses—running entirely on the client side.

## 🚀 Live Demo
neurotrace.vercel.app

## ⚡ Core Features

* **Multi-Step ReAct Visualization:** Parses and visually graphs the "Thought → Action → Observation" loop of an AI agent in real-time.
* **LLM-as-a-Judge Evaluation:** Triggers a secondary LLM pipeline to grade the primary agent's output out of 100 based on accuracy and logic.
* **Autonomous Self-Correction:** Automatically triggers a reflection and retry prompt if the Judge LLM scores the initial output below a 75% quality threshold.
* **Failure Mode Classifier:** Intercepts system exceptions (e.g., `JSON_PARSE_ERROR`, `API_LIMIT_OR_AUTH`) and renders graceful fallback UIs rather than crashing the application.
* **Session Memory Context:** Stores and retrieves recent conversational context, automatically injecting it into the agent's system prompt for continuous tasking.
* **Universal Model Compatibility:** A flexible configuration matrix allows runtime hot-swapping between API providers (Groq, OpenAI) and models (Llama 3.1, GPT-4o).
* **Exportable Telemetry:** One-click download of the entire execution trace (including latencies, token counts, and judge critiques) as a structured `.json` file.

## 🛠️ Tech Stack

* **Frontend:** Vanilla HTML5, CSS3, JavaScript (ES6+)
* **Architecture:** Zero-backend client-side API fetching (`fetch`, `async/await`)
* **Styling:** Custom utilitarian CSS with CSS Variables (No frameworks like Tailwind or Bootstrap used)
* **Storage:** Browser `localStorage` for secure API key and session retention

## ⚙️ How to Use

Since this application runs 100% client-side, there are no build steps, dependencies, or local servers required.

1. Clone the repository or simply download the `index.html` file.
2. Open `index.html` in any modern web browser.
3. In the bottom-left **Configuration** panel, enter a valid API Key (e.g., Groq or OpenAI).
4. Type a task into the main input bar and hit **Execute**.
5. *Tip: To see the self-correction loop in action, assign a task and explicitly tell the agent to do it incorrectly (e.g., "What is 2+2? Say it is 5"). The Judge LLM will catch the error and force a reflection sequence.*

## 🔒 Security Note

Your API keys are never transmitted to any external server other than the official LLM provider you select (e.g., `api.groq.com` or `api.openai.com`). Keys are saved locally in your browser's `localStorage` purely for session convenience and are never hardcoded into the source code.
