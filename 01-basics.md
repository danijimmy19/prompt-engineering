### Importance of Consistent Formatting
- Presenting prompt in a clear and structured manner increases the chances of receiving the desired output.
- There are multiple approaches for structuring a prompt, here, we'll look at the Markdown Prompt Framework (MPF).

#### Markdown Prompts Framework (MPF)
- High-level summary of MPF:
  1. Split the prompt into markdown sections like: `__SECTION__`
     - This makes the prompt easily skimmable.
  2. Begin with `__ASK__` section at the top of your prompt
     - This allows team members to quickly understand the goal of the prompt from the very onset.
  3. Format each section as a markdown bullet points to make them easier to read and understand.
     - Bulleted lists are much easier to skim and they tend to lead to better instruction following by LLMs 
  4. While trying to minimize the number of sections, for complex prompts, include the following key sections:
     - `__ASK__`: what are we asking the LLM to do?
     - `__CONTEXT__`: what does the LLM need to know to be able to respond accurately?
     - `__CONSTRAINTS__`: what constraints needs to be followed when responding?
     - `__EXAMPLE__`: what's a good example of an output that you'd be happy with?
    - Example of a well-structured prompt
    ```markdown
    I need a short and uplifting song about the spirit of teamwork for a children's animated football show. The show is called "Dream Team" and the main characters are a group of animated animals who form a football team. The team consists of Penny the Penguin (Goalkeeper), Leroy the Leopard (Striker), and Bobby the Bear (Captain and Midfielder). The song has to mention the characters by name and illustrate the importance of teamwork. The song should have a catchy chorus and two verses like the given example:

    __ASK__
    - Write a short and uplifting song about the spirit of team work for a children's animated football show
    
    __CONTEXT__
    - The name of the show is "Dream Team"
    - Main characters are a group of animated animals who form a football team
    
    __CONSTRAINTS__
    - The team should consist of Penguin named Penny as Goalkeeper, Leapord named Leory as Striker, and Bear named Bobby as Captian and Midfielder.
    - The song should mention the characters by name and illustrate the importance of teamwork.
    
    
    __EXAMPLE__
    - The song should have a catchy chorus and two verses like the example given below:
    
    (Chorus)  
    Penny, Leroy and Bobby too,  
    Playing football, dream come true!  
    Through wind or rain, they got the knack,  
    With teamwork, there's no turning back. 
     
    (Verse 1)  
    A penguin in goal, wings spread wide,  
    Leroy leaps, no place to hide.  
    Bobby calls 'pass', then 'shoot',  
    When they play together, it's a hoot!
    
    (Verse 2)  
    Through each challenge, they found a way,  
    United under the sun's bright ray.  
    Their dream was football, their spirit strong,  
    Together in team, where they belong.
    ```
  
### Crafting Effective Examples for LLM Prompting
- Great examples are not just an add-ons, they are fundamental to designing effective prompts for LLMs. They guide the model towards our expectations and significantly influence the quality of the content generated.

### Context Limits and Implications
- A context limit refers to maximum amount of text an LLM can consider when generating a response. For example, GPT-3.5 has a context window of approximately 4096 tokens.
- It's important to realize that a token isn't just a word. It can be a word, part of a word, or punctuation.
- As a general rule of thumb, it's okay to think of tokens as words.

#### How to overcome Context Limits
1. Prompt compression: Simplify prompt to contain only the most essential information. This involves summarizing lengthy backgrounds or context into concise statements that retain the core message.
2. Focused Queries: Instead of asking broad, unfocused questions, pinpoint your inquiry. Specific questions tend to yield more accurate and relevant responses within the context limit.
3. Iterative prompting: Break down complex tasks into smaller, sequential prompts. By iteratively refining the query, you can guide the LLM through a logical sequence of thought, even with strick token limit.