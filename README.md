# Awesome MomoChenIsMe Skills

A collection of Claude Code skills for productivity, content creation, and development workflows.

## Skills Overview

| Skill | Description |
|-------|-------------|
| **Sync Scribe** | Note-taking and todo management |
| **MomoChenIsMe Writing Style** | Blog writing style guide (Traditional Chinese) |
| **Skill Creator** | Guide for creating effective Claude Code skills |
| **Plugin Creator** | Guide for creating Claude Code plugins |
| **Claude Code CLI Guide** | Complete CLI usage reference |
| **Gemini CLI Guide** | Complete Gemini CLI usage reference |
| **OpenSpec Guide** | Spec-Driven Development workflow framework |
| **Coding Agent** | Run coding agents (Codex/Claude Code/OpenCode/Pi) via background process |
| **tmux** | Remote-control tmux sessions for interactive CLI workflows |

---

## Sync Scribe

A simplified note-taking and todo management skill for Claude Code.

### Features

- **Auto-categorization**: Automatically determines if input is a todo or note
- **Todo management**: Add, complete, and delete tasks
- **Note management**: Categorized notes with timestamps
- **Search & filter**: Find items by keyword or category

### Usage

#### Slash Commands

| Command | Description |
|---------|-------------|
| `/add-todo <task>` | Add a new todo |
| `/complete-todo <keyword>` | Mark as complete |
| `/list-todos [filter]` | List all todos |
| `/delete-todo <keyword>` | Remove a todo |
| `/add-note <content>` | Add a new note |
| `/list-notes [category\|keyword]` | List notes |
| `/delete-note <keyword>` | Remove a note |

#### Natural Language

Just say:
- "Remember to buy milk" → Adds to todos
- "Note: the coffee shop was great" → Adds to notes
- "Buying milk is done" → Marks complete

### Data Storage

- `TODOS.md` - Todo list
- `NOTES.md` - Categorized notes

Files are stored in your workspace root.

---

## MomoChenIsMe Writing Style

A skill that mimics the unique writing style of MomoChenIsMe blogger for technical articles.

### Features

- **Conversational tone**: Friendly, approachable writing like chatting with a friend
- **Moderate humor**: Light self-deprecating humor with frequent use of "XD"
- **Practice-oriented**: Emphasizes "how to do" over abstract theory
- **Language style**: Traditional Chinese with English technical terms preserved

### Suitable Article Types

- **Technical tutorials**: Step-by-step guides with screenshots and code blocks
- **Product reviews**: Tool introductions with honest pros and cons
- **Personal reflections**: Experience sharing with lessons learned
- **Year-end reviews**: Timeline-based retrospectives

### Usage

Trigger naturally by asking Claude:
- "Use MomoChenIsMe style to write a Docker tutorial"
- "Introduce this tool in MomoChenIsMe style"
- "Write a year-end review in MomoChenIsMe's voice"

### Style Highlights

| Element | Usage |
|---------|-------|
| **Bold** | Emphasis on keywords |
| `Code` | Technical terms and commands |
| > Quote | Important callouts |

---

## Skill Creator

> Source: [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/skill-creator)

A comprehensive guide for creating effective Claude Code skills.

### Features

- **Skill anatomy**: SKILL.md structure, frontmatter, and body guidelines
- **Resource bundling**: Scripts, references, and assets organization
- **Progressive disclosure**: Three-level loading system for context efficiency
- **Best practices**: Concise writing, appropriate degrees of freedom

### Key Concepts

