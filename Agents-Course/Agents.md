#HuggingFace #AI
#### By: Hugging Face
---
## What are they?
Formally put:
	*"An **agent** is a system that leverages an AI model to interact with its environment in order to achieve a user-defined objective. It combines reasoning, planning, and the execution of actions (often via external tools) to fulfill tasks."*

They have two main parts:

 1. **The Brain (AI Model)**
This is where all the thinking happens. The AI model **handles reasoning and planning**. It decides **which Actions to take based on the situation**.
2. **The Body (Capabilities and Tools)**
This part represents **everything the Agent is equipped to do**.

The **scope of possible actions** depends on what the agent **has been equipped with**. For example, because humans lack wings, they can’t perform the “fly” **Action**, but they can execute **Actions** like “walk”, “run”, “jump”, “grab”, and so on.

## What type of AI Models do we use for Agents?
The most common **AI model** found in **agents** are **LLM** (*Large Language Model*), which take ***Text*** as an input and outputs ***Text*** as well. We may also use *Vision Language Models* (**VLM**), but we will focus on **LLMs**.

## How does an AI take action on its environment?
Although **LLMs** can only generate text, developers have found ways to add additional functionality (called ***Tools***) to their AI models. Basically:
__
	An Agent can perform ANY tasl we implement via Tools to complete Actions
__