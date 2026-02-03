# AI Research Assistant Agent

An AI-powered research assistant built with **LangChain** that can search the web, query Wikipedia, and save structured research results to a file using tool-calling agents.

This project demonstrates how to build a **tool-using AI agent** that produces **structured, machine-readable output** using `Pydantic`.

---

## Features

* Tool-calling AI agent powered by **OpenAI GPT**
* Web search using **DuckDuckGo**
* Wikipedia lookup for quick factual references
* Structured responses enforced with **Pydantic**
* Ability to save research outputs to a text file
* Designed as a reusable research assistant pattern

---

## Architecture Overview

The agent follows this flow:

1. User provides a research query
2. AI agent decides which tools to use
3. Tools fetch external information (web / Wikipedia)
4. AI compiles results into a structured schema
5. Output can optionally be saved to disk

```
User → Agent → Tools (Search / Wiki / Save) → Structured Output
```

---

## Project Structure

```
.
├── main.py           # Agent setup and execution
├── tools.py          # Custom and community tools
├── requirements.txt  # Project dependencies
├── .env              # API keys (not committed)
```

---

## Structured Output Schema

The agent always responds using the following schema:

```python
class ResearchResponse(BaseModel):
    topic: str
    summary: str
    sources: list[str]
    tools_used: list[str]
```

This ensures the output is predictable and easy to store, parse, or extend.

---

## Tools Used

| Tool              | Description                               |
| ----------------- | ----------------------------------------- |
| DuckDuckGo Search | Searches the web for relevant information |
| Wikipedia Tool    | Fetches concise factual summaries         |
| Save Tool         | Saves research output to a `.txt` file    |

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/ojeyelizaphan/AI-Research-Assistant-Agent.git
cd ai-research-agent
```

---

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
```

---

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

### 4. Set up environment variables

Create a `.env` file in the root directory:

```env
OPENAI_API_KEY=your_openai_api_key
```

> ⚠️ Make sure `.env` is added to `.gitignore`

---

### 5. Run the agent

```bash
python main.py
```

You’ll be prompted with:

```
What can i help you research?
```

---

## Example Output

```json
{
  "topic": "Quantum Computing",
  "summary": "Quantum computing leverages quantum mechanics to perform computations...",
  "sources": [
    "Wikipedia",
    "DuckDuckGo Search"
  ],
  "tools_used": [
    "search",
    "wikipedia",
    "save_text_to_file"
  ]
}
```

---

## Technologies Used

* Python
* LangChain
* OpenAI GPT
* Pydantic
* DuckDuckGo Search
* Wikipedia API
* dotenv

---

## Future Improvements

* Add citation URLs instead of source names
* Export results as JSON or Markdown
* Add streaming responses
* Add memory for multi-step research
* Build a web or CLI interface

---

## Acknowledgements

* [LangChain](https://www.langchain.com/)
* OpenAI
* DuckDuckGo
* Wikipedia

---

## License

MIT License — free to use, modify, and distribute.

---
