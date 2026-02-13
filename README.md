# Aurelia 2 Skill Plugin

A plugin providing expert guidance for building modern web applications with the Aurelia 2 framework. Compatible with AI coding tools that support the plugin/skill format, including Claude Code and GitHub Copilot CLI.

## Overview

This plugin adds an Aurelia 2 skill to your AI coding assistant, giving it deep knowledge of:

- Project setup and configuration
- Component development and lifecycle
- Templating and data binding
- Routing and navigation
- Dependency injection
- State management
- Testing strategies
- Best practices and patterns

## Plugin Structure

```
skills-aurelia-2/
├── .claude-plugin/
│   └── plugin.json        # Plugin manifest
├── skills/
│   └── aurelia-2/
│       └── SKILL.md       # Skill content
├── LICENSE
└── README.md
```

## Installation

### Claude Code

From a marketplace:

```bash
claude plugin install aurelia-2
```

Direct installation (local development):

```bash
claude --plugin-dir /path/to/skills-aurelia-2
```

Project-scoped (shared with team via version control):

```bash
claude plugin install aurelia-2 --scope project
```

### GitHub Copilot CLI

Install as a skill plugin:

```bash
copilot plugin install /path/to/skills-aurelia-2
```

Or add to your project's Copilot configuration to share with your team.

## What the Skill Provides

When active, your AI assistant gains contextual knowledge about Aurelia 2 including:

- **Project Setup** — Opinionated starter templates with Vitest and Playwright
- **Component Architecture** — Three-file component structure (TS, HTML, CSS)
- **Styling** — Scoped vanilla CSS patterns
- **Dependency Injection** — Using `resolve()` for clean dependency management
- **Routing** — Standard Aurelia 2 routing patterns with lifecycle hooks
- **Templating** — Modern binding syntax (`.bind`, `.trigger`)
- **Best Practices** — Feature folders, lifecycle management, testing strategies

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT
