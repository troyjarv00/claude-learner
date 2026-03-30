---
title: "Exercise: Write Your First Effective Prompt"
parent: "Introduction to Prompt Engineering"
type: exercise
tags:
  - learning
  - prompt-engineering
  - exercise
---

# Exercise: Write Your First Effective Prompt

## Scenario

You are building a Python web API using FastAPI. You need to add input validation to an endpoint but you have never used Pydantic validators before.

## Your Task

Write a prompt that you would send to Claude to get help with this. Your prompt should:

1. State what you are building (project context)
2. Specify the technology (FastAPI, Pydantic)
3. Describe exactly what you need (input validation on a specific endpoint)
4. Mention your experience level with this specific tool (new to Pydantic validators)
5. Ask for what you actually want (working code example, not just an explanation)

## What Success Looks Like

Your prompt should be 3-6 sentences and include all five elements above. A good prompt here would get you a working, copy-paste-ready code example on the first try.

## Hints

<details>
<summary>Hint 1: Structure</summary>
Start with context ("I'm building..."), then the specific need ("I need to..."), then your knowledge gap ("I haven't used..."), then the ask ("Can you show me...").
</details>

<details>
<summary>Hint 2: Specificity</summary>
Don't just say "an endpoint" — describe what the endpoint does. Don't just say "validation" — describe what you want to validate (string length? email format? numeric range?).
</details>

## Solution

<details>
<summary>Example solution (try writing your own first!)</summary>

"I'm building a user registration API with FastAPI. I need to add input validation to my POST /users endpoint — specifically, I want to validate that the email field is a valid email format, the password is at least 8 characters with one uppercase and one number, and the username is 3-20 characters alphanumeric only. I'm new to Pydantic field validators. Can you show me the Pydantic model with validators and the FastAPI endpoint using it, with example request/response?"

This works because it provides full context, names specific technologies, describes exact validation rules, states experience level, and asks for concrete output.

</details>
