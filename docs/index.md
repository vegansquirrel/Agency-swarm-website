# Agency Swarm Cookbook

An open scource project created by [VRSEN AI](https://www.vrsen.ai/)


## Introduction

- What is Agency Swarm?

Agency Swarm is an open-source agent orchestration framework designed to automate and streamline AI development processes. Leveraging the power of the OpenAI Assistants API, it enables the creation of a collaborative swarm of agents (Agencies), each with distinct roles and capabilities. This framework aims to replace traditional AI development methodologies with a more dynamic, flexible, and efficient agent-based system.

- Goal of the project
Allow people to create their agencies with AI and build a self expanding system, that grows with each contribution

- Agency Swarm vs Other Frameworks

Differences between agency swarm and Autogen.

## Differences between Autogen and Agency swarm.

AutoGen recreated from scratch using just five or six functions with the new OpenAI Assistants API. Here is their famous example, featuring a chart of YTD, Meta, and Tesla stock prices, that was made by this system, consisting of just 2 agents: a coding assistant and a user proxy agent. But the best part is that this system is much more controllable and customizable, which means unlike autogen, it is actually deployable in production.

Agency Swarm does not write prompts for you
- It includes automatic type checking with instructor
- It is build on top of the latest OpenAI Assistants API (OpenAI is extremely likely to include more exciting features soon)
- It allows you to easily define communication flows

## Quick Start

- Short description of how to install and create a simple agency with simple tools

### [Assistant API](https://platform.openai.com/docs/assistants/overview/agents)  working

The [Assistant API](https://platform.openai.com/docs/assistants/overview/agents) working is quite different from the previous chat completions approach. In this new api, there are threads that represent conversations, messages that represent individual messages within the threads, and agents that execute the threads to generate new messages.
I know it can be confusing. So, the general process is as follows: 

1. First, you have to create an agent. 
2. Then, you have to create a thread. 
3. Next, you have to add a message to the thread. 
4. After that, you have create a run for this thread and agent ids. 
The big change here is that runs execute asynchronously, so you have to continuously check for the updates until the run is finished. 
5. And finally, once that's done, if the run is in completed status, the run goes into requires_action or completed status. 

## Installation

```python
pip install agency-swarm
```

### Getting Started

1. **Set Your OpenAI Key**:

```python
from agency_swarm import set_openai_key
set_openai_key("YOUR_API_KEY")
```

### Advanced Tools

- Brief explanation on how to create tools with [Instuctor](https://github.com/jxnl/instructor)
- Some tool examples would be cool
- How to use ToolFactory class to convert openai schemas into tools or import langchain tools with examples

2. **Create Tools**: Define your custom tools with [Instructor](https://github.com/jxnl/instructor):

[github]
Convert from OpenAPI schemas:

### Agent Roles:

Start by defining the roles of your agents. For example, a CEO agent for managing tasks and a developer agent for executing tasks.

```py 
from agency_swarm import Agent

ceo = Agent(name="CEO",
            description="Responsible for client communication, task planning and management.",
            instructions="You must converse with other agents to ensure complete task execution.", # can be a file like ./instructions.md
            files_folder="./files", # files to be uploaded to OpenAI
            schemas_folder="./schemas", # OpenAPI schemas to be converted into tools
            tools=[MyCustomTool, LangchainTool])
```

Import from existing agents: