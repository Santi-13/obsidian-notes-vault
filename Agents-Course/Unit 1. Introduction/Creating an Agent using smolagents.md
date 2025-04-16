#HuggingFace #Unit1
#### By: Hugging Face
---
In the last section, we learned how we can create Agents from scratch using Python code, and we **saw just how tedious that process can be**. Fortunately, many Agent libraries simplify this work by **handling much of the heavy lifting for you**.

In this tutorial, **you’ll create your very first Agent** capable of performing actions such as image generation, web search, time zone checking and much more!
## What is smolagents?
To make this Agent, we’re going to use `smolagents`, a library that **provides a framework for developing your agents with ease**.

This lightweight library is designed for simplicity, but it abstracts away much of the complexity of building an Agent, allowing you to focus on designing your agent’s behavior.

In short, `smolagents` is a library that focuses on **codeAgent**, a kind of agent that performs **“Actions”** through code blocks, and then **“Observes”** results by executing the code.

## Let’s build our Agent!

To start, duplicate this Space: [https://huggingface.co/spaces/agents-course/First_agent_template](https://huggingface.co/spaces/agents-course/First_agent_template)

Duplicating this space means **creating a local copy on your own profile**:

![Duplicate](https://huggingface.co/datasets/agents-course/course-images/resolve/main/en/unit1/duplicate-space.gif)

After duplicating the Space, you’ll need to add your Hugging Face API token so your agent can access the model API:

1. First, get your Hugging Face token from [https://hf.co/settings/tokens](https://hf.co/settings/tokens) with permission for inference, if you don’t already have one
2. Go to your duplicated Space and click on the **Settings** tab
3. Scroll down to the **Variables and Secrets** section and click **New Secret**
4. Create a secret with the name `HF_TOKEN` and paste your token as the value
5. Click **Save** to store your token securely

Throughout this lesson, the only file you will need to modify is the (currently incomplete) **“app.py”**. You can see here the [original one in the template](https://huggingface.co/spaces/agents-course/First_agent_template/blob/main/app.py). To find yours, go to your copy of the space, then click the `Files` tab and then on `app.py` in the directory listing.

You can check the agent working in the `App` tab. First we start by importing some important libraries:
```python
from smolagents import CodeAgent, DuckDuckGoSearchTool, FinalAnswerTool, HfApiModel, load_tool, tool
import datetime
import requests
import pytz
import yaml
```
### The Tools
Now let’s get into the tools! 

```python
@tool
def my_custom_tool(arg1:str, arg2:int)-> str: # it's important to specify the return type
    # Keep this format for the tool description / args description but feel free to modify the tool
    """A tool that does nothing yet 
    Args:
        arg1: the first argument
        arg2: the second argument
    """
    return "What magic will you build ?"

@tool
def get_current_time_in_timezone(timezone: str) -> str:
    """A tool that fetches the current local time in a specified timezone.
    Args:
        timezone: A string representing a valid timezone (e.g., 'America/New_York').
    """
    try:
        # Create timezone object
        tz = pytz.timezone(timezone)
        # Get current time in that timezone
        local_time = datetime.datetime.now(tz).strftime("%Y-%m-%d %H:%M:%S")
        return f"The current local time in {timezone} is: {local_time}"
    except Exception as e:
        return f"Error fetching time for timezone '{timezone}': {str(e)}"
```

### The Agent

It uses [`Qwen/Qwen2.5-Coder-32B-Instruct`](https://huggingface.co/Qwen/Qwen2.5-Coder-32B-Instruct) as the LLM engine. This is a very capable model that we’ll access via the serverless API.

```python
final_answer = FinalAnswerTool()
model = HfApiModel(
    max_tokens=2096,
    temperature=0.5,
    model_id='Qwen/Qwen2.5-Coder-32B-Instruct',
    custom_role_conversions=None,
)

with open("prompts.yaml", 'r') as stream:
    prompt_templates = yaml.safe_load(stream)
    
# We're creating our CodeAgent
agent = CodeAgent(
    model=model,
    tools=[final_answer], # add your tools here (don't remove final_answer)
    max_steps=6,
    verbosity_level=1,
    grammar=None,
    planning_interval=None,
    name=None,
    description=None,
    prompt_templates=prompt_templates
)

GradioUI(agent).launch()
```