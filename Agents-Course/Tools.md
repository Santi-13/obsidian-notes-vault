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

Furthermore, **LLMs predict the completion of a prompt based on their training data**, which means that their internal knowledge only includes events prior to their training. Therefore, if your agent needs up-to-date data you must provide it through some tool.

- A Tool should contain:
    - A **textual description of what the function does**.
    - A _Callable_ (something to perform an action).
    - _Arguments_ with typings.
    - (Optional) Outputs with typings.

## How do tools work?
What we mean when we talk about _providing tools to an Agent_, is that we **teach** the LLM about the existence of tools, and ask the model to generate text that will invoke tools when it needs to.

The LLM will generate _text_, in the form of code, to invoke that tool. It is the responsibility of the **Agent** to parse the LLM’s output, recognize that a tool call is required, and invoke the tool on the LLM’s behalf. The output from the tool will then be sent back to the LLM, which will compose its final response for the user.

