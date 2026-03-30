---
name: learn
description: Turn any URL into a structured learning curriculum. Give it a link to a course, article, GitHub repo, tweet, or docs page and it generates a full lesson plan with study guides, quizzes, and exercises — saved to Obsidian or local markdown. Usage - /learn <url>
user_invocable: true
---

# Learn — Build a Curriculum from Any URL

You have been given a URL to turn into a structured learning curriculum. Your job is to fetch the content, analyze it, and generate a complete set of lesson notes that a tutor (the `/teach` skill) can use to interactively teach this material.

## Input

The user provides a URL as an argument: `/learn <url>`

If no URL is provided, ask for one. Accept any URL — web pages, GitHub repos, tweets, documentation, course pages, etc.

## Step 1: Fetch the Content

- Use **WebFetch** for web pages, articles, blog posts, course pages, documentation
- Use **Bash with `gh`** for GitHub repos (fetch README, key source files, docs/)
- If the URL is inaccessible or returns minimal content, tell the user and ask if they have an alternative source

Fetch thoroughly. For course catalog pages that list multiple topics, fetch the catalog AND each individual course/topic page linked from it.

## Step 2: Analyze and Classify

For each distinct topic found in the content, determine:

**Topic type** (drives teaching style):
- **conceptual** — theory, frameworks, mental models, explanations (articles, docs, overviews)
- **practical** — hands-on CLI usage, tool workflows, configuration (tutorials, guides, Claude Code features)
- **api-code** — programming interfaces, SDKs, code patterns (API docs, SDK references, GitHub repos)
- **mixed** — combination of the above

**Depth:**
- **introductory** — no prerequisites, explains from zero
- **intermediate** — assumes basic familiarity
- **advanced** — assumes working knowledge, covers edge cases and advanced patterns

## Step 3: Detect Multi-Topic Sources

If a single URL contains multiple distinct topics (e.g., a course catalog listing 15 courses, a documentation site with multiple sections), create a **separate curriculum folder for each topic**. Do not lump them together.

For each topic, you will repeat Steps 4-6 independently.

Tell the user how many topics you detected and list them before generating.

## Step 4: Generate the Curriculum

For each topic, generate the following notes:

### Overview Note (`00-overview.md`)
- Title and one-paragraph summary of what this topic covers
- Source URL
- Prerequisites (what someone should know before starting — or "None" for introductory)
- Estimated time to complete
- Learning objectives (3-5 bullet points: "After completing this, you will be able to...")
- Ordered list of lessons with one-line descriptions

### Lesson Notes (`01-<slug>.md`, `02-<slug>.md`, etc.)
Each lesson covers one major concept or section. Every lesson must contain:

1. **Why this matters** — real-world context for why this concept is important (2-3 sentences)
2. **Explanation** — teach the concept from zero. Use analogies. Be thorough but clear. Assume the reader knows nothing about this topic.
3. **Key takeaways** — 3-5 bullet points summarizing the core ideas
4. **Content-appropriate assessment** (varies by type):
   - Conceptual: comprehension questions ("In your own words, explain..."), true/false, multiple choice
   - Practical: step-by-step exercise to try in the terminal ("Open Claude Code and...")
   - API/Code: coding challenge ("Write a function that...", "Build a minimal...")
   - Mixed: combination

### Quiz Notes (`quiz-<slug>.md`) — optional, for conceptual topics
- 5-10 questions testing understanding
- Mix of formats: multiple choice, true/false, short answer, "explain in your own words"
- Include answers in a collapsed/spoiler section at the bottom
- Questions should test understanding, not memorization

### Exercise Notes (`exercise-<slug>.md`) — optional, for practical/api topics
- Clear scenario description
- Step-by-step instructions
- Expected outcome (what success looks like)
- Hints section (for if the learner gets stuck)
- Solution in a collapsed/spoiler section at the bottom

## Step 5: Save to Obsidian

Check if the Obsidian MCP tools are available (try listing the directory).

**If Obsidian is available:**
Save all notes to `Personal/Learning/<Topic Name>/` using the Obsidian `write_note` tool.

**If Obsidian is NOT available:**
Save all notes as local markdown files to `~/Learning/<Topic Name>/` using the Write tool. Create directories as needed.

### Frontmatter for Overview Notes

```yaml
---
title: "<Topic Name>"
type: <conceptual|practical|api-code|mixed>
depth: <introductory|intermediate|advanced>
source: "<original URL>"
status: not-started
created: <today's date>
lessons-total: <number>
tags:
  - learning
  - <topic-specific-tag>
---
```

### Frontmatter for Lesson Notes

```yaml
---
title: "<Lesson Title>"
parent: "<Topic Name>"
lesson-number: <N>
status: not-started
type: <conceptual|practical|api-code|mixed>
tags:
  - learning
  - <topic-specific-tag>
---
```

## Step 6: Report to User

After generating, show a summary:
- How many topics were created
- For each topic: name, number of lessons, type, depth
- Where the notes were saved (Obsidian path or local path)
- Suggest: "Use `/teach <topic name>` to start learning interactively."

## Important Rules

- **Teach from zero.** Every lesson assumes the reader knows nothing. No "as you probably know" shortcuts.
- **Be thorough.** A lesson should contain enough information that someone could understand the concept without any other resource.
- **Be practical.** Always connect concepts to real-world usage. "When would I use this?" should be answerable from the lesson.
- **Organize well.** Lessons should follow a logical progression — each building on the previous one.
- **No fluff.** Every sentence should teach something. Cut filler.
