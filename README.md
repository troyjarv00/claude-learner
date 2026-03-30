# Claude Learner

Turn any URL into an interactive learning experience. Two Claude Code skills that fetch content from any link, generate a structured curriculum, and then teach it to you step-by-step.

## How It Works

**`/learn <url>`** — Give it any link (article, GitHub repo, course page, tweet, API docs). Claude fetches the content, analyzes it, and generates a full curriculum: lessons, study guides, quizzes, and hands-on exercises. Saved as organized notes in Obsidian or local markdown.

**`/teach <topic>`** — Pick a topic from your learning library. Claude becomes your interactive tutor — explains concepts from zero, quizzes you, gives you hands-on exercises, validates your work, and tracks your progress. Adapts its teaching style to the content: conceptual topics get quizzes, practical topics get live exercises, code topics get build challenges.

## Prerequisites

- [Claude Code](https://claude.ai/code) installed and working
- **Optional:** [Obsidian](https://obsidian.md) with an MCP server for the best experience (see `templates/obsidian-setup.md`)

## Installation

Copy the skills to your Claude Code skills directory:

```bash
# Clone the repo
git clone https://github.com/troyjarv00/claude-learner.git

# Copy skills to Claude Code
cp -r claude-learner/skills/learn ~/.claude/skills/learn
cp -r claude-learner/skills/teach ~/.claude/skills/teach
```

Or symlink them (so you get updates with `git pull`):

```bash
ln -s $(pwd)/claude-learner/skills/learn ~/.claude/skills/learn
ln -s $(pwd)/claude-learner/skills/teach ~/.claude/skills/teach
```

Restart Claude Code. You should see `/learn` and `/teach` available as slash commands.

## Usage

### Learn from any source

```
/learn https://anthropic.skilljar.com/
/learn https://github.com/modelcontextprotocol/servers
/learn https://docs.anthropic.com/en/docs/build-with-claude/tool-use
```

### Start a lesson

```
/teach                          # list available topics
/teach Model Context Protocol   # start or resume a specific topic
```

### What gets generated

```
Personal/Learning/
  Model Context Protocol/
    00-overview.md
    01-what-is-mcp.md
    02-building-servers.md
    03-tool-definitions.md
    quiz-mcp-basics.md
    exercise-build-server.md
```

Each lesson includes explanations (from zero), key takeaways, and assessments appropriate to the content type. See `examples/sample-curriculum/` for a full example.

## Storage

- **With Obsidian MCP:** Notes saved to `Personal/Learning/<Topic>/` in your vault
- **Without Obsidian:** Notes saved to `~/Learning/<Topic>/` as plain markdown

Both options use the same format. Progress is tracked in note frontmatter.

## Teaching Approach

The `/teach` skill adapts based on the content:

| Content Type | How Claude Teaches |
|---|---|
| Conceptual | Explain, discuss, quiz, re-explain if needed |
| Practical/CLI | Explain, demo, you try it, Claude validates |
| API/Code | Explain, coding challenge, review your solution |

Every lesson assumes zero prior knowledge. Claude validates understanding before moving forward.

## Contributing

Skills are pure markdown — no code to build or test. To contribute:

1. Fork this repo
2. Edit the SKILL.md files
3. Test by copying to `~/.claude/skills/` and invoking
4. Open a PR

## License

MIT
