#HuggingFace #AI
#### By: Hugging Face
---
Actions are the concrete steps an **AI agent takes to interact with its environment**.

Whether it’s browsing the web for information or controlling a physical device, each action is a deliberate operation executed by the agent.

For example, an agent assisting with customer service might retrieve customer data, offer support articles, or transfer issues to a human representative.

## Types of Agent Actions
There are multiple types of Agents that take actions differently:

|Type of Agent|Description|
|---|---|
|JSON Agent|The Action to take is specified in JSON format.|
|Code Agent|The Agent writes a code block that is interpreted externally.|
|Function-calling Agent|It is a subcategory of the JSON Agent which has been fine-tuned to generate a new message for each action.|
Actions themselves can serve many purposes:

| Type of Action          | Description                                                           |
| ----------------------- | --------------------------------------------------------------------- |
| Information Gathering   | Performing web searches, querying databases, or retrieving documents. |
| Tool Usage              | Making API calls, running calculations, and executing code.           |
| Environment Interaction | Manipulating digital interfaces or controlling physical devices.      |
| Communication           | Engaging with users via chat or collaborating with other agents.      |

One crucial part of an agent is the **ability to STOP generating new tokens when an action is complete**, and that is true for all formats of Agent: JSON, code, or function-calling. This prevents unintended output and ensures that the agent’s response is clear and precise.

The LLM only handles text and uses it to describe the action it wants to take and the parameters to supply to the tool.