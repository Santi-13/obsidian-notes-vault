#HuggingFace #Unit2
#### By: Hugging Face
---
## When to Use an Agentic Framework
An agentic framework is **not always needed when building an application around LLMs**. They provide flexibility in the workflow to efficiently solve a specific task, but they’re not always necessary.

Sometimes, **predefined workflows are sufficient** to fulfill user requests, and there is no real need for an agentic framework. If the approach to build an agent is simple, like a chain of prompts, using plain code may be enough. The advantage is that the developer will have **full control and understanding of their system without abstractions**.

However, when the workflow becomes more complex, such as letting an LLM call functions or using multiple agents, these abstractions start to become helpful.

Considering these ideas, we can already identify the need for some features:

- An _LLM engine_ that powers the system.
- A _list of tools_ the agent can access.
- A _parser_ for extracting tool calls from the LLM output.
- A _system prompt_ synced with the parser.
- A _memory system_.
- _Error logging and retry mechanisms_ to control LLM mistakes. We’ll explore how these topics are resolved in various frameworks, including `smolagents`, `LlamaIndex`, and `LangGraph`.
## Agentic Frameworks Units

| Framework                                                                                | Description                                                           | Unit Author                                                                                                                                                       |
| ---------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [smolagents](https://huggingface.co/learn/agents-course/unit2/smolagents/introduction)   | Agents framework developed by Hugging Face.                           | Sergio Paniego - [HF](https://huggingface.co/sergiopaniego) - [X](https://x.com/sergiopaniego) - [Linkedin](https://www.linkedin.com/in/sergio-paniego-blanco)    |
| [Llama-Index](https://huggingface.co/learn/agents-course/unit2/llama-index/introduction) | End-to-end tooling to ship a context-augmented AI agent to production | David Berenstein - [HF](https://huggingface.co/davidberenstein1957) - [X](https://x.com/davidberenstei) - [Linkedin](https://www.linkedin.com/in/davidberenstein) |
| [LangGraph](https://huggingface.co/learn/agents-course/unit2/langgraph/introduction)     | Agents allowing stateful orchestration of agents                      | Joffrey THOMAS - [HF](https://huggingface.co/Jofthomas) - [X](https://x.com/Jthmas404) - [Linkedin](https://www.linkedin.com/in/joffrey-thomas)                   |