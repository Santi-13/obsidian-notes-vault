#HuggingFace #Unit2
#### By: Hugging Face
---
Code agents are the default agent type in `smolagents`. They generate Python tool calls to perform actions, achieving action representations that are efficient, expressive, and accurate.

Their streamlined approach reduces the number of required actions, simplifies complex operations, and enables reuse of existing code functions. `smolagents` provides a lightweight framework for building code agents, implemented in approximately 1,000 lines of code.

Their streamlined approach reduces the number of required actions, simplifies complex operations, and enables reuse of existing code functions. `smolagents` provides a lightweight framework for building code agents, implemented in approximately 1,000 lines of code.

![Code vs JSON Actions](https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/transformers/code_vs_json_actions.png)

If you want to learn more about why code agents are effective, check out [this guide](https://huggingface.co/docs/smolagents/en/conceptual_guides/intro_agents#code-agents) from the smolagents documentation.

## Why Code Agents?
In a multi-step agent process, the LLM writes and executes actions, typically involving external tool calls. Traditional approaches use a JSON format to specify tool names and arguments as strings, **which the system must parse to determine which tool to execute**.

However, research shows that **tool-calling LLMs work more effectively with code directly**. This is a core principle of `smolagents`, as shown in the diagram above from [Executable Code Actions Elicit Better LLM Agents](https://huggingface.co/papers/2402.01030).

Writing actions in code rather than JSON offers several key advantages:

- **Composability**: Easily combine and reuse actions
- **Object Management**: Work directly with complex structures like images
- **Generality**: Express any computationally possible task
- **Natural for LLMs**: High-quality code is already present in LLM training data

## How Does a Code Agent Work?

![From https://huggingface.co/docs/smolagents/conceptual_guides/react](https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/smolagents/codeagent_docs.png)

The diagram above illustrates how `CodeAgent.run()` operates, following the ReAct framework we mentioned in [[Internal Reasoning and Re-Act Approach|Unit 1]]. The main abstraction for agents in `smolagents` is a `MultiStepAgent`, which serves as the core building block. `CodeAgent` is a special kind of `MultiStepAgent`, as we will see in an example below.

A `CodeAgent` performs actions through a cycle of steps, with existing variables and knowledge being incorporated into the agent’s context, which is kept in an execution log:

1. The system prompt is stored in a `SystemPromptStep`, and the user query is logged in a `TaskStep`.

2. Then, the following while loop is executed:
	21. Method `agent.write_memory_to_messages()` writes the agent’s logs into a list of LLM-readable [chat messages](https://huggingface.co/docs/transformers/main/en/chat_templating).
	22. These messages are sent to a `Model`, which generates a completion.
	23. The completion is parsed to extract the action, which, in our case, should be a code snippet since we’re working with a `CodeAgent`.
	24. The action is executed.
	25. The results are logged into memory in an `ActionStep`.

At the end of each step, if the agent includes any function calls (in `agent.step_callback`), they are executed.
