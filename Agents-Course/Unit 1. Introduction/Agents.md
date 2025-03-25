#HuggingFace #AI
#### By: Hugging Face
---
## What are they?
Formally put:

>  *"An **agent** is a system that leverages an AI model to interact with its environment in order to achieve a user-defined objective. It combines reasoning, planning, and the execution of actions (often via external tools) to fulfill tasks."*

They have two main parts:

1. **The Brain (AI Model)**
	This is where all the thinking happens. The AI model **handles reasoning and planning**. It decides **which Actions to take based on the situation**.

2. **The Body (Capabilities and Tools)**
	This part represents **everything the Agent is equipped to do**.

The **scope of possible actions** depends on what the agent **has been equipped with**. For example, because humans lack wings, they can’t perform the “fly” **Action**, but they can execute **Actions** like “walk”, “run”, “jump”, “grab”, and so on.

## What type of AI Models do we use for Agents?
The most common **AI model** found in **agents** are **LLM** (*Large Language Model*), which take ***Text*** as an input and outputs ***Text*** as well. We may also use *Vision Language Models* (**VLM**), but we will focus on **LLMs**.

## How does an AI take action on its environment?
Although **LLMs** can only generate text, developers have found ways to add additional functionality (called ***Tools***) to their AI models. Basically,	an **Agent** can perform **ANY** task we implement via **Tools** to complete **Actions**.

For example, if I write an Agent to act as my personal assistant (like Siri) on my computer, and I ask it to “send an email to my Manager asking to delay today’s meeting”, I can give it some code to send emails. This will be a new Tool the Agent can use whenever it needs to send an email. We can write it in Python:

```python
def send_message_to(recipient, message):
    """Useful to send an e-mail message to a recipient"""
    ...
```

The **design of the Tools is very important and has a great impact on the quality of your Agent**. Some tasks will require very specific Tools to be crafted, while others may be solved with general purpose tools like “web_search”.

# Flashcards
---
**What is an agent?**:: A system that leverages an AI model to interact with its environment to achieve a user-defined objective, combining reasoning, planning, and execution of actions.
<!--SR:!2025-03-28,3,250-->

**What are the two main parts of an agent?**:: The Brain (AI Model) and the Body (Capabilities and Tools).
<!--SR:!2025-03-26,1,230-->

**What does the Brain of an agent do?**:: It handles reasoning and planning, deciding which actions to take based on the situation.
<!--SR:!2025-03-26,1,230-->

**What type of AI model is most commonly used in agents?**:: Large Language Models (LLMs), which take text as input and output text.
<!--SR:!2025-03-26,1,230-->

**How can an AI agent take action on its environment?**:: By using additional functionality called Tools, which allow the agent to perform tasks beyond just generating text.
<!--SR:!2025-03-28,3,250-->