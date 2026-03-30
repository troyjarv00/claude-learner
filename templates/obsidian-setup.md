# Obsidian Setup for Claude Learner

Claude Learner works best with Obsidian for storing and browsing your learning materials. This guide explains how to set it up.

## What You Need

1. **Obsidian** — free note-taking app ([obsidian.md](https://obsidian.md))
2. **Obsidian MCP server** — connects Claude Code to your vault
3. **Claude Code** — with the learn and teach skills installed

## Setting Up the Obsidian MCP Server

Add the Obsidian MCP server to your Claude Code settings. In `~/.claude/settings.json`, add under `mcpServers`:

```json
{
  "obsidian": {
    "command": "npx",
    "args": ["-y", "obsidian-mcp", "--vault", "/path/to/your/vault"]
  }
}
```

Replace `/path/to/your/vault` with your actual Obsidian vault path.

## Folder Structure

The `/learn` skill saves curricula to `Personal/Learning/` inside your vault. Create this folder structure if it doesn't exist:

```
Your Vault/
  Personal/
    Learning/
      (curricula will be created here automatically)
```

## Without Obsidian

If you don't have Obsidian or prefer not to use it, the skills fall back to saving plain markdown files in `~/Learning/`. Everything works the same — you just won't have the Obsidian browsing experience.

## Verifying It Works

1. Open Claude Code
2. Run `/learn https://example.com/any-article`
3. Check your Obsidian vault — you should see a new folder under `Personal/Learning/`
4. Run `/teach` to see available topics
