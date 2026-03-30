---
title: "Quiz: Prompt Engineering Fundamentals"
parent: "Introduction to Prompt Engineering"
type: quiz
tags:
  - learning
  - prompt-engineering
  - quiz
---

# Quiz: Prompt Engineering Fundamentals

Test your understanding of the core concepts from Lessons 1-2.

## Questions

**1.** What is the primary factor that determines the quality of an LLM's response?

A) The model's parameter count
B) The clarity and specificity of the prompt
C) The length of the conversation
D) The programming language mentioned

**2.** True or False: Adding context about your project to a prompt is unnecessary because the model can infer it.

**3.** Which of these is a more effective prompt and why?
- Option A: "Help me with my code"
- Option B: "I have a Python FastAPI endpoint that returns a 422 error when I POST a JSON body with nested objects. Here is the endpoint code and the request body I am sending. What is wrong?"

**4.** In your own words, explain why being specific in prompts matters.

**5.** You ask Claude "Can you make this faster?" and it responds with a generic list of optimization tips unrelated to your code. What went wrong with your prompt?

---

<details>
<summary>Answers (try answering first!)</summary>

**1.** B — The clarity and specificity of the prompt is the primary factor.

**2.** False — models only know what you include in the prompt. They cannot see your project, files, or goals unless you provide that context.

**3.** Option B is far more effective. It provides: the language (Python), the framework (FastAPI), the specific error (422), the context (POST with nested objects), and offers to show code. Option A gives the model almost nothing to work with.

**4.** Good answers should mention: models are literal, they can only work with what you provide, vague prompts lead to vague or generic responses, specific prompts help the model narrow down to a relevant answer.

**5.** The prompt lacked context — it did not specify what "this" is, what language or framework is being used, what "faster" means (response time? build time? query performance?), or what the current performance looks like. The model guessed generically because it had no specifics.

</details>
