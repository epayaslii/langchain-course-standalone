# LangChain Hello World

A minimal LangChain example: a `PromptTemplate` piped into a chat model to turn a block of biographical text into a short summary and two interesting facts.

## What it does

`main.py` builds a prompt template that takes an `{information}` variable, asks for a summary plus two facts about it, and pipes the template into a chat model (`prompt | llm`). The LLM is swappable — `ChatGoogleGenerativeAI`, `ChatOllama`, and `ChatOpenAI` are all imported; uncomment whichever one you want to use.

## Running

```bash
uv sync
uv run python main.py
```

Needs whichever credential matches the LLM you have active — `GOOGLE_API_KEY` for Gemini, `OPENAI_API_KEY` for OpenAI — in a `.env` file, or a local Ollama instance running for `ChatOllama`.

## Acknowledgements

This project was built while following Eden Marco's [LangChain](https://commencis.udemy.com/course/langchain/learn/lecture/49043719?learning_path_id=7785136#content) Udemy course, based on his original [langchain-course](https://github.com/emarco177/langchain-course) repository.
