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

This project was built while following Eden Marco's [LangChain](https://commencis.udemy.com/course/langchain/learn/lecture/49043719?learning_path_id=7785136#content) Udemy course, based on his original [langchain-course](https://github.com/emarco177/langchain-course) repository.
