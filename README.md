# 🦜🪞 LangGraph Reflection Agent

This repository contains a reflection-style agent architecture built with LangGraph that improves output quality through self-critique and refinement.

## ✨ Overview

The reflection agent uses a feedback loop between a generation component and a reflection component to iteratively improve responses to user queries. In this implementation, we've created a Twitter assistant that enhances tweets through multiple rounds of critique and revision.

```mermaid
graph LR;
    __start__([__start__]):::first
    generate(generate)
    reflect(reflect)
    __end__([__end__]):::last
    __start__ --> generate;
    generate --> reflect;
    reflect -.-> generate;
    generate -.-> __end__;
    classDef default fill:#f2f0ff,line-height:1.2
    classDef first fill-opacity:0
    classDef last fill:#bfb6fc
```

## 🔄 How It Works

1. **Generate**: The initial component creates a response (in our case, a tweet) based on the user's input
2. **Reflect**: The reflection component evaluates the generated content and provides specific feedback for improvement
3. **Loop**: The generation component refines its output based on the reflection's feedback
4. **Termination**: The process ends after a predetermined number of iterations (currently set to 6)

This approach creates a self-improving system that produces higher quality outputs through deliberate reflection.

## 💻 Installation

```bash
# Clone the repository
git clone https://github.com/epayaslii/langchain-project.git
cd langchain-project
git checkout project/reflection-agent

# Install dependencies using Poetry
poetry install
```

## 📁 Project Structure

```
reflection-agent/
├── chains.py         # Defines the prompt chains for generation and reflection
├── main.py           # Implements the core LangGraph structure
├── pyproject.toml    # Project dependencies and configuration
└── README.md         # This documentation
```

## 🛠️ Implementation Details

### Main Components

The reflection agent is built with two primary nodes:

1. **Generation Node** (in `chains.py`):
   - Uses a specialized prompt for creating Twitter content
   - Responds to critique by refining previously generated content

2. **Reflection Node** (in `chains.py`):
   - Critiques the generated content against quality criteria
   - Provides specific recommendations for improvement

## 🔍 Example Usage

```python
from langchain_core.messages import HumanMessage
from main import graph

# Create input prompt
input_tweet = HumanMessage(content="""Make this tweet better:
@LangChainAI — newly Tool Calling feature is seriously underrated.
After a long wait, it's here- making the implementation of agents across different models with function calling - super easy.
Made a video covering their newest blog post""")

# Run the reflection agent
improved_tweet = graph.invoke(input_tweet)
print(improved_tweet)
```

## 👏 Acknowledgment

This reflection agent implementation is based on the concepts and patterns described in the LangGraph documentation. For more information about reflection agents, visit the [LangGraph Reflection Tutorial](https://langchain-ai.github.io/langgraph/tutorials/reflection/reflection/).

This project was built while following Eden Marco's [LangChain](https://commencis.udemy.com/course/langchain/learn/lecture/49043719?learning_path_id=7785136#content) Udemy course, based on his original [langchain-course](https://github.com/emarco177/langchain-course) repository.
