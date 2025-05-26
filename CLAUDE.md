# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains a Python utility script for automating CLAUDE.md file creation across pnpm workspace packages. The main script `init-claude-workspaces.py` is designed to work with monorepos that use pnpm workspaces.

## Common Commands

```bash
# Install dependencies with uv
uv sync

# Run the script to create CLAUDE.md files for all workspace packages
uv run claude-init

# Process a specific directory only
uv run claude-init <directory>
```

## Architecture

The script operates by:
1. Reading `pnpm-workspace.yaml` to discover workspace patterns
2. Expanding glob patterns to find directories containing `package.json` files
3. Running the `claude` CLI tool in each directory to generate CLAUDE.md files
4. Skipping directories that already have CLAUDE.md files

Key functions:
- `load_workspace_config()`: Parses pnpm workspace configuration
- `expand_glob_patterns()`: Handles various glob patterns (direct paths, wildcards, recursive patterns)
- `run_claude_init()`: Executes claude CLI with specific parameters for CLAUDE.md generation

## Dependencies

The script requires:
- Python 3.8+ (managed by uv)
- PyYAML (automatically installed via uv)
- Claude CLI tool installed and available in PATH
- A valid `pnpm-workspace.yaml` file in the repository root

## Usage Context

This tool is intended for repository maintainers who want to systematically create CLAUDE.md files across all packages in a monorepo, ensuring consistent AI assistant support throughout the codebase.