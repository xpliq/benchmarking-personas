# Testing Personified Prompts vs Instructional Prompts for LLMs
- Personaified Prompts give a role to an LLM
- Instructional Prompts give LLMs a task they follow throughout their response generation
- Personas vs Instruction was motivated from how LLMs consider both when generating responses. Ultimately they follow a similar structure of having the Prompt (Persona or Inst.) as their system prompt throughout all response generation.
- Because both are similar in execution, how different are the two in actual response quality.


### Personified Prompts vs Instructional Prompts Examples
```
Persona
{
    {"role": "system", "content": "You are an expert in App Development with a specialization in JavaScript."},
    {"role": "user", "content": "Write a todo list app in JavaScript."}
} 

Instruction
{
    {"role": "system", "content": "You only know how to develop apps and your responses are to only include JavaScript."},
    {"role": "user", "content": "Write a todo list app in JavaScript."}
}
```

### Personas and Instructions to System Content
Above examples display system roles that have been assigned to the LLM, and the user makes a query with that in mind.
- What if we had an intermediary LLM generate the roles after a user query
```
Example
{
    {"role": "user", "content": "Write a todo list app[1] in JavaScript[2]."}
    {"role": "system", "content": "You are an expert in App Development[1] with a specialization in JavaScript[2]."},
}
```
- This concept is useful for adaptive/dynamic personas and instructions.


# Prompts for Prompt Generation
### Personas
```
"Based on the user query, generate a prompt for an LLM that describes a persona or specialization for the LLM. Something along the lines of  'You are an expert in ___ with a specialization in ___'. Only provide the prompt, do not respond with anything else."
```
### Instruction
```
"Based on the user query, generate an instruction to give to an LLM as a prompt. Something along the lines of 'You must be able to ___'. Ensure that the prompt is an instruction that instructs the LLM to do something related to the user query. Only provide the prompt, do not respond with anything else."
```

# Data

- WikiQA

### Result Mean Values

##### Persona Responses
- rouge1: 0.1540348498741638
- rouge2: 0.04250547528205004
- rougeL: 0.10385418694215125
- rougeLsum: 0.10519427848454284

##### Instruction Responses
- rouge1: 0.1535807634398431
- rouge2: 0.04051400012115329
- rougeL: 0.10121977013988975
- rougeLsum: 0.10370625810853101