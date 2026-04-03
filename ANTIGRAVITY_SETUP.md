# Antigravity Setup Guide

Complete installation and configuration for Antigravity (GitKraken AI IDE).

---

## What is Antigravity?

**Antigravity** (by GitKraken) is an AI-powered IDE built for developers who work with Git:
- Git-first workflow (visual Git management)
- AI-assisted coding (integrated AI)
- Full IDE features (terminal, debugging, etc.)
- Beautiful UI (modern, intuitive)
- Cross-platform (Windows, macOS, Linux)

**Best for:** Git-heavy workflows, DevOps, deployment management, team coordination

---

## Prerequisites

- ✅ Antigravity installed → https://www.gitkraken.com/antigravity
- ✅ Git installed and configured
- ✅ GitHub/GitLab account (optional, for remotes)
- ✅ Code editor experience

---

## Step 1: Install Antigravity

### Download & Install
1. Go to https://www.gitkraken.com/antigravity
2. Download for your OS (Windows, macOS, Linux)
3. Install the application
4. Launch Antigravity

### Verify Installation
```bash
# Check if antigravity available
antigravity --version

# Or from any Git repository
antigravity .
```

---

## Step 2: Configure Git Integration

### Setup Git Credentials
```bash
# Configure Git user
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# Setup SSH key (optional, recommended)
ssh-keygen -t ed25519 -C "your@email.com"
# Follow prompts, save to ~/.ssh/id_ed25519
```

### Configure GitHub/GitLab (Optional)
1. Open Antigravity
2. Settings → Integrations
3. Connect GitHub or GitLab
4. Authorize account

---

## Step 3: Clone This Repository

```bash
# Clone codex-howto
git clone https://github.com/yourusername/codex-howto
cd codex-howto

# Copy Antigravity instructions
cp ANTIGRAVITY.md ~/.antigravity/
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

### Create ANTIGRAVITY.md (Project Instructions)
Copy from template or create new:

```markdown
# Project Name — Antigravity Setup

## Git Workflow
- Main branch: production
- Develop branch: staging
- Feature branches: feature/*

## Merge Strategy
- Squash commits
- Require PR review
- Delete branch after merge

## Deployment
- Push to develop → Auto-deploy to staging
- Merge to main → Auto-deploy to production

## Common Git Tasks
- Create feature branch
- Commit with AI suggestions
- Create pull request
- Code review
- Merge and deploy
```

### Setup Git Repository
```bash
cd ~/my-project

# Initialize if not already
git init

# Add remote (if using GitHub)
git remote add origin https://github.com/yourusername/my-project

# Create initial commit
git add .
git commit -m "Initial commit"

# Create branches
git checkout -b develop
git push -u origin develop

git checkout -b main
git push -u origin main
```

---

## Step 5: Open in Antigravity

```bash
# Option 1: Command line
cd ~/my-project
antigravity .

# Option 2: Antigravity → Open Repository → select ~/my-project

# Option 3: Drag folder into Antigravity
```

---

## Step 6: Start Working

### Git Workflow in Antigravity

**1. Create Feature Branch**
```
Left panel → Branches → Create Branch
Name: feature/payment-endpoint
Base: develop
```

**2. Make Changes**
```
Editor: Write code
AI Suggestions: Available
```

**3. Commit Changes**
```
Bottom panel → Changes
Select files → Stage
Write message (AI can help)
Commit
```

**4. Create Pull Request**
```
Right panel → Create Pull Request
Title & description
Push to remote
Create on GitHub/GitLab
```

**5. Review & Merge**
```
Review code
Approve if ready
Merge to develop/main
Delete branch
```

---

## Antigravity Features

### 1. Visual Git Graph
```
Left panel shows:
- All branches
- Commit history
- Tags
- Remotes
- Stashes
```

### 2. AI Commit Messages
```
Write code → Stage changes
Antigravity suggests commit message
Accept or edit
Commit
```

### 3. Git Management
```
Easy to:
- Create/delete branches
- Checkout branches
- Rebase branches
- Cherry-pick commits
- Revert commits
- Squash commits
```

### 4. Pull Request Management
```
Integrated PR workflow:
- Create PR in UI
- Review code
- Approve
- Merge
- Delete branch
```

### 5. Code Editor
```
Built-in editor:
- Syntax highlighting
- Formatting
- Linting
- Debugging
- Terminal access
```

---

## Workflow: Antigravity + Codex + Cursor

Use **all three together** for complete workflow:

```
Development:
├─ Cursor: Component/service development
└─ Codex: Complex logic + testing

Version Control:
└─ Antigravity: Git management + PRs

Deployment:
└─ Antigravity: Merge & deploy
```

### Example Workflow

```
1. Feature idea
   → Create feature branch in Antigravity

2. Development
   → Write code in Cursor/Codex
   → Test with Codex CLI (o3 reasoning)

3. Ready to commit
   → Antigravity suggests commit message
   → Review changes in Git graph
   → Commit

4. Push & PR
   → Antigravity creates PR
   → Team reviews
   → Approve

5. Merge & Deploy
   → Merge in Antigravity
   → Auto-deploy via webhook
   → Monitor in Antigravity
```

---

## Common Git Tasks in Antigravity

### Task 1: Create Feature Branch
```
1. Left panel → Branches
2. Right-click develop → Create branch from here
3. Name: feature/your-feature
4. Confirm
```

### Task 2: Sync with Remote
```
1. Top menu → Pull (get latest)
2. Work on your feature
3. Top menu → Push (send to remote)
```

### Task 3: Create Pull Request
```
1. Right panel → Create Pull Request
2. Select base branch: develop
3. Add title & description
4. Click Create Pull Request
```

### Task 4: Resolve Merge Conflict
```
1. Antigravity detects conflict
2. Shows files with conflicts
3. Edit file to resolve
4. Stage changes
5. Complete merge
```

### Task 5: Review PR
```
1. Right panel → Open PR
2. View Changes tab → see diff
3. Approve or Request Changes
4. Merge when ready
```

---

## Best Practices for Antigravity

### 1. Meaningful Commit Messages
```
✅ Good:
feat: Add payment endpoint with validation

❌ Bad:
fix stuff
update code
```

### 2. Logical Commits
```
One feature = one branch
One logical change = one commit
Don't mix features in commits
```

### 3. Regular Syncing
```
Pull regularly (before starting work)
Push regularly (after commits)
Don't let branches diverge too much
```

### 4. Clean Branch Names
```
feature/  - new features
fix/      - bug fixes
docs/     - documentation
refactor/ - code improvement
```

### 5. Code Review Process
```
1. Create PR
2. Link to issue (if applicable)
3. Describe changes
4. Request reviewers
5. Wait for approval
6. Merge with squash
7. Delete branch
```

---

## Integration with Codex CLI & Cursor

### Project Structure (All Three Tools)

```
~/my-project/
├── AGENTS.md              ← For Codex CLI
├── CLAUDE.md              ← For Cursor
├── ANTIGRAVITY.md         ← For Antigravity
├── .git/
├── src/
└── tests/
```

### Team Workflow

```
Everyone has same repository:
1. Clone with Antigravity
2. All files visible (AGENTS.md, CLAUDE.md, ANTIGRAVITY.md)
3. Each developer chooses their tool
4. Same patterns, different tools
5. Changes visible to all
```

---

## Keyboard Shortcuts (Antigravity)

| Action | Shortcut |
|--------|----------|
| Commit | Ctrl+Enter (Cmd+Enter) |
| Pull | Ctrl+Shift+I |
| Push | Ctrl+Shift+O |
| Create Branch | Ctrl+Shift+B |
| Search | Ctrl+F |
| Open Terminal | Ctrl+` |

---

## Troubleshooting

### Issue: "Permission denied" on git push

**Solution:**
1. Setup SSH key:
   ```bash
   ssh-keygen -t ed25519
   # Add to GitHub/GitLab
   ```
2. Or use HTTPS token:
   ```bash
   git remote set-url origin https://token@github.com/user/repo
   ```

### Issue: Merge conflicts

**Solution:**
1. Antigravity shows conflicts
2. Edit files to resolve
3. Stage resolved files
4. Complete merge

### Issue: Accidentally committed wrong file

**Solution:**
1. Create new commit fixing it
2. Or use `git reset --soft HEAD~1`
3. Un-stage wrong file
4. Commit again

### Issue: Need to undo changes

**Solution:**
1. Right-click commit → Revert
2. Or stash changes (WIP)
3. Or create new branch with older code

---

## Tips for Team Collaboration

### 1. Use Antigravity's PR Review
```
Integrated code review:
- Comments on changes
- Approve/request changes
- Discussions in PR
- All in Antigravity UI
```

### 2. Set Merge Rules
In GitHub/GitLab settings:
```
Require:
- Pull request review
- Status checks passed
- Branches up to date
- No conflicts
```

### 3. Use Git Hooks
```
Pre-commit hooks:
- Run linter
- Run tests
- Prevent bad commits

Post-commit hooks:
- Notifications
- CI/CD triggers
```

### 4. Document in ANTIGRAVITY.md
```
Share with team:
- Git workflow
- Branch naming
- Merge strategy
- Deployment process
```

---

## Deployment Integration

### Auto-Deploy with Webhooks

```
GitHub → Actions
GitLab → CI/CD Pipeline

Setup:
1. Define workflow file (.github/workflows/)
2. Trigger on push to main
3. Run tests
4. Deploy to production
5. Antigravity shows status
```

### Example GitHub Actions

```yaml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy
        run: |
          npm install
          npm run build
          npm run deploy
```

---

## Next Steps

1. ✅ Install Antigravity
2. ✅ Configure Git
3. ✅ Clone codex-howto
4. ✅ Setup project
5. ✅ Initialize Git repo
6. ✅ Create branches
7. ✅ Start development
8. ✅ Create PR → Merge → Deploy

---

## Resources

- **Antigravity Docs:** https://support.gitkraken.com/antigravity/
- **Git Guide:** https://git-scm.com/doc
- **This Repository:** README.md
- **Project Instructions:** ANTIGRAVITY.md (in your project)

---

**Ready to manage Git with Antigravity?** Open your project and start working! 🚀
