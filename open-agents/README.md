# Open Agent System

This folder contains an **Open Agent System**—a structure of markdown files that transform AI coding assistants (Claude Code, Gemini CLI, Codex) into specialized agents.

## What Is This?

Instead of writing code, these agents:
- Manage files and content
- Perform research
- Transform documents between formats
- Execute domain-specific workflows

The agents are defined in markdown. No code required.

## Getting Started

Read `INSTRUCTIONS.md` for:
- Available agents and what they do
- How to invoke each agent
- Routing logic (which agent handles which requests)

## Folder Structure

- `agents/` — Agent definition files
- `tools/` — Scripts created by agents for repeatable operations
- `source/` — Input materials (your raw content goes here)
- `output-drafts/` — First-stage outputs
- `output-refined/` — Second-stage outputs
- `output-final/` — Final deliverables

## How It Works

1. Entry point files (CLAUDE.md, AGENTS.md, GEMINI.md) point to `INSTRUCTIONS.md`
2. `INSTRUCTIONS.md` catalogs available agents and routing logic
3. Agent files in `agents/` contain full definitions
4. Agents are loaded on demand when triggered
5. Outputs follow the source → drafts → refined → final workflow

## Creating Your Own Agents

See the [OpenAgentDefinition.md](../open-agent-system/OpenAgentDefinition.md) file for the complete specification on how to create, modify, and manage agents.