- **SKILL.md**: Required file with YAML frontmatter (name, description) and Markdown body
- **scripts/**: Executable code for deterministic, repetitive tasks
- **references/**: Documentation loaded on-demand into context
- **assets/**: Files used in output (templates, images, fonts)

### Workflow

1. Understand the skill with concrete examples
2. Plan reusable contents (scripts, references, assets)
3. Initialize with `scripts/init_skill.py`
4. Edit SKILL.md and implement resources
5. Package with `scripts/package_skill.py`
6. Iterate based on real usage

---

## Plugin Creator

A guide for creating Claude Code plugins - distributable packages that bundle skills, hooks, and MCP servers.

### Features

- **Plugin structure**: Directory layout and manifest configuration
- **Component types**: Commands, skills, hooks, MCP servers, LSP servers
- **Initialization script**: Quick plugin scaffolding
- **Testing guide**: Local plugin loading and debugging

### When to Use Plugin vs Standalone

| Use Case | Recommended |
|----------|-------------|
| Single project only | Place in `.claude/` |
| Share across projects | Create a Plugin |
| Distribute to others | Create a Plugin |

### Quick Start

```bash
# Create new plugin
python skills/plugin-creator/scripts/init_plugin.py my-plugin

# Test local plugin
claude --plugin-dir ./my-plugin
```

### Plugin Structure

```
my-plugin/
├── .claude-plugin/
│   └── plugin.json      # Manifest (required)
├── commands/            # User-invocable skills
├── skills/              # Agent skills
├── hooks/               # Hook configurations
└── README.md
```

---

## Claude Code CLI Guide

Complete reference for Claude Code CLI commands and flags.

### Basic Commands

| Command | Description |
|---------|-------------|
| `claude` | Start interactive REPL |
| `claude "query"` | Start REPL with initial prompt |
| `claude -p "query"` | One-shot query (pipe/SDK mode) |
| `claude -c` | Continue most recent conversation |
| `claude -r <id>` | Resume specific session |
| `claude config` | Configuration management |
| `claude mcp` | MCP server configuration |
| `claude update` | Update to latest version |

### Common Flags

| Flag | Description |
|------|-------------|
| `-p, --print` | One-shot query mode |
| `-c, --continue` | Continue recent conversation |
| `--model <name>` | Specify model (opus/sonnet/haiku) |
| `--output-format <fmt>` | Output format (text/json/stream-json) |
| `--max-turns <n>` | Limit agent turns |
| `--verbose` | Verbose logging |

### References

- [commands.md](skills/claude-code-cli-guide/references/commands.md) - All commands explained
- [flags.md](skills/claude-code-cli-guide/references/flags.md) - All flags by category
- [examples.md](skills/claude-code-cli-guide/references/examples.md) - Common usage examples

---

## Gemini CLI Guide

Complete reference for Gemini CLI commands and configuration.

### Basic Commands

| Command | Description |
|---------|-------------|
| `gemini` | Start interactive REPL |
| `gemini "query"` | Start REPL with initial prompt |
| `gemini -p "query"` | One-shot query (pipe mode) |

### Slash Commands

| Command | Description |
|---------|-------------|
| `/help` | Show all available commands |
| `/chat` | Start new conversation |
| `/resume` | Restore previous conversation |
| `/save` | Save current conversation |
| `/memory` | Show active memories |

### Common Flags

| Flag | Description |
|------|-------------|
| `-p, --prompt` | One-shot query mode |
| `-m, --model` | Specify model |
| `-s, --sandbox` | Enable sandbox mode |
| `--approval-mode` | Set approval mode (default/auto_edit/plan/yolo) |
| `--output-format` | Output format (text/json/stream-json) |
| `-d, --debug` | Enable debug mode |

### References

- [commands.md](skills/gemini-cli-guide/references/commands.md) - All commands explained
- [flags.md](skills/gemini-cli-guide/references/flags.md) - All CLI flags by category
- [configuration.md](skills/gemini-cli-guide/references/configuration.md) - Settings and MCP configuration
- [examples.md](skills/gemini-cli-guide/references/examples.md) - Common usage examples

---

## OpenSpec Guide

A lightweight Spec-Driven Development (SDD) framework for managing changes systematically.

### Core Philosophy

- **Fluid** not rigid
- **Iterative** not waterfall
- **Simple** not complex

### Document Structure

```
.openspec/changes/<change-id>/
├── proposal.md      # Why & What
├── specs/           # Requirements (delta specs)
├── design.md        # How
└── tasks.md         # Implementation checklist
```

### Commands

| Command | Purpose |
|---------|---------|
| `/opsx:new` | Create new change |
| `/opsx:ff` | Fast-forward: generate all docs |
| `/opsx:continue` | Resume in-progress change |
| `/opsx:apply` | Execute implementation |
| `/opsx:verify` | Verify against specs |
| `/opsx:archive` | Archive completed change |
| `/opsx:explore` | Explore mode (no changes) |

### Standard Workflow

```
/opsx:new → /opsx:ff → /opsx:apply → /opsx:verify → /opsx:archive
```

---

## Coding Agent

A skill for running coding agents (Codex CLI, Claude Code, OpenCode, or Pi Coding Agent) via background processes with programmatic control.

### Features

- **PTY mode support**: Proper pseudo-terminal allocation for interactive CLI tools
- **Background execution**: Run agents in background and monitor via process tool
- **Multiple agent support**: Works with Codex, Claude Code, OpenCode, and Pi
- **Process management**: Full control via process tool actions (poll, log, write, kill)

### Key Requirements

Always use `pty:true` when running coding agents - they require pseudo-terminals to work correctly:

```bash
# ✅ Correct - with PTY
bash pty:true command:"codex exec 'Your prompt'"

# ❌ Wrong - no PTY, agent may break
bash command:"codex exec 'Your prompt'"
```

### Common Parameters

| Parameter | Description |
|-----------|-------------|
| `pty` | **Required** - Allocates pseudo-terminal for interactive CLIs |
| `background` | Run in background, returns sessionId for monitoring |
| `workdir` | Working directory (agent sees only this folder's context) |
| `timeout` | Timeout in seconds (kills process on expiry) |

### Process Management

Use the process tool to manage background sessions:
- `list` - List all running/recent sessions
- `poll` - Check if session is still running
- `log` - Get session output
- `write/submit` - Send input to agent
- `kill` - Terminate the session

---

## tmux

Remote-control tmux sessions for interactive CLI workflows by sending keystrokes and scraping pane output.

### Features

- **Isolated socket management**: Dedicated socket directory for OpenClaw sessions
- **Interactive TTY control**: Send keystrokes and capture pane output
- **Session management**: Create, attach, and monitor tmux sessions programmatically
- **Pane targeting**: Flexible session:window.pane addressing

### When to Use

Use tmux for interactive TTY applications. For long-running, non-interactive tasks, prefer `exec` background mode.

### Quick Start

```bash
SOCKET_DIR="${OPENCLAW_TMUX_SOCKET_DIR:-/tmp/openclaw-tmux-sockets}"
mkdir -p "$SOCKET_DIR"
SOCKET="$SOCKET_DIR/openclaw.sock"
SESSION=openclaw-python

# Create new session
tmux -S "$SOCKET" new -d -s "$SESSION" -n shell

# Send commands
tmux -S "$SOCKET" send-keys -t "$SESSION":0.0 -- 'python3 -q' Enter

# Capture output
tmux -S "$SOCKET" capture-pane -p -J -t "$SESSION":0.0 -S -200
```

### Core Commands

| Command | Purpose |
|---------|---------|
| `new -d -s <session>` | Create detached session |
| `send-keys -t <target> -- <text>` | Send keystrokes to pane |
| `capture-pane -p -J -t <target>` | Capture and print pane output |
| `list-sessions` | List all sessions on socket |
| `attach -t <session>` | Attach to session for monitoring |

---

## Other Recommended Skills

A curated list of useful Claude Code skills from the community.

👉 [View Full List](skills/RECOMMENDED_SKILLS.md)

---

## Installation

```bash
# Local development
claude --plugin-dir ./
```

## File Structure

```
awesome-momochenisme-skills/
├── README.md
├── README_zh.md
├── .claude-plugin/
│   └── plugin.json
├── commands/
│   ├── add-todo.md
│   ├── complete-todo.md
│   ├── list-todos.md
│   ├── delete-todo.md
│   ├── add-note.md
│   ├── list-notes.md
│   └── delete-note.md
└── skills/
    ├── RECOMMENDED_SKILLS.md
    ├── RECOMMENDED_SKILLS_zh.md
    ├── sync-scribe/
    │   └── SKILL.md
    ├── momochenisme-writing-style/
    │   ├── SKILL.md
    │   └── references/
    │       └── style-examples.md
    ├── skill-creator/
    │   ├── SKILL.md
    │   ├── scripts/
    │   └── references/
    ├── plugin-creator/
    │   ├── SKILL.md
    │   ├── scripts/
    │   └── references/
    ├── claude-code-cli-guide/
    │   ├── SKILL.md
    │   └── references/
    ├── gemini-cli-guide/
    │   ├── SKILL.md
    │   └── references/
    ├── openspec-guide/
    │   ├── SKILL.md
    │   └── references/
    ├── coding-agent/
    │   └── SKILL.md
    └── tmux/
        ├── SKILL.md
        └── scripts/
```

## License

MIT License
