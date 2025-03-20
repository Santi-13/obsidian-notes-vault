#HuggingFace #AI
#### By: Hugging Face
---
# What are Tools?
One crucial aspect of AI Agents is their ability to take **actions**. As we saw, this happens through the use of **Tools**.

In this section, we’ll learn what Tools are, how to design them effectively, and how to integrate them into your Agent via the System Message.
## What are AI Tools?
A **Tool is a function given to the LLM**. This function should fulfill a **clear objective**. Some commonly used tools in AI agents are:

| Tool             | Description                                                         |
| ---------------- | ------------------------------------------------------------------- |
| Web Search       | Allows the agent to fetch up-to-date information from the internet. |
| Image Generation | Creates images based on text descriptions.                          |
| Retrieval        | Retrieves information from an external source.                      |
| API Interface    | Interacts with an external API (GitHub, YouTube, Spotify, etc.).    |
The beauty is that we can create a tool for any use case, but a **good tool** should be something that **complements the power of an LLM**.
