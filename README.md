# LangChain Agents 🦜🔗

A collection of standalone LangChain / LangGraph agent projects. Each project lives on its own branch — `main` only holds this README, the license, and shared logo assets.

![LangChain Logo](/static/LangChain_OSS%20Lockup_light.png)
![LangGraph Logo](/static/LangGraph_OSS%20Lockup_light.png)

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)

## Branches

| Branch | What it does |
|---|---|
| [`project/hello-world`](https://github.com/epayaslii/langchain-course/tree/project/hello-world) | Minimal LangChain example: builds a prompt template and sends it to an LLM (Gemini/Ollama/OpenAI, swappable) to summarize a block of text into a short summary plus two facts. |
| [`project/search-agent`](https://github.com/epayaslii/langchain-course/tree/project/search-agent) | A LangChain v1 `create_agent` agent equipped with Tavily web search as a tool, returning a structured response (answer + list of source URLs) via a Pydantic schema. |
| [`project/agents-under-the-hood`](https://github.com/epayaslii/langchain-course/tree/project/agents-under-the-hood) | The same tool-calling agent loop implemented three ways at decreasing levels of abstraction, to show what an "agent" is actually doing under the hood: (1) LangChain's `@tool` decorator + `init_chat_model`, (2) the same loop hand-written against Ollama's raw function-calling API with no LangChain, (3) the same loop again with no function-calling API at all — tool calls are parsed out of raw ReAct-style text completions. |
| [`project/documentation-helper`](https://github.com/epayaslii/langchain-course/tree/project/documentation-helper) | A RAG chatbot that answers questions about LangChain's docs. `ingestion.py` crawls `python.langchain.com` with Tavily, chunks and embeds the pages, and stores them in a local Chroma vector store. `backend/core.py` wires a LangChain agent to a retrieval tool over that store, and `main.py` is a Streamlit chat UI on top of it. |

## Getting started

```bash
git clone https://github.com/epayaslii/langchain-course
cd langchain-course
git checkout project/<name>   # e.g. project/hello-world
uv sync
uv run python main.py
```

Each branch has its own `pyproject.toml`/`.env` requirements — check that branch's own README for specifics (API keys needed, etc.).
