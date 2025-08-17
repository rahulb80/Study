# Resources
## Code Resources
- LangChain Official Documentation
  - https://python.langchain.com/docs/introduction/
    
- LangChain Udemy Course - Code Resources file
  - https://github.com/emarco177?tab=repositories
  - Details of the code repo are at :
      - https://github.com/rahulb80/Study/blob/main/AI%20Notes/LangChain%20Udemy%20Course%20-%20Code%20Resources.md
    
# Packages
- dotenv package method load_dotenv
  - Used to fetch environment variables
- LangChain package
  - hub
  - community
- langchain_openai package
  - ChatOpenAI class,
- langchain.prompts.prompt package
  - PromptTemplate class
- langchain_core.tools package
  - Tool class
- langchain.agents package
  - create_react_agent
  - AgentExecutor      
- LangChain chat models,
- LLM chains

# Tools 
- Free LLM
  - Gemini Vertex AI - Get Free $300 credit for using LLM
- List of LLMs
  - GPT4o mini  
  - GPT 3.5
  - GPT 4 Turbo
  - Gemini 1.5
  - Anthropic Sonnet
# AI Terms
### Agent (AI Agent): 
  An AI agent is an autonomous system that uses an LLM to perceive its environment, make decisions, and take actions towards achieving a specific goal, often leveraging external tools.
### Large Language Model (LLM): 
  A large language model is a deep learning model trained on a massive dataset of text, capable of understanding, generating, and processing human language.
### Tools (AI Agents): 
  In the context of AI agents, tools are external functions or resources (like APIs or databases) that an agent can utilize to interact with its environment and perform actions beyond its core LLM capabilities.
### Tasks (AI Agents): 
  Tasks are the specific objectives or actions that an AI agent is designed to achieve, ranging from simple information retrieval to complex multi-step processes like planning or problem-solving.
### ReAct Agent 
### Output parser
### Chain of thoughts Prompting
### composition of a prompt
- Output indicator

# Useful Prompts
## hwchase17/react
This prompt is sent to LLM along with agents that LLM can use for to take specific actions. It also takes scratchpad, which is kind of history of what happened until now with Agent so far. It will return an answer may be a final answer that the agent finished his job and we have the answer, Or it's going to be which tools that we need to invoke now with which arguments.


# Code Examples
## LangChain Tool 
- has properties 
  - Name
	- function that LLM is going to call
	- Description - apt description that will guide LLM to use this tool in appropriate scenario

```tools_for_agent = [
        Tool(
            name="Crawl Google 4 linkedin profile page",
            func=get_profile_url_tavily,
            description="useful for when you need get the Linkedin Page URL",
        )     
    ]
```
Agent Code : 

```
react_prompt = hub.pull("hwchase17/react")
agent = create_react_agent(llm=llm, tools=tools_for_agent, prompt=react_prompt)
agent_executor = AgentExecutor(agent=agent, tools=tools_for_agent, verbose=True)

result = agent_executor.invoke(
        input={"input": prompt_template.format_prompt(name_of_person=name)}
    )
```

So we have our prompt, then we have here our agent.
This Agent basically holds the way we want to communicate with the LLM and which tools that we have, and then how to parse the outputs that we get from the LLM.

Now to execute the Agent will LLM to get our output, we provide it the runtime : how to run in loops, etc.
So we want to create something which is called an AgentExecutor.
It's going to receive that agent, it's going to receive a list of tools because those are actually the tools that will be invoked. And we want to supply verbose equals true, so we'll see extensive logging and we'll understand a bit more how this agent is working.

> Why do we need to create a react agent and then create from it an agent executor.
But you can think about it as the agent is going to be the recipe, what we're sending to the LM and
getting back to it and parsing it.
But the agent executor is going to be responsible for orchestrating all of this and to be actually invoking those Python functions.

At last, we will invoke the agent_executor by calling the invoke method on it. 
` agent_executor.invoke() `

> Complete code for this is at URL : https://github.com/emarco177/IceBreaker/blob/main/agents/linkedin_lookup_agent.py
