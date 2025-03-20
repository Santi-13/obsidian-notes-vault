#HuggingFace #AI
#### By: Hugging Face
---
## The Core Components
Agents work in a continuous cycle of: **thinking (Thought) → acting (Act) and observing (Observe)**.

Let’s break down these actions together:

1. **Thought**: The LLM part of the Agent decides what the next step should be.
2. **Action:** The agent takes an action, by calling the tools with the associated arguments.
3. **Observation:** The model reflects on the response from the tool.

The three components work together in a continuous loop. To use an analogy from programming, the agent uses a **while loop**: the loop continues until the objective of the agent has been fulfilled.

In many Agent frameworks, **the rules and guidelines are embedded directly into the system prompt**, ensuring that every cycle adheres to a defined logic.

In a simplified version, our system prompt may look like this:

```python
system_message = """You are an AI assistant designed to help users effectively and accurately. Your primary goal is to provide helpful, precise, and clear responses.

You have access to the following tools:
Tool Name: calculator, Description: Multiply two integers., Arguments: a: int, b: int, Outputs: int

You should think step by step in order to fulfill the objective with a reasoning devided in Thought/Action/Observation that can repeat multiple times if needed.

You should first reflect with: 'Thought: {your_thoughts}' on the current situation, then (if necessary), call a tool with the proper JSON formatting 'Action: {JSON_BLOB}', or print your final answer starting with the prefix 'Final Answer:'
"""
```

We see here that in the System Message we defined :
- The _Agent’s behavior_.
- The _Tools our Agent has access to_, as we described in the previous section.
- The _Thought-Action-Observation Cycle_, that we bake into the LLM instructions.

**The interplay of Thought, Action, and Observation empowers AI agents to solve complex tasks iteratively**.