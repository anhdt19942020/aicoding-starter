# Complete Guide: Cursor + Codex CLI + Antigravity

How to use all three tools together for maximum productivity.

---

## The Three Tools

### 🎯 Cursor IDE
**What:** AI-first code editor
**Best for:** Component creation, UI/UX, full-stack development
**Interface:** IDE (Visual)
**Models:** Claude (Anthropic)

### 🤖 Codex CLI
**What:** CLI-based AI assistant
**Best for:** Backend services, complex logic, extended reasoning
**Interface:** Terminal (CLI)
**Models:** GPT-4o, o3, o4-mini (OpenAI)

### 📊 Antigravity
**What:** Git-integrated IDE
**Best for:** Version control, PRs, team collaboration, deployment
**Interface:** IDE + Git (Visual)
**Models:** AI for commit messages

---

## When to Use Each Tool

### Scenario 1: Building React Component
```
Tool: Cursor
Why: IDE features, preview, Ctrl+K for code generation
Process:
  1. Cursor: Create component with Cmd+K
  2. Cursor: Write tests with Cmd+K
  3. Antigravity: Commit changes
```

### Scenario 2: Building API Service
```
Tool: Codex CLI
Why: o3 reasoning, extended thinking
Process:
  1. Codex: `codex start`
  2. Codex: "Create payment service"
  3. Codex: "Review and test"
  4. Cursor: Refine UI that calls service
  5. Antigravity: Commit and push
```

### Scenario 3: Complex Algorithm
```
Tool: Codex CLI with o3
Why: Extended thinking for complex problems
Process:
  1. Codex: Use o3 model for reasoning
  2. Codex: "Design this algorithm"
  3. Cursor: Integrate into UI
  4. Antigravity: Commit
```

### Scenario 4: Team Collaboration
```
Tool: Antigravity (primary)
Supporting: Cursor + Codex
Process:
  1. Antigravity: Create feature branch
  2. Cursor: Develop component
  3. Codex: Develop service
  4. Antigravity: Commit and create PR
  5. Antigravity: Team reviews and merges
```

### Scenario 5: Fixing Bug
```
Tool: Depends on bug type
If UI bug:
  → Cursor for debugging
If logic bug:
  → Codex for reasoning
Final:
  → Antigravity for commit
```

---

## Project Structure for All Three

### Files Each Tool Uses

```
~/my-project/
├── CLAUDE.md           ← Cursor reads this
├── AGENTS.md           ← Codex CLI reads this
├── ANTIGRAVITY.md      ← Antigravity reference
├── src/
│   ├── components/     ← Develop in Cursor
│   ├── services/       ← Develop in Codex CLI
│   └── utils/
├── tests/              ← Write in Cursor or Codex
├── .git/               ← Managed by Antigravity
└── package.json
```

### How Each Tool Sees the Project

**Cursor sees:**
- Project structure
- Code files
- CLAUDE.md (instructions)
- Can edit files directly

**Codex CLI sees:**
- Project files (via terminal)
- AGENTS.md (instructions)
- Session-based context
- Full control via commands

**Antigravity sees:**
- Git repository structure
- Branches
- Commits
- PRs (integrated with GitHub/GitLab)

---

## Complete Workflow Example

### Day 1: Start New Feature

```
1. Create Issue in GitHub
   Title: "Add Payment Processing"
   Issue #123

2. Antigravity: Create feature branch
   Branch: feature/payment-processing (#123)
   Base: develop

3. Codex: Design the service
   $ codex start
   "Design payment service for issue #123"
   Uses: o3 model for complex logic
   Output: PaymentService structure

4. Cursor: Create service implementation
   Open in Cursor
   Cmd+K: "Implement PaymentService"
   Review generated code
   Cmd+K: "Write tests for PaymentService"

5. Cursor: Create React component
   Cmd+K: "Create PaymentForm component"
   Cmd+K: "Add form validation"

6. Antigravity: Commit
   Stage all files
   Commit message: "feat: Add payment processing (#123)"
   Push to feature branch
```

### Day 2: Code Review & Merge

```
1. Antigravity: Create Pull Request
   Title: "Add payment processing (#123)"
   Description: Changes summary
   Request review from team

2. Team: Review in Antigravity
   Check code quality
   Suggest improvements
   Approve or request changes

3. Developer: Address feedback
   Fix issues in Cursor or Codex
   Commit updates
   Push updates (PR auto-updates)

4. Antigravity: Merge
   All reviews approved
   All CI checks pass
   Squash commits
   Merge to develop
   Delete feature branch
   Close issue #123

5. Auto-Deploy
   Merge triggers deployment
   Tests run
   Deploys to staging
   Ready for production
```

---

## Keyboard Shortcuts

### Cursor Shortcuts
| Action | Shortcut |
|--------|----------|
| Code Generation | Cmd+K / Ctrl+K |
| Chat | Cmd+L / Ctrl+L |
| Search | Cmd+Shift+I / Ctrl+Shift+I |
| Terminal | Cmd+` / Ctrl+` |
| Save | Cmd+S / Ctrl+S |

### Antigravity Shortcuts
| Action | Shortcut |
|--------|----------|
| Commit | Cmd+Enter / Ctrl+Enter |
| Pull | Cmd+Shift+I / Ctrl+Shift+I |
| Push | Cmd+Shift+O / Ctrl+Shift+O |
| Create Branch | Cmd+Shift+B / Ctrl+Shift+B |

