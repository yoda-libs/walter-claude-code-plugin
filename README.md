<div align="center">

# Walter - Your AI Development Team

### Ship Features 10x Faster with an Automated AI Workflow

**Stop context-switching. Start shipping.**

Walter is a Claude Code plugin that gives you a complete AI-powered development team — from product planning to code review — all working together to deliver production-ready features.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Plugin-blueviolet)](https://claude.ai)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

[Get Started](#quick-start) | [How It Works](#how-it-works) | [Documentation](#documentation)

</div>

---

## Why Walter?

Building software is hard. You're constantly switching between:
- Writing specs and requirements
- Implementing code
- Writing and running tests
- Reviewing for security issues
- Keeping documentation updated

**What if AI could handle the entire workflow?**

Walter orchestrates 5 specialized AI agents that work together like a real development team:

| Agent | What It Does | Why It Matters |
|-------|--------------|----------------|
| **Product Manager** | Writes detailed PRDs with acceptance criteria | No more ambiguous requirements |
| **Developer** | Implements features using TDD | Clean, tested code from the start |
| **QA Tester** | Validates against acceptance criteria | Catches bugs before they ship |
| **Code Reviewer** | Security audits and best practices | Production-ready, secure code |
| **KB Updater** | Auto-updates your documentation | Always up-to-date docs |

## How It Works

One command. Five phases. Production-ready code.

```
/walter:feature Add user authentication with OAuth
```

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  1. PLAN    │ ──► │  2. DEVELOP │ ──► │  3. TEST    │ ──► │  4. REVIEW  │ ──► │  5. DOCUMENT│
│             │     │             │     │             │     │             │     │             │
│ PRD with    │     │ TDD-driven  │     │ Automated   │     │ Security    │     │ Knowledge   │
│ acceptance  │     │ implementa- │     │ validation  │     │ audit &     │     │ base auto-  │
│ criteria    │     │ tion        │     │ & testing   │     │ code review │     │ updated     │
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
```

### The Result?

- **Consistent quality** — Every feature follows the same rigorous process
- **Complete documentation** — PRDs, tests, and docs generated automatically
- **Security-first** — Built-in security review catches vulnerabilities early
- **Knowledge retention** — Your project's knowledge base grows with every feature

---

## Quick Start

### 1. Install the Plugin

```bash
# Add the marketplace
/plugin marketplace add yoda-libs/walter-claude-code-plugin

# Install the plugin
/plugin install walter@yoda-libs
```

Or for local development:
```bash
claude --plugin-dir /path/to/walter-claude-code-plugin
```

### 2. Initialize Your Project

```bash
/walter:feature my first feature
```

Walter will detect if your project isn't set up and guide you through initialization.

### 3. Start Building

```bash
/walter:feature Add user authentication with social login
```

That's it. Walter handles the rest.

---

## Features at a Glance

### Full Automated Workflow
Run the complete development cycle with a single command. Walter coordinates all agents automatically, passing context between phases.

### Specialized AI Agents
Each agent is optimized for its role with specific prompts, tools, and access levels. The Product Manager can't accidentally modify code. The Developer has full access to implement.

### Built-in Quality Gates
Every feature goes through testing and security review before completion. No shortcuts, no "we'll add tests later."

### Self-Documenting Codebase
The KB Updater agent automatically maintains your project's knowledge base, documenting patterns, decisions, and features as you build.

### Works With Your Stack
Walter adapts to your tech stack, coding conventions, and project structure. Configure once, benefit forever.

---

## Documentation

### Project Configuration

Create `.walter/WALTER-PROJECT.md` in your repository with:

```markdown
## Tech Stack
- Language: TypeScript
- Runtime: Node.js 20
- Framework: Next.js 14

## Commands
- Dev: `npm run dev`
- Test: `npm test`
- Lint: `npm run lint`

## Paths
- PRDs: `.walter/PRDs/`
- Knowledge Base: `.walter/project-kb/`
```

### Directory Structure

```
.walter/
├── project-kb/           # Your project's knowledge base
│   ├── README.md         # KB index
│   ├── features/         # Feature documentation
│   ├── patterns/         # Code patterns & conventions
│   └── sop/              # Standard operating procedures
├── PRDs/                 # Generated PRDs
├── WALTER-PROJECT.md     # Project configuration
└── init                  # Initialization marker
```

### Using Individual Agents

Need just one phase? Use agents directly:

```bash
# Planning only
Use the walter-product-manager subagent to plan: user authentication

# Development only
Use the walter-developer subagent to implement .walter/PRDs/USER_AUTH.md

# Testing only
Use the walter-qa-tester subagent to validate .walter/PRDs/USER_AUTH.md

# Review only
Use the walter-code-reviewer subagent to review .walter/PRDs/USER_AUTH.md
```

---

## Requirements

### Claude Code
Walter is a plugin for [Claude Code](https://claude.ai), Anthropic's AI-powered coding assistant.

### Browser Testing (Optional)
For UI testing capabilities, install the agent-browser skill:

```bash
npx @anthropic-ai/claude-code skills add https://github.com/anthropics/agent-browser --skill agent-browser
```

---

## Comparison

| Feature | Traditional Dev | With Walter |
|---------|----------------|-------------|
| Requirements | Manual PRD writing | AI-generated with acceptance criteria |
| Implementation | Write code manually | TDD-driven AI implementation |
| Testing | Write tests after | Tests written alongside code |
| Security Review | Often skipped | Automated security audit |
| Documentation | Always outdated | Auto-updated knowledge base |
| Context Switching | Constant | Zero — one command does it all |

---

## Plugin Architecture

```
walter-claude-code-plugin/
├── .claude-plugin/
│   └── plugin.json                # Plugin manifest
├── commands/
│   └── feature.md                 # Main workflow command
├── agents/
│   ├── walter-product-manager.md  # PRD & planning
│   ├── walter-developer.md        # Implementation
│   ├── walter-qa-tester.md        # Testing & validation
│   ├── walter-code-reviewer.md    # Security & review
│   └── walter-kb-updater.md       # Documentation
└── README.md
```

---

## Contributing

We welcome contributions! Whether it's:
- Bug fixes
- New agent capabilities
- Documentation improvements
- Feature requests

Please open an issue or submit a PR.

---

## License

MIT License — use it, modify it, ship it.

---

<div align="center">

### Ready to 10x Your Development Speed?

```bash
/plugin marketplace add yoda-libs/walter-claude-code-plugin
/plugin install walter@yoda-libs
```

**[Get Started Now](#quick-start)**

---

Built with Claude Code | Made for developers who ship

</div>
