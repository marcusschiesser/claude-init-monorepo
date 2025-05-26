# Claude Init Monorepo

A Python utility to automatically create `CLAUDE.md` files across all packages in a pnpm workspace monorepo. This tool helps ensure consistent AI assistant support throughout your codebase by generating guidance files for Claude Code.

## Features

- 🔍 **Auto-discovery**: Parses `pnpm-workspace.yaml` to find all workspace packages
- 🎯 **Smart targeting**: Supports processing all packages or a specific directory
- ⚡ **Efficient**: Skips packages that already have `CLAUDE.md` files
- 🛡️ **Safe**: Validates dependencies and directory structure before processing

## Prerequisites

- [uv](https://docs.astral.sh/uv/) - Python package manager
- [Claude CLI](https://claude.ai/code) - For generating CLAUDE.md files
- A monorepo with `pnpm-workspace.yaml` configuration

## Installation

```bash
# Install as a global tool with uv (recommended)
uv tool install git+https://github.com/marcusschiesser/claude-init-monorepo.git

# Or clone and install locally
git clone <repository-url>
cd claude-init-monorepo
uv tool install .
```

## Usage

### For your own pnpm workspace

After installing with `uv tool install`, simply run from your monorepo directory:

```bash
# From your monorepo root directory
cd /path/to/your/monorepo

# Process all packages
claude-init

# Process only a specific directory
claude-init apps/frontend
```

## How it Works

1. **Discovery**: Reads `pnpm-workspace.yaml` to identify workspace patterns
2. **Expansion**: Resolves glob patterns to find actual package directories
3. **Validation**: Ensures each directory contains a `package.json` file
4. **Generation**: Runs Claude CLI in each package to create `CLAUDE.md` files
5. **Safety**: Skips packages that already have `CLAUDE.md` files

## Supported Workspace Patterns

The tool handles various pnpm workspace patterns:

- Direct paths: `"apps/frontend"`
- Single-level wildcards: `"packages/*"`
- Recursive patterns: `"examples/**"`

## Example Output

```
🔍 Found 3 workspace patterns
📂 Found 12 package directories

Directories to process:
  - apps/frontend
  - apps/backend
  - packages/ui
  - packages/utils
  ...

🚀 Starting CLAUDE.md creation...
📦 Creating CLAUDE.md in: apps/frontend
✅ Successfully created CLAUDE.md in apps/frontend
...

✅ Completed! Successfully created CLAUDE.md in 12/12 packages
```

## License

MIT License - see [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.