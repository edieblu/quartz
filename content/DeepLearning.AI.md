---
tags:
  - ✅
published: true
sr-due: 2024-10-27
sr-interval: 165
sr-ease: 260
---

⬅️ [[AI]]
Short course from [here](https://learn.deeplearning.ai/)

What are the two types of large language models (LLMs)

- Base LLM (predicts the next word)
- Instruction Tuned LLM (tries to follow instructions)
	- RLHF: Reinforcement Learning with Human Feedback

## Key Principles
- write clear and specific instructions
	- use delimiters (backticks, quotation marks, slashes)
	- ask for structured output (HTML, JSON)
	- check whether conditions are satisfied
	- few-shot prompting (Give successful examples of completing tasks)
- give the model time to think
	- specify the steps to complete a task
	- instruct the mode to work out its own solution before rushing to a conclusion
## Main capabilities
- summarizing
- inferring
- transforming (translating, formatting)
- expanding

## Example of a complex prompt (with delimiters)
![[Pasted image 20240207093425.png]]


## Hallucinations
**🤔 What are hallucinations?**
Makes statements that sound plausible but are not true.

🤔 How do you reduce hallucinations?
- first find relevant information and then answer the question based on the relevant information

## Temperature
- the degree of exploration or randomness of the model
- at a higher temperature (a value between 0 and 1) it might choose one of the less likely following words
- with temperature 0, everytime 

## The Chat Format
- `user` message is the input
- `assistant` message is the output
- `system` role is a high level instructions for the conversation
![[Pasted image 20240207111428.png]]

```python
messages =  [  
{'role':'system', 'content':'You are an assistant that speaks like Shakespeare.'},    
{'role':'user', 'content':'tell me a joke'},   
{'role':'assistant', 'content':'Why did the chicken cross the road'},   
{'role':'user', 'content':'I don\'t know'}  ]
```

