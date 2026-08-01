# Search Agent

A LangChain v1 agent that answers questions by searching the web with Tavily, and returns a structured, typed response instead of freeform text.

## What it does

`main.py` builds a `create_agent` agent (`ChatOpenAI(model="gpt-5")`) equipped with LangChain's built-in `TavilySearch` tool. The agent's output is constrained to an `AgentResponse` Pydantic model — an `answer` string plus a list of `sources` (each with a `url`) — so every response comes back typed and easy to parse.

The example query in `main()` asks the agent to search LinkedIn for AI engineer job postings in the Bay Area and list their details.

## Running

```bash
uv sync
uv run python main.py
```

Needs `OPENAI_API_KEY` and `TAVILY_API_KEY` in a `.env` file.

## Acknowledgements

This project was built while following Eden Marco's [LangGraph - Develop LLM powered AI agents with LangGraph](https://www.udemy.com/course/langgraph/) Udemy course, based on his original [langgraph-course](https://github.com/emarco177/langgraph-course) repository.
