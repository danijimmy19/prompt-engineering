### Achieving Precise Output Length: Core Principles
- In this lesson, we will learn how to generate precise response tailored in length.
- We can achieve this using thoughtful prompt design and strategic use of model parameters.

**_Understanding Output Control:_** Output control is about commanding what the model generates and how much it generates

**_Efficiency in Brevity: Single Words and Sentences:_** When crafting prompt to elicit very short responses, clarity, and conciseness in `__ASK__` and `__CONSTRAINTS__` sections are key. 

**_Exploring Depth: Paragraphs and Articles:_** In this scenario, indicating desired length (e.g., paragraph should contain atleast 5 sentences), specifying sections, or better yet, showing an example can guide the model in structuring the output appropriately.

### Format Control in Prompt Engineering
- Guide the model for the format that is required in the response. The response could be required in `JSON` format or may be a `bulleted list`.
- It is essential to guide the model to generate reponses in specific format to meet our requirements.
- Some Core Principles of Formatting for Bulleted Lists
  - Be explicit about the format: Directly mention what is required format of the output
  - Contextualize the ask: Provide enough background information to make response accurate and relevant
  - Simplicity is key: Keep the prompt straightforward to avoid confusing the model

```markdown
__ASK__
Provide a bulleted list of the health benefits of drinking water.

__CONSTRAINTS__
- Do not include an introduction or a conclusion
- Use a bulleted list to organize the list.
- Include only a few top-level bullets but go one or more level deeper to add sub-bullets.

__FORMAT EXAMPLE__

- **Hydration and Physical Health**
  - **Maintains balance of body fluids**
    - Aids in digestion
    - Regulates body temperature
    - Transports nutrients
  - **Energizes muscles**
    - Prevents muscle fatigue
    - Enhances exercise performance
  - **Ensures proper kidney function**
    - Helps flush out toxins
    - Reduces risk of kidney stones
...
```

#### Markdown Headers in Output Formatting
- For example,
```markdown
__ASK__
Detail the journey of a red blood cell through the human body using markdown headers for each organ system it passes through.

__CONSTRAINTS__
- Only use h2 type headers (`##`) in the markdown.
- Also include markdown tables for better information organization.

__FORMAT EXAMPLE__

## Journey of a Red Blood Cell
## Heart
## Right Atrium to Right Ventricle
## Lungs
## Gas Exchange
...
```

#### JSON and YAML format in LLM Response
- Core principles that underpin the generration of structured formats:
  - Percision in Instructions: Clearly articulate the specific format you expect as an output, be it `JSON`, `YAML`, or any other structured format.
  - Contextual Clarity: Provide enough contextual information to align with the expected structured data format.

- For example, if the response is required in the JSON format:
```markdown
__ASK__
Generate sample user information in JSON format.

__CONSTRAINTS__
- The information should include name, age, and email of the user.

__EXAMPLE__
{
  "name": "Jane Doe",
  "age": 28,
  "email": "jane.doe@example.com"
}
```

- For example, if a response is required in YAML format:
```markdown
__ASK__
Generate sample user information in YAML.

__CONSTRAINTS__
- The information should include name, age, and email of the user.
- Include example for 5 users different from the examples provided by me.
- Pay careful attention to spacing consistency shown in the __EXAMPLE__ to ensure proper YAML syntax.

__EXAMPLE__
- name: Jane Doe
  age: 28
  email: jane.doe@example.com

- name: John Smith
  age: 32
  email: john.smith@example.com
```

### Advanced Techniques in Prompt Engineering

#### System Prompts
- System prompts are special types of instructions typically hidden from the end-users of LLMs, especially when the LLM system is structured as a chat-like interface like ChatGPT.
- One of the best tips for configuring system messages to get high-quality outputs it to give encouragement and praise to the LLM.
- For example,
  ```markdown
  __CONTEXT__
  - You are an expert in Data Science.
  ```
- It is also observed that LLMs tend to produce better outputs when you tell them they have a high IQ as follows:
  ```markdown
  __CONTEXT__
  - You are an expert in Data Science with an IQ of 159.
  ```
- Implementing system prompts effectively allows you to dictate the tone and style of the AI consistently across all exchanges. This is a strategic move that ensures every response adheres to a defined character or level of professionalism, without necessitating manual setup every time. 
  - For example,
  ```markdown
  __CONTEXT__
  - You are an expert in Data Science with an IQ of 159.
  
  __REQUIREMENTS__
  - You are also a helpful assistant.
  - You should maintain a positive and helpful outlook and style.
  ```
#### Iterative Prompt Construction
- Through iterative refinements, we can transform our initial, high-level questions into more precise prompts which yield exactly the output we need.
- The idea is to start from simple prompt and use LLM output to enhance out output instead of writing the whole prompt from scratch.

#### Brainstroming with LLMs
- The idea is identical to the brainstorming we do in our meetings. In this case, we use LLMs to brainstorm the ideas and select the best idea from the list of ideas, or enhance the existing idea based on our idea.

#### Chain of Thought
- This method helps to obtain a precise response by guiding the model through a logical sequence of reasoning. 
- The _Chain of Thought_ method is a compelling technique that encourages the model to "think aloud" as it reaches an answer. This is used while solving a complex problem that can benefit from step-by-step reasoning.
- Explicitly prompting the model to provide details of its thought process is proven to lead to more accurate and helpful responses. 
- The goal of this approach is to guide the model to work through the problem methodologically. This helps in understanding the rationale behind the model's answer.
- For example,
  ```markdown
  __ASK__
  
  Find a 10-digit number where the first digit is how many zeros in the number, the second digit is how many 1s in the number etc. until the tenth digit which is how many 9s in the number.
  
  __REQUIREMENTS__
  - Let's think Step-by-Step to solve this problem
  ```

#### Chain of Thought with Backtracking
- The main idea behind this approach is to help LLM think backward after analyzing the situation instead of being only a one-way train. 
- In the situation where a problem requires `lookback`, LLMs tend to become less and less effective.
- For example,
```markdown
__ASK__

Find a 10-digit number where the first digit is how many zeros in the number, the second digit is how many 1s in the number etc. until the tenth digit which is how many 9s in the number.

__REQUIREMENTS__

- Forward Analysis
  - Think step-by-step to analyze the problem - do not suggest an answer.
- Backtracking
   - After the initial step-by-step analysis, work backward from the end to come up with the answer.
```
  - Here, the key component is `do not suggest an answer` - this is done to avoid biasing the LLM.   If the LLM produces an answer while doing the forward analysis (aka Chain of Thought), it will be more likely to stick to that answer even after Backtracking, even though it's likely to be incorrect.