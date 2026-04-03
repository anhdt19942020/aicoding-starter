# Switch Project Prompt — Codex CLI

Use this prompt when setting up a **new project** for Codex CLI.

---

## Prompt to Copy & Paste

```
I'm setting up a new project for Codex CLI. Please help me create the necessary files.

Project Info:
- Project name: {PROJECT_NAME}
- Project path: {PROJECT_PATH}
- Tech stack: {TECH_STACK} (e.g., Laravel, NestJS, Next.js)
- Project type: {TYPE} (e.g., API, Web App, Full-stack)
- Database: {DATABASE} (e.g., MySQL, PostgreSQL, MongoDB)

Please create:

1. **AGENTS.md** in {PROJECT_PATH}
   - Project overview (type, path, port, dev commands)
   - Architecture overview (modules, layers, patterns)
   - Key domains (list the main features/domains)
   - Common tasks with code examples (new endpoint, new migration, new test)
   - Error handling approach
   - Run commands (dev, test, build, database)
   - Before committing checklist

2. **.codex/config.toml** in {PROJECT_PATH}
   - Set project_doc_max_bytes = 65536
   - (Keep rest minimal, inherit from global ~/.codex/config.toml)

3. **.git/info/exclude** updates
   - Add: AGENTS.md
   - Add: .codex/

4. **Summary**
   - List all files created
   - Show AGENTS.md content
   - Ready to code ✅
```

---

## How to Use

### Step 1: Fill in Project Details
Replace placeholders:
- `{PROJECT_NAME}` — e.g., "Payment Processing API"
- `{PROJECT_PATH}` — e.g., "D:\projects\payment-api"
- `{TECH_STACK}` — e.g., "NestJS + TypeScript"
- `{TYPE}` — e.g., "Backend API"
- `{DATABASE}` — e.g., "PostgreSQL"

### Step 2: Copy & Paste into Codex
```bash
codex start
# Paste the prompt above into the chat
```

### Step 3: Codex Creates Files
Codex will create:
- ✅ AGENTS.md with full project instructions
- ✅ .codex/config.toml with project config
- ✅ Updates to .git/info/exclude
- ✅ Ready for development!

### Step 4: Start Coding
```bash
codex resume --last
# Continue with your work
```

---

## Example

```
I'm setting up a new project for Codex CLI. Please help me create the necessary files.

Project Info:
- Project name: E-Learning Platform API
- Project path: D:\projects\elearning-api
- Tech stack: NestJS + TypeScript
- Project type: REST API
- Database: PostgreSQL

Please create:

1. **AGENTS.md** in D:\projects\elearning-api
   - Project overview (NestJS, port 3000, npm run start:dev)
   - Architecture with modules: course, student, enrollment, payment
   - Common tasks with code examples
   - Error handling and logging strategy
   - Run commands for dev, test, migrations
   - Before committing checklist

2. **.codex/config.toml** in D:\projects\elearning-api
   - Set project_doc_max_bytes = 65536

3. **.git/info/exclude** updates
   - Add AGENTS.md and .codex/

4. **Summary**
   - Show created files
   - Display AGENTS.md content
   - Ready to code ✅
```

---

## Template Selection

You can also reference the templates:
- **Laravel Template:** From codex-howto/templates/laravel-project/AGENTS.md
- **NestJS Template:** From codex-howto/templates/nestjs-project/AGENTS.md
- **Next.js Template:** From codex-howto/templates/nextjs-project/AGENTS.md

Or ask Codex to create from scratch based on your stack.

---

## Global vs Project

- **Global (~/.codex/AGENTS.md):** Shared across all projects
- **Project ({project}/AGENTS.md):** Project-specific instructions
- **Both are auto-read:** Codex loads both and merges

---

## After Setup

1. ✅ Codex auto-reads AGENTS.md
2. ✅ Full context loaded automatically
3. ✅ No manual context pasting needed
4. ✅ Session history maintained across days
5. ✅ Team-friendly (commit AGENTS.md to git)

---

**Copy this prompt, fill in your project details, and paste into Codex!** 🚀
