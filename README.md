# claude-cli-template

Simple CLAUDE.md file to preserve continuity across sessions.

## Problem

Claude code *is* great. However, due to session limits and/or interruptions, it often loses the ability to follow instructions and stay on the task.

In addition, Claude often uses a todo tool to keep track of tasks. However, when context gets full or a session ends, the todo generally gets lost - or diluted during compacting.

Claude is able to recover from these scenarios at the cost of project status analysis, and subsequent token consumption.

### Why this repo

What was missing for me was a way to keep track of backlog items and WIP tasks across sessions, so that any interruption wouldn't result in expensive context losses, and without relying on the todo tool that Claude uses - over which I had no control.

This project template, although far from perfect and with no guarantees whatsoever, helped me do that: keep Claude focus on the task at hand, and work on long projects over multiple sessions without major issues.

Sharing HTH.

### How to use

Prerequisites:
1. Git
2. Claude Code
3. A backup of the local `.claude` folder in your project

Installation:
1. Read the contents of this repo and README carefully before doing anything.
2. Backup your local `.claude` folder if not empty.
3. Copy this repo's `.claude` folder into your project - whole, or single files if you prefer.
4. **Edit** the `.claude/CLAUDE.md` and `.claude/DESIGN.md` files to match your needs.
5. **Optional**: **Add** a list of task as a backlog in `.claude/ROADMAP.md` - the more concise the description, the better.

**Please note**: the Claude instructions in this repo rely on Git for maximum flow. If you don't use Git, this repo won't be of much help.

### How it works

Project instructions are in `.claude/CLAUDE.md` and follow a custom workflow that works for me and I am happy with. Claude reads this file at the beginning of every session run. You can also ask/prompt Claude to re-read the file during a session if you observe any inconsistent behavior.

### Customization

The basic workflow is a simplified TDD-inspired workflow with task tracking.
I generally augment it with extra steps as needed (documentation, examples, etc). 

To customize:
1. Make your changes in `.claude/CLAUDE.md` (free-form)
2. In case, remove the remaining files in this repo if no longer useful, don't forget to remove the mentions in `.claude/CLAUDE.md`

### Model selection and other options

Claude code has a default behavior that can be configured, including the model selection. The [official docs](https://code.claude.com/docs/en/settings) explain what can be changed in `settings.json`. There are plenty of options described there.

In particular, Claude code may add a self-attribution note on Git commits: setting `includeCoAuthoredBy` to `false` should normally mute the behavior.

Here's my local `.claude/settings.local.json` for reference:
```json
{
  "permissions": {
    "allow": [],
    "deny": [
      "Bash(curl:*)",
      "Read(~/**)",
      "Read(./.env)",
      "Read(./.env.*)",
      "Read(./secrets/**)"
    ],
    "ask": []
  },
  "env": {
    "CLAUDE_CODE_ENABLE_TELEMETRY": "0"
  },
  "includeCoAuthoredBy": false,
  "gitAttribution": false,
  "model": "sonnet",
  "outputStyle": "default"
}
```

## Does it work?

It did for me. Anyway, Claude **will** end up ignoring instructions from time to time, especially when the context gets too long.

When that happens, here's what helped me:
1. Stop the session / interrupt the current run.
2. Ask Claude to re-read `.claude/CLAUDE.md` and related documents.

**Tip**: a context cleanup, and/or a fresh session start before 1+2 seemed to help too.
