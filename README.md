# Codex How-To

Structured learning guide for mastering **OpenAI Codex CLI** as an AI-powered development tool.

> Similar to [claude-howto](https://github.com/luongnv89/claude-howto) but optimized for Codex CLI

## Overview

This repository provides:
- ✅ Progressive setup templates for multiple tech stacks
- ✅ AGENTS.md best practices (equivalent to CLAUDE.md)
- ✅ Project-specific instructions and workflows
- ✅ Codex CLI configuration patterns
- ✅ Guides for switching projects efficiently
- ✅ Integration with MCP (Model Context Protocol) servers

## Quick Start

### Prerequisites
- ✅ [Install Codex CLI](./INSTALLATION.md) — Complete setup guide
- ✅ OpenAI API key configured
- ✅ Git installed

### 1. Clone Repository
```bash
git clone https://github.com/yourusername/codex-howto
cd codex-howto
```

### 2. Setup Global Codex Config
Copy global AGENTS.md to your Codex directory:
```bash
cp AGENTS.md ~/.codex/
cp .codex/config.toml ~/.codex/config.toml (merge with existing)
```

### 3. Create New Project
Choose your tech stack:
- [Laravel API](./templates/laravel-project/AGENTS.md)
- [NestJS API](./templates/nestjs-project/AGENTS.md)
- [Next.js App](./templates/nextjs-project/AGENTS.md)

Copy template to your project:
```bash
cp -r templates/laravel-project/* ~/your-project/
# Edit AGENTS.md with your project details
```

### 4. Start Coding
```bash
cd ~/your-project
# Codex CLI will auto-read AGENTS.md
codex start
```

## Repository Structure

```
codex-howto/
├── README.md                          # This file
├── GETTING_STARTED.md                 # Detailed setup guide
├── AGENTS.md                          # Global instructions template
├── .codex/
│   └── config.toml                    # Global config template
├── templates/                         # Project templates
│   ├── laravel-project/
│   │   ├── AGENTS.md
│   │   └── .codex/config.toml
│   ├── nestjs-project/
│   │   ├── AGENTS.md
│   │   └── .codex/config.toml
│   └── nextjs-project/
│       ├── AGENTS.md
│       └── .codex/config.toml
├── skills/                            # Reference skills (from ~/.codex/skills/)
│   ├── code-review-checklist.md
│   ├── testing-patterns.md
│   ├── database-design.md
│   └── deployment-procedures.md
├── guides/
│   ├── SWITCH_PROJECT_PROMPT.md       # Prompt for new projects
│   ├── CODEX_vs_CLAUDE.md             # Comparison
│   ├── BEST_PRACTICES.md              # Codex-specific tips
│   ├── MCP_GUIDE.md                   # MCP servers setup
│   └── TROUBLESHOOTING.md
└── .gitignore
```

## Key Concepts

### AGENTS.md (= CLAUDE.md in Claude Code)
- Auto-read by Codex at session start
- Contains project architecture, patterns, workflows
- Global + project-level layering

### Skills
- 60+ pre-built skills in Codex (`~/.codex/skills/`)
- Reference-based (no duplication needed)
- Use in prompts: `/code-review-checklist`, `/testing-patterns`

### Configuration
- **User-level**: `~/.codex/config.toml` (global, applies to all projects)
- **Project-level**: `.codex/config.toml` (optional, per-project overrides)

### Session Management
```bash
codex start                  # Start new session
codex resume --last         # Resume last session
codex resume <SESSION_ID>   # Resume specific session
```

## Guides

1. **[Getting Started](./GETTING_STARTED.md)** - Complete setup walkthrough
2. **[Codex vs Claude](./guides/CODEX_vs_CLAUDE.md)** - Feature comparison
3. **[Best Practices](./guides/BEST_PRACTICES.md)** - Codex-specific patterns
4. **[MCP Servers](./guides/MCP_GUIDE.md)** - External tools integration
5. **[Switch Project](./guides/SWITCH_PROJECT_PROMPT.md)** - New project setup
6. **[Troubleshooting](./guides/TROUBLESHOOTING.md)** - Common issues

## Project Templates

### Laravel API
- Service/Repository/DTO patterns
- 260+ console commands management
- Eloquent migrations and relationships

### NestJS API
- Module architecture with DI
- TypeORM entity and migrations
- Decorator-based validation

### Next.js App
- Server Components and data fetching
- App Router navigation
- Deployment on Vercel

## Session Management

Codex maintains full session history:
```bash
# View recent sessions
codex ls

# Resume with history
codex resume --last

# Continue developing without re-explaining context
```

## Integration with Claude Code

You can run **both** Claude Code and Codex CLI:
- Claude Code: `CLAUDE.md` in project root
- Codex CLI: `AGENTS.md` in project root
- Both auto-loaded in respective tools
- Share same project structure

See [Codex vs Claude](./guides/CODEX_vs_CLAUDE.md) for detailed comparison.

## Tips & Best Practices

### Workflow
1. Create AGENTS.md before starting development
2. Keep instructions concise but complete
3. Reference existing patterns in codebase
4. Update AGENTS.md as project evolves

### Performance
- Codex auto-compacts sessions at context limits
- Use `codex resume --last` to continue efficiently
- MCP servers extend context with real-time data

### Team Setup
1. Commit AGENTS.md to version control
2. Exclude `.codex/` (local config)
3. Team reads same AGENTS.md
4. Individual session history in `~/.codex/sessions/`

## License

MIT — Open source, contribute freely

## Community

- [OpenAI Codex Docs](https://developers.openai.com/codex/)
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- Similar project: [claude-howto](https://github.com/luongnv89/claude-howto)

---

**Ready to use Codex efficiently?** → [Get Started](./GETTING_STARTED.md) 🚀
