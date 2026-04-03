# Codex How-To Setup Summary

Complete repository for mastering OpenAI Codex CLI. Similar to [claude-howto](https://github.com/luongnv89/claude-howto) but optimized for Codex.

---

## 📂 What's Included

### Core Documentation
- ✅ **README.md** — Overview and quick start
- ✅ **GETTING_STARTED.md** — Step-by-step setup guide
- ✅ **AGENTS.md** — Global instructions template

### Project Templates (Choose One)
- ✅ **templates/laravel-project/** — Laravel API template with AGENTS.md
- ✅ **templates/nestjs-project/** — NestJS API template with AGENTS.md
- ✅ **templates/nextjs-project/** — Next.js App template with AGENTS.md

### Configuration
- ✅ **.codex/config.toml** — Global Codex configuration template
- ✅ **templates/*/**.codex/config.toml** — Project-level config templates

### Guides
- ✅ **guides/SWITCH_PROJECT_PROMPT.md** — Setup new projects automatically
- ✅ **guides/CODEX_vs_CLAUDE.md** — Comparison with Claude Code
- ✅ **guides/BEST_PRACTICES.md** — Production patterns and optimization

### Utilities
- ✅ **.gitignore** — Git ignore patterns for projects
- ✅ This file — Setup summary and quick reference

---

## 🚀 Quick Start

### 1. Clone Repository
```bash
git clone https://github.com/yourusername/codex-howto
cd codex-howto
```

### 2. Setup Global Config
```bash
# Copy global instructions
cp AGENTS.md ~/.codex/

# Merge config (review and customize)
# Merge .codex/config.toml into ~/.codex/config.toml
```

### 3. Choose & Copy Template
```bash
# Option A: Laravel
cp -r templates/laravel-project ~/my-project

# Option B: NestJS
cp -r templates/nestjs-project ~/my-project

# Option C: Next.js
cp -r templates/nextjs-project ~/my-project
```

### 4. Customize AGENTS.md
```bash
cd ~/my-project

# Edit AGENTS.md:
# - Update project paths
# - Update port numbers
# - Add your specific domains/features
# - Add code examples
```

### 5. Add to Git
```bash
# Add AGENTS.md to project (shared with team)
git add AGENTS.md

# Exclude local config
echo ".codex/" >> .git/info/exclude
echo "AGENTS.md" >> .git/info/exclude  # Or keep in git, your choice

git commit -m "docs: Add Codex project instructions"
```

### 6. Start Coding
```bash
codex start
# Codex reads AGENTS.md automatically
# Full context ready!
```

---

## 📖 Documentation Guide

### For Setup
1. Start: **README.md** — Overview
2. Follow: **GETTING_STARTED.md** — Step-by-step
3. Create: Copy templates → customize AGENTS.md

### For Development
1. Reference: **guides/BEST_PRACTICES.md** — Patterns
2. Compare: **guides/CODEX_vs_CLAUDE.md** — When to use Codex
3. Automate: **guides/SWITCH_PROJECT_PROMPT.md** — New projects

### For Implementation
1. Choose template matching your tech stack
2. Copy AGENTS.md from template
3. Customize with your project details
4. Commit to git, share with team

---

## 🎯 Key Files Overview

### AGENTS.md (Global Template)
**Purpose:** Shared instructions for all projects
**Location:** `~/.codex/AGENTS.md` (after setup)
**Contents:**
- Workflow rules (code quality, architecture)
- API design principles
- Database management patterns
- Security guidelines
- Testing strategy
- Git & commit practices

### AGENTS.md (Project Templates)
**Purpose:** Project-specific instructions
**Location:** `{project}/AGENTS.md`
**Contents:**
- Project overview (type, path, port, commands)
- Architecture (modules, layers, patterns)
- Key domains/features
- Common tasks with code examples
- Error handling
- Run commands
- Before committing checklist

### .codex/config.toml (Global)
**Purpose:** Global Codex configuration
**Location:** `~/.codex/config.toml`
**Contents:**
- Default model (gpt-4o, o3, o4-mini)
- Context settings (AGENTS.md max size)
- Behavior (auto-compact, timeout)

### .codex/config.toml (Project)
**Purpose:** Project-level config overrides
**Location:** `{project}/.codex/config.toml`
**Contents:** Usually minimal (inherit from global)

---

## 🔄 Workflow Summary

### First Time Setup
```
Clone repo
    ↓
Copy AGENTS.md to ~/.codex/
    ↓
Choose template (Laravel/NestJS/Next.js)
    ↓
Copy template to your project
    ↓
Customize AGENTS.md
    ↓
Commit AGENTS.md to git
    ↓
Exclude .codex/ in .git/info/exclude
    ↓
Ready to code!
```

### Daily Workflow
```
codex start              ← First time, creates new session
    ↓
AGENTS.md auto-loaded   ← Codex reads it
    ↓
You develop             ← Code, test, commit
    ↓
codex resume --last     ← Continue next day
    ↓
Full context restored   ← No re-explanation needed
```

### Team Workflow
```
All team members:
    ↓
Clone project
    ↓
AGENTS.md in repo (shared)
    ↓
codex start
    ↓
Same context for everyone ✅
```

---

## 📊 Configuration Hierarchy

```
Global (applies everywhere):
~/.codex/AGENTS.md          ← Global instructions
~/.codex/config.toml        ← Global config

Project-Specific (overrides global):
{project}/AGENTS.md         ← Project instructions
{project}/.codex/config.toml ← Project config

Result:
Codex loads both and merges:
1. Global settings/patterns
2. Project-specific details
3. Combined context ready
```

---

## 🛠 Customization Guide

### Customize AGENTS.md for Your Project

1. **Update Overview:**
```markdown
## Project Overview
- **Type:** Your framework
- **Root:** Your project path
- **Port:** Your dev port
```

2. **Update Architecture:**
```markdown
## Architecture
- [Your modules]
- [Your patterns]
- [Your database]
```

3. **Add Your Domains:**
```markdown
## Key Domains
- Payment processing
- User management
- Reporting
```

4. **Add Code Examples:**
```typescript
## Create New Endpoint
1. Create DTO
2. Create Controller
3. Create Service

## Example:
[Your actual code examples]
```

5. **Update Commands:**
```bash
## Run Commands
npm run dev              # Your dev command
npm test               # Your test command
npm run build          # Your build command
```

---

## 🎓 Learning Path

### Beginner
1. Read: README.md
2. Read: GETTING_STARTED.md
3. Copy: One template
4. Customize: AGENTS.md
5. Code: Start your first session

### Intermediate
1. Read: BEST_PRACTICES.md
2. Read: CODEX_vs_CLAUDE.md
3. Optimize: Session management
4. Reference: Code examples in AGENTS.md
5. Share: AGENTS.md with team

### Advanced
1. Create: Custom templates
2. Extend: AGENTS.md for complex projects
3. Optimize: Token usage and cost
4. Automate: New project setup with prompt
5. Collaborate: Multi-developer workflows

---

## 🔗 Integration with Claude Code

You can use **both** Codex CLI and Claude Code:

```
Codex CLI (Backend/Complex):
- AGENTS.md in project root
- API, architecture, databases
- o3 model for reasoning

Claude Code (Frontend/UI):
- CLAUDE.md in project root
- React components, styling
- Preview servers

Both:
- Share project structure
- Different AGENTS/CLAUDE files
- Complementary strengths
```

See **guides/CODEX_vs_CLAUDE.md** for details.

---

## 📝 Before Using

### Prerequisites
- ✅ Codex CLI installed (`brew install openai-codex`)
- ✅ OpenAI API key configured
- ✅ Git installed (for version control)
- ✅ Your project directory ready

### Configuration Needed
- ✅ `~/.codex/config.toml` — Global settings
- ✅ `~/.codex/AGENTS.md` — Global instructions
- ✅ `{project}/AGENTS.md` — Project instructions
- ✅ `{project}/.codex/config.toml` — Project config

---

## 🎯 Next Steps

1. **Read:** Start with README.md → GETTING_STARTED.md
2. **Choose:** Pick a template matching your tech stack
3. **Setup:** Copy template, customize AGENTS.md
4. **Code:** `codex start` and begin development
5. **Optimize:** Reference BEST_PRACTICES.md for patterns
6. **Share:** Commit AGENTS.md to git for team collaboration

---

## 📚 Additional Resources

### In This Repository
- [README.md](./README.md) — Project overview
- [GETTING_STARTED.md](./GETTING_STARTED.md) — Setup walkthrough
- [guides/BEST_PRACTICES.md](./guides/BEST_PRACTICES.md) — Patterns
- [guides/CODEX_vs_CLAUDE.md](./guides/CODEX_vs_CLAUDE.md) — Comparison
- [guides/SWITCH_PROJECT_PROMPT.md](./guides/SWITCH_PROJECT_PROMPT.md) — Automation

### External Resources
- [OpenAI Codex Docs](https://developers.openai.com/codex/)
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [Claude Code Similar Project](https://github.com/luongnv89/claude-howto)

---

## 📞 Support

### For Codex Issues
- Check: [OpenAI Codex Documentation](https://developers.openai.com/codex/)
- Reference: Local AGENTS.md for project patterns

### For This Repository
- Fork and customize templates for your needs
- Update AGENTS.md as your architecture evolves
- Share findings with your team

---

## 📄 License

MIT — Open source, contribute freely

---

**Ready to use Codex efficiently?** → [Get Started](./GETTING_STARTED.md) 🚀

Last Updated: April 2026
