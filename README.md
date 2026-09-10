# PolyModel: Multi-Model Self-Consistency Engine

PolyModel is a modern, responsive web dashboard and orchestration backend designed to run self-consistency algorithms across multiple Large Language Models (LLMs) in parallel. 

It queries **OpenAI (GPT-4o)**, **Groq (Llama-3.3)**, and **OpenRouter** simultaneously, cross-references their outputs, and runs a meta-evaluation synthesis algorithm to compile the final, most reliable response.

---

## Key Features

* **Multi-Model Consensus**: Compiles answers from independent LLM endpoints in parallel to eliminate hallucinations.
* **Consensus Synthesis**: Evaluates and synthesizes raw model outputs into a single cohesive response.
* **Premium Responsive UI**: Built with a sleek orange-and-white visual identity that transitions smoothly between:
  - **Dark Mode**: High-contrast slate theme with glowing sunset highlights.
  - **Light Mode**: Softer warm off-white and terracotta palettes to reduce eye strain.
* **Custom Toggle Switch**: Features a custom sun/moon toggle knob that changes styles and slides interactively.
* **Interactive Timeline Loader**: Shows a step-by-step query status progress panel with a dedicated **Stop** button to abort ongoing requests immediately.
* **Developer Quick Examples**: Preset prompt buttons focusing on web-dev concepts like JWT, JavaScript Debouncing, and API design comparisons.
* **Keyboard Shortcut**: Pressing `Enter` in the prompt area automatically triggers evaluation (while `Shift + Enter` inserts a new line).
* **Local History Log**: Retains past queries in a sidebar for single-click reloads and lets you clear them instantly.

---

## Tech Stack

* **Backend**: Node.js, Express, TypeScript, TSX
* **Frontend**: Vanilla HTML5, CSS Custom Properties (Variables), Vanilla JavaScript
* **Libraries**: `marked.js` (Markdown parsing), `FontAwesome` (Vector icons)

---

## Prerequisites

To run this project, you will need active API keys for:
1. **OpenAI API Key** (e.g. for GPT-4o)
2. **Groq API Key** (e.g. for Llama models)
3. **OpenRouter API Key** (for open-source models)

---

## Local Setup

1. **Clone the Repository**:
   ```bash
   git clone <your-repository-url>
   cd self-consistency
   ```

2. **Install Dependencies**:
   ```bash
   npm install
   ```

3. **Configure Environment Variables**:
   - Copy the environment template file:
     ```bash
     cp .env.example .env
     ```
   - Open the new `.env` file and replace the placeholders with your actual API keys:
     ```env
     PORT=3000
     OPENAI_API_KEY=your_openai_api_key_here
     GROQ_API_KEY=your_groq_api_key_here
     OPENROUTER_API_KEY=your_openrouter_api_key_here
     ```

4. **Run Development Server**:
   ```bash
   npm run dev
   ```
   Open your browser and navigate to **`http://localhost:3000`**.

---

## Deployment

### Option 1: Vercel (Serverless)
This project is pre-configured to run out-of-the-box on Vercel:
* **Configured Routing**: `vercel.json` routes all requests dynamically to the serverless function.
* **Graceful In-Memory History**: In read-only serverless environments, history logs fall back gracefully to memory instead of writing to disk (`history.json`), avoiding runtime errors.

**Steps to Deploy**:
1. Import your GitHub repository to the [Vercel Dashboard](https://vercel.com).
2. Add your `OPENAI_API_KEY`, `GROQ_API_KEY`, and `OPENROUTER_API_KEY` under the **Environment Variables** section.
3. Click **Deploy**.

### Option 2: Render or Railway (Persistent Node Server)
If you want persistent local history files (`history.json`), you can deploy to Render or Railway:
* **Build Command**: `npm install && npm run build`
* **Start Command**: `npm start`
* Configure environment variables in the service dashboard.