### Codex CLI Commands
| Action | Command |
|--------|---------|
| Start | `codex start` |
| Resume | `codex resume --last` |
| List Sessions | `codex ls` |
| Help | `codex --help` |

---

## Switching Between Tools

### From Cursor to Codex CLI

```
1. Terminal in Cursor: Cmd+`
2. Type: codex resume --last
3. Codex loads session
4. Switch between two side-by-side
```

### From Codex CLI to Antigravity

```
1. In Codex session: Finish changes
2. Minimize/close Codex
3. Open Antigravity
4. View changes in Git
5. Commit and push
```

### From Antigravity to Cursor

```
1. In Antigravity: Pull latest
2. Switch to Cursor
3. Changes auto-update
4. Continue development
```

---

## Best Practices for All Three

### 1. Keep Instructions Updated
```
Maintain:
  - CLAUDE.md for Cursor patterns
  - AGENTS.md for Codex patterns
  - ANTIGRAVITY.md for git workflow
Share with team
```

### 2. Consistent Patterns
```
All tools should:
  - Use same architecture
  - Follow same naming conventions
  - Write tests the same way
  - Commit with same format
```

### 3. Clear Communication
```
Document:
  - What each tool is used for
  - When to use which tool
  - How changes flow through tools
  - Team preferences
```

### 4. Leverage Tool Strengths
```
Cursor:    UI/Components (Cmd+K generation)
Codex:     Services/Logic (o3 reasoning)
Antigravity: Git/Collaboration (PR workflow)
```

### 5. Avoid Duplication
```
Don't use:
  - Cursor for complex logic (use Codex)
  - Codex for UI (use Cursor)
  - Antigravity for coding (use Cursor/Codex)
```

---

## Common Questions

### Q: Can I use just one tool?
```
A: Yes, but losing benefits:
  - Cursor only: Hard to do backend logic
  - Codex only: No IDE features
  - Antigravity only: Can't code efficiently

Combination is optimal.
```

### Q: Which tool should I start with?
```
A: Depends on task:
  - UI work → Cursor first
  - Logic work → Codex first
  - Git work → Antigravity first
  - New feature → Codex (design), then Cursor (UI)
```

### Q: Do I need all three?
```
A: For solo development:
  - Cursor + Codex = sufficient
  - Can use git command line

For team development:
  - All three = optimal
  - Better collaboration
```

### Q: How do costs compare?
```
Cursor:  Subscription
Codex:   Pay-per-token
Antigravity: Free (GitKraken paid version)

Total for 1 dev:
  Cursor: $20/month
  Codex: $50-100/month (if used heavily)
  Antigravity: $7-12/month (team plan)
```

### Q: Can I switch tools mid-development?
```
A: Yes!
  1. Codex: Design service
  2. Cursor: Implement component
  3. Codex: Test service
  4. Cursor: Test component
  5. Antigravity: Commit all

All work in same repo.
```

---

## Example Projects

### Project 1: Blog Platform
```
Codex CLI:  Blog service, database queries
Cursor:     React components, UI
Antigravity: Team collaboration, deployment
```

### Project 2: E-Commerce API
```
Codex CLI:  Payment, inventory, order services
Cursor:     Admin dashboard UI
Antigravity: Release management
```

### Project 3: Mobile App Backend
```
Codex CLI:  API services, authentication
Cursor:     Web dashboard UI
Antigravity: Deployment to staging/prod
```

---

## Troubleshooting

### Issue: Code style inconsistent between tools

**Solution:**
```
1. Setup linter (ESLint, Prettier)
2. Configure in Cursor (.prettierrc)
3. Add pre-commit hooks in Antigravity
4. All tools format consistently
```

### Issue: Merge conflicts

**Solution:**
```
1. Cursor: Resolve locally
2. Or Antigravity: Resolve in UI
3. Stage resolved files
4. Commit
```

### Issue: Lost work

**Solution:**
```
1. Antigravity: Check git history
2. Can revert commits
3. Stash feature branches
4. All work recoverable in git
```

---

## Team Onboarding

### New Developer Setup
```
1. Install Cursor, Codex CLI, Antigravity
2. Clone repository
3. Read:
   - CLAUDE.md (Cursor patterns)
   - AGENTS.md (Codex patterns)
   - ANTIGRAVITY.md (git workflow)
4. Create feature branch
5. Start developing
```

### Team Guidelines
```
Document:
  - Who uses which tool
  - Common workflows
  - How to handle conflicts
  - Deployment process
  - Code review expectations
```

---

## Summary

| Aspect | Cursor | Codex | Antigravity |
|--------|--------|-------|------------|
| **Installation** | Easy | Moderate | Easy |
| **Learning Curve** | Low | Moderate | Low |
| **Best For** | UI/Components | Backend/Logic | Git/Collaboration |
| **Cost** | $20/mo | $50-100/mo | Free-$12/mo |
| **Team Work** | Good | Good | Best |
| **Solo Work** | Good | Good | OK |
| **Reasoning** | Good | Excellent | N/A |

---

**Use all three together for optimal development experience!** 🚀
