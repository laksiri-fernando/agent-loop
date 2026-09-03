# Loop Agent

A tiny open-source demo of a self-correcting multi-agent workflow built with FastAPI, LangGraph, LangChain, and Groq.

The app runs a simple Writer → Reviewer → Reviser agent loop to generate an explanation for any topic, then refines it until the reviewer approves or the revision limit is reached.

## Features

- FastAPI web UI for running the agent workflow from the browser
- Structured multi-agent loop with separate writer, reviewer, and reviser roles
- Groq Llama model integration via `langchain-groq`
- Demo-friendly free-tier setup and local execution

## Contents

- `app.py` — FastAPI application and web endpoint
- `backend.py` — agent workflow graph and core loop logic
- `templates/index.html` — browser interface
- `static/app.js` — client-side interaction and results rendering
- `static/style.css` — demo styling
- `requirements.txt` — Python dependencies

## Requirements

- Python 3.11+
- A Groq API key configured in a `.env` file
- `pip` installed

## Installation

```bash
conda create -n loop-agent python=3.11 -y
conda activate loop-agent
pip install -r requirements.txt
```

## Configuration

Create a `.env` file in the project root with the following values:

```env
GROQ_API_KEY=your_groq_api_key
GROQ_MODEL=llama-3.3-70b-versatile
MAX_REVISIONS=2
```

- `GROQ_API_KEY` — required API key for Groq
- `GROQ_MODEL` — model name to use (default: `llama-3.3-70b-versatile`)
- `MAX_REVISIONS` — number of revisions allowed before stopping the loop

## Running locally

```bash
python app.py
```

Then open `http://127.0.0.1:8000` in your browser.

## Usage

1. Enter a topic or question into the UI.
2. Click **Run Agent Loop**.
3. Watch the writer, reviewer, and reviser produce and improve the final answer.

The backend returns a structured workflow trace plus the accepted answer.

## Project architecture

- `app.py` serves the web UI and exposes `/api/run`
- `backend.py` defines the `StateGraph` workflow and the agent functions:
  - `writer()` generates the first answer
  - `reviewer()` evaluates the draft and decides whether to revise
  - `reviser()` improves the answer when needed
- `run_workflow(topic)` executes the graph and returns the final result

## Contributing

Contributions are welcome! Suggested improvements include:

- adding tests for the workflow and API
- expanding the review rules or reviewer behavior
- supporting additional model providers
- improving the UI or visual trace

## License

This project is provided as-is for learning and experimentation.
