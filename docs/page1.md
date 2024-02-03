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