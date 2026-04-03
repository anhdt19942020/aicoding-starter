# Getting Started with Codex CLI

Complete setup guide for OpenAI Codex CLI with project templates.

## Prerequisites

1. **Codex CLI installed**
   ```bash
   # macOS/Linux
   brew install openai-codex

   # Windows - via npm
   npm install -g @openai/codex
   ```

2. **OpenAI API key**
   ```bash
   export OPENAI_API_KEY="your-key-here"
   # Or configure in ~/.codex/config.toml
   ```

3. **Git** (for version control)

## Step 1: Global Setup

### Copy Global Instructions
```bash
# Copy AGENTS.md to Codex home directory
cp AGENTS.md ~/.codex/

# Copy/merge config
# Review ~/.codex/config.toml and add any needed settings
```

### Verify Setup
```bash
# Check Codex version
codex --version

# List available models
codex list-models
```

## Step 2: Choose Project Template

Select your tech stack:

### Option A: Laravel API
```bash
# Copy template
cp -r templates/laravel-project ~/my-laravel-api

# Customize AGENTS.md
cd ~/my-laravel-api
# Edit AGENTS.md:
# - Update project paths
# - Update port numbers
# - Add your specific domains
```

### Option B: NestJS API
```bash
cp -r templates/nestjs-project ~/my-nestjs-api
cd ~/my-nestjs-api
# Edit AGENTS.md for your project
```

### Option C: Next.js App
```bash
cp -r templates/nextjs-project ~/my-nextjs-app
cd ~/my-nextjs-app
# Edit AGENTS.md for your project
```

## Step 3: Project Configuration

### Create AGENTS.md (Project Instructions)
Copy template and customize:

```markdown
# Project Name — Agent Instructions

## Project Overview
- **Type:** [Framework/Type]
- **Root:** [Your project path]
- **Port:** [Dev port]
- **Commands:** [Key commands]

## Architecture
- [Patterns used]
- [Key modules/domains]
- [Database setup]

## Common Tasks
- [Task 1 with code example]
- [Task 2 with code example]

## Run Commands
```bash
[your dev commands]
```
```

### Create .codex/config.toml (Project Config)
```toml
# .codex/config.toml
[context]
project_doc_max_bytes = 65536  # Max 64KB for AGENTS.md
```

### Add .git/info/exclude
```bash
# Exclude local-only files from git
echo "AGENTS.md" >> .git/info/exclude
echo ".codex/" >> .git/info/exclude
```

## Step 4: Start Using Codex

### Start New Session
```bash
cd ~/your-project
codex start

# Codex will:
# 1. Load AGENTS.md automatically
# 2. Read global instructions
# 3. Initialize session with context
```

### Continue Previous Session
```bash
# Resume most recent session
codex resume --last

# Resume specific session
codex resume <SESSION_ID>

# List recent sessions
codex ls
```

### Common Codex Commands
```bash
codex start              # New session
codex resume --last      # Last session
codex ls                 # List sessions
codex rm <SESSION_ID>    # Delete session
codex --version          # Check version
```

## Step 5: Project Workflow

### Daily Workflow
```
1. Start session
   $ codex start

2. Codex reads:
   - ~/.codex/AGENTS.md (global)
   - {project}/AGENTS.md (project-specific)

3. You code with context
   - Codex remembers architecture
   - You request code review, tests, etc.

4. Continue next day
   $ codex resume --last
   - Full context restored
   - No re-explanation needed
```

### Code Review
```bash
# In session, you ask:
# "Review my PaymentService implementation"

# Codex will:
# 1. Read code
# 2. Check against patterns in AGENTS.md
# 3. Give feedback with improvements
```

### Testing
```bash
# "Create tests for this feature"
# "Why is this test failing?"
# "Help debug this async issue"

# Codex uses testing patterns from AGENTS.md
```

### Switching Projects
```bash
# End current session
exit

# Switch to another project
cd ~/another-project

# Start new session
codex start

# Different AGENTS.md is loaded
# Different architecture context applies
```

## Step 6: Team Setup

### Commit AGENTS.md
```bash
# AGENTS.md is public documentation
git add AGENTS.md
git commit -m "docs: Add Codex project instructions"
git push
```

### Exclude Local Config
```bash
# Don't commit local session data
# .git/info/exclude handles this

# Verify
git status
# AGENTS.md shown (✓ good)
# .codex/ not shown (✓ good)
```

### Team Onboarding
New developers:
1. Clone repo
2. Codex auto-reads AGENTS.md
3. Full context available
4. No setup needed!

## Best Practices

### 1. AGENTS.md Quality
✅ Keep instructions concise but complete
✅ Include code examples
✅ Document architecture clearly
✅ List common tasks with solutions
✅ Update when patterns change

❌ Don't hardcode credentials
❌ Don't include sensitive data
❌ Don't make it too long (stay under 64KB)

### 2. Session Management
✅ Use `codex resume --last` to continue
✅ Start fresh session for new feature
✅ Keep related work in same session
✅ Archive long-running sessions

❌ Don't lose session context
❌ Don't start new session for trivial changes

### 3. Project Structure
✅ One AGENTS.md per project
✅ .codex/ folder in .gitignore
✅ AGENTS.md in version control
✅ Update AGENTS.md with architecture changes

❌ Don't duplicate AGENTS.md across folders
❌ Don't commit .codex/ config

## Troubleshooting

### Session Not Loading
```bash
# Check AGENTS.md exists
ls -la AGENTS.md

# Check it's valid markdown
file AGENTS.md

# Try resuming specific session
codex resume <SESSION_ID>
```

### Context Limit Exceeded
```bash
# Codex auto-compacts, but you can:

# Start fresh session
codex start --fresh

# Or resume and continue
codex resume --last
```

### Credentials Exposure
```bash
# Check for secrets in AGENTS.md
grep -i "password\|api_key\|secret" AGENTS.md

# Remove any found
# Use environment variables instead
```

### Large AGENTS.md
```bash
# Check file size
ls -lh AGENTS.md

# If > 65KB, consider:
# - Moving some content to linked files
# - Creating sub-AGENTS.md files
# - Reference external docs

# Default limit: 65536 bytes (64KB)
```

## Next Steps

1. **Choose template** → Copy to your project
2. **Customize AGENTS.md** → Update with your details
3. **Setup .codex/config.toml** → Project-level config
4. **Add to .git/info/exclude** → Keep local files local
5. **Start coding!** → `codex start`

## Additional Resources

- [Codex API Reference](https://developers.openai.com/codex/)
- [MCP Servers Guide](./MCP_GUIDE.md)
- [Best Practices](./BEST_PRACTICES.md)
- [Codex vs Claude](./CODEX_vs_CLAUDE.md)

---

**Ready?** Pick a template and start coding! 🚀
