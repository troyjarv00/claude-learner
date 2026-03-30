---
title: "What is a Prompt?"
parent: "Introduction to Prompt Engineering"
lesson-number: 1
status: not-started
type: conceptual
tags:
  - learning
  - prompt-engineering
---

# What is a Prompt?

## Why This Matters

Every interaction you have with an AI model like Claude starts with a prompt. The quality of your prompt directly determines the quality of the response. Understanding what prompts are and how models interpret them is the foundation for everything else in this curriculum.

## Explanation

A prompt is the text you send to a large language model (LLM) to get a response. Think of it like giving instructions to a very capable but very literal assistant — the more clearly you communicate what you want, the better the result.

When you type a message to Claude, that entire message is your prompt. The model reads your text, processes it using patterns learned during training, and generates a response one token (roughly one word) at a time.

Here is what matters about prompts:

**Prompts are the only way to communicate.** The model has no other context about you, your project, or your goals beyond what you write in the prompt (and any system instructions or conversation history).

**Models are literal.** If you ask "Can you write a function?" the model might answer "Yes, I can" instead of actually writing one. Saying "Write a function that..." gets you the function.

**More context produces better results.** Telling the model what you are building, what language you are using, and what constraints exist helps it give you a relevant answer instead of a generic one.

## Key Takeaways

- A prompt is the text input you send to an LLM to get a response
- Models interpret prompts literally — clarity and specificity matter
- The model only knows what you tell it in the prompt
- Better prompts = better responses, every time
- Prompt engineering is the skill of writing effective prompts

## Check Your Understanding

1. In your own words, what is a prompt?
2. True or False: An LLM remembers information about you between separate conversations.
3. Why does being specific in your prompt lead to better results?
4. What is the difference between asking "Can you write a test?" and "Write a pytest unit test for the calculate_total function in cart.py"?
5. Multiple choice: What determines the quality of an LLM's response?
   - a) The size of the model
   - b) The quality of the prompt
   - c) The time of day
   - d) The programming language used
