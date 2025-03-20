#HuggingFace #AI
#### By: Hugging Face
---
Now that we understand how LLMs work, let’s look at **how they structure their generations through chat templates**.

Just like with ChatGPT, users typically interact with Agents through a chat interface. Therefore, we aim to understand how LLMs manage chats.

> **Q**: But … When, I’m interacting with ChatGPT/Hugging Chat, I’m having a conversation using chat Messages, not a single prompt sequence
> 
> **A**: That’s correct! But this is in fact a UI abstraction. Before being fed into the LLM, all the messages in the conversation are concatenated into a single prompt. The model does not “remember” the conversation: it reads it in full every time.

Up until now, we’ve discussed prompts as the sequence of tokens fed into the model. But when you chat with systems like ChatGPT or HuggingChat, **you’re actually exchanging messages**. Behind the scenes, these messages are **concatenated and formatted into a prompt that the model can understand**.

This is where chat templates come in. They act as the **bridge between conversational messages (user and assistant turns) and the specific formatting requirements** of your chosen LLM. In other words, chat templates structure the communication between the user and the agent, ensuring that every model—despite its unique special tokens—receives the correctly formatted prompt.

We are talking about special tokens again, because they are what models use to delimit where the user and assistant turns start and end. Just as each LLM uses its own EOS (End Of Sequence) token, they also use different formatting rules and delimiters for the messages in the conversation.

## Messages: The Underlying System of LLMs

### [](https://huggingface.co/learn/agents-course/unit1/messages-and-special-tokens#system-messages)System Messages

System messages (also called System Prompts) define **how the model should behave**. They serve as **persistent instructions**, guiding every subsequent interaction. For example:

```
system_message = {
    "role": "system",
    "content": "You are a professional customer service agent. Always be polite, clear, and helpful."
}
```

When using Agents, the System Message also **gives information about the available tools, provides instructions to the model on how to format the actions to take, and includes guidelines on how the thought process should be segmented.**