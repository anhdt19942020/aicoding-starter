# Cursor IDE Setup Guide

Complete installation and configuration for Cursor (AI-powered code editor).

---

## What is Cursor?

**Cursor** is an AI-first code editor built on VS Code with integrated AI assistance:
- Claude API integration (uses Claude models)
- File reading/writing in IDE
- Code preview and debugging
- Git integration
- Terminal access
- Superior autocomplete

**Best for:** Full-stack development, component creation, UI/UX work

---

## Prerequisites

- ✅ Cursor installed → https://cursor.com
- ✅ Anthropic API key (optional, uses Claude)
- ✅ Git installed
- ✅ Code editor experience

---

## Step 1: Install Cursor

### Download & Install
1. Go to https://cursor.com
2. Download for your OS (Windows, macOS, Linux)
3. Install like any application
4. Launch Cursor

### Verify Installation
```bash
# Check if cursor command available
cursor --version

# Or open from terminal
cursor ~/your-project
```

---

## Step 2: Configure Claude Models

### Option A: Use Cursor Default
Cursor comes with built-in Claude API access (recommended for most users).

No extra setup needed!

### Option B: Bring Your Own API Key
If using your own Anthropic API:

1. Go to https://console.anthropic.com/keys
2. Create new API key
3. In Cursor:
   - Settings → Extensions → Cursor Settings
   - Paste API key under "Anthropic API Key"

---

## Step 3: Clone This Repository

```bash
# Clone codex-howto
git clone https://github.com/yourusername/codex-howto
cd codex-howto

# Copy Cursor instructions
cp CURSOR.md ~/.cursor/
```

---

## Step 4: Setup Your Project

### Choose Template
```bash
# Option 1: Laravel
cp -r templates/laravel-project ~/my-project

# Option 2: NestJS
cp -r templates/nestjs-project ~/my-project

# Option 3: Next.js
cp -r templates/nextjs-project ~/my-project
```

### Create CLAUDE.md (Project Instructions)
Copy from template or create new:

```markdown
# Project Name — Claude Code Instructions

## Project Overview
- **Type:** [Your framework]
- **Root:** ~/my-project
- **Port:** [Your port]

## Architecture
- [Your patterns]
- [Your services]
- [Your database]

## Common Tasks
- [Create endpoint]
- [Write tests]
- [Deploy]

## Run Commands
npm run dev
npm test
npm run build
```

### Setup Git
```bash
cd ~/my-project

# Add CLAUDE.md
git add CLAUDE.md

# Exclude Cursor local files
echo ".cursor/" >> .git/info/exclude

git commit -m "docs: Add Cursor project instructions"
```

---

## Step 5: Open in Cursor

```bash
# Option 1: Command line
cursor ~/my-project

# Option 2: Cursor → File → Open Folder → select ~/my-project

# Option 3: Drag folder into Cursor window
```

---

## Step 6: Start Coding

### Claude Composer (Main Feature)
1. Press `Ctrl+K` (or `Cmd+K` on Mac)
2. Describe what you want: "Create a new API endpoint for payments"
3. Claude generates code
4. Review → Accept → Done

### Cursor Features

**Inline Code Generation**
```
Press Ctrl+K and type:
"Add error handling to this function"
```

**Code Search**
```
Cmd+Shift+I (macOS) or Ctrl+Shift+I (Windows/Linux)
Search codebase with natural language
```

**Chat Panel**
```
Press Ctrl+L to open Chat
Ask questions about your code
Get explanations, debugging help
```

**Codebase Understanding**
```
Cursor reads your entire codebase
Understands context from CLAUDE.md
Generates code consistent with patterns
```

---

## Cursor Settings

### Recommended Settings

**File → Preferences → Settings:**

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[python]": {
    "editor.defaultFormatter": "ms-python.python"
  },
  "cursor.general.notificationLevel": "messages",
  "cursor.chat.contextLength": "full"
}
```

### Keyboard Shortcuts
- `Ctrl+K` — Code generation (in editor)
- `Ctrl+L` — Chat panel (ask questions)
- `Ctrl+Shift+I` — Code search (natural language)
- `Ctrl+/` — Toggle comment
- `Ctrl+S` — Save file (triggers formatter)

---

## Workflow: Cursor + Codex CLI

Use **both together** for maximum productivity:

```
Frontend Work:
→ Cursor IDE
→ React components
→ CLAUDE.md for patterns
→ Preview servers

Backend Work:
→ Codex CLI
→ NestJS services
→ AGENTS.md for patterns
→ Extended thinking (o3)

Deployment:
→ Antigravity
→ Git workflows
→ Merge management
```

---

## Integration with Codex CLI & Antigravity

### All Three Tools

```
Project Structure:
├── CLAUDE.md           ← For Cursor
├── AGENTS.md           ← For Codex CLI
├── ANTIGRAVITY.md      ← For Antigravity
└── ...code files

Workflow:
1. Cursor: Component development + UI
2. Codex CLI: Service development + reasoning
3. Antigravity: Git management + deployment
```

---

## Common Tasks in Cursor

### Create React Component
```
Press Ctrl+K
"Create a Button component with Tailwind styling"

Cursor generates:
- Functional component
- Props typing
- Tailwind classes
- Export statement
```

### Write Tests
```
Press Ctrl+K
"Write unit tests for this function using Jest"

Cursor generates:
- Test file structure
- Test cases
- Mock setup
- Assertions
```

### Debug Issue
```
Press Ctrl+L
"Why is this component not rendering?"

Chat explains:
- Root cause
- How to fix
- Shows example code
```

### Refactor Code
```
Press Ctrl+K
"Refactor this to use hooks instead of class"

Cursor converts:
- Class component → Functional
- setState → useState
- Lifecycle → useEffect
```

---

## Cursor vs Claude Code vs Codex CLI

| Feature | Cursor | Claude Code | Codex CLI |
|---------|--------|------------|-----------|
| **IDE Integration** | ✅ Full | ✅ Full | ❌ CLI only |
| **Code Generation** | ✅ Yes | ✅ Yes | ✅ Yes |
| **File Tools** | ✅ Yes | ✅ Yes | ⚠️ Limited |
| **Preview Servers** | ✅ Yes | ✅ Yes | ❌ No |
| **Chat** | ✅ Yes | ✅ Yes | ✅ Yes |
| **Extended Thinking** | ❌ No | ❌ No | ✅ o3 model |
| **Cost** | Subscription | Subscription | Pay-per-token |
| **Best For** | Full-stack | All tasks | Backend/complex |

---

## Tips & Tricks

### 1. Use Context with CLAUDE.md
Cursor reads CLAUDE.md for context:
- Architecture patterns
- Code style guidelines
- Common patterns
- Examples

Make CLAUDE.md comprehensive!

### 2. Leverage Chat for Refactoring
```
Cmd+L (open chat)
"Refactor this to follow our patterns from CLAUDE.md"
```

### 3. Use Code Search
```
Cmd+Shift+I
"How do we handle authentication?"
Cursor finds examples in codebase
```

### 4. Generate from Comments
```
// Create a user service with validation
Ctrl+K → generates implementation
```

### 5. Ask for Tests Immediately
```
Generate endpoint → Ctrl+K → "Write tests for this"
```

---

## Troubleshooting

### Issue: Cursor not generating code

**Solution:**
1. Check CLAUDE.md exists in project
2. Restart Cursor
3. Check API key configuration
4. Verify Claude models are available

### Issue: Code quality poor

**Solution:**
1. Improve CLAUDE.md documentation
2. Add more code examples
3. Specify patterns clearly
4. Provide context in comments

### Issue: Slow generation

**Solution:**
1. Reduce CLAUDE.md size
2. Use inline comments for context
3. Close unused tabs
4. Check internet connection

---

## Best Practices

### 1. Maintain CLAUDE.md
- Update patterns as they evolve
- Add code examples
- Document architecture
- Share with team

### 2. Use Comments for Context
```typescript
// Create payment service following the pattern:
// 1. Validate input with DTO
// 2. Call repository
// 3. Dispatch event
// 4. Return result
```

### 3. Review Generated Code
- Don't blindly accept
- Check against CLAUDE.md
- Verify tests
- Test manually

### 4. Combine with Codex CLI
- Use Cursor for UI/components
- Use Codex for backend/complex logic
- Share AGENTS.md + CLAUDE.md
- Consistent architecture

---

## Next Steps

1. ✅ Install Cursor
2. ✅ Configure Claude models
3. ✅ Clone codex-howto
4. ✅ Setup project with template
5. ✅ Create CLAUDE.md
6. ✅ Open in Cursor
7. ✅ Start coding with Ctrl+K

---

## Resources

- **Cursor Docs:** https://docs.cursor.com
- **This Repository:** README.md → GETTING_STARTED.md
- **Project Instructions:** CLAUDE.md (in your project)
- **Best Practices:** guides/BEST_PRACTICES.md

---

**Ready to code with Cursor?** Open your project and press `Ctrl+K` to start! 🚀
