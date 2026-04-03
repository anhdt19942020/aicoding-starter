# Global Agent Instructions — Antigravity IDE

**Location:** Project root `ANTIGRAVITY.md` (reference guide for Antigravity users)
**Purpose:** Git workflows and team collaboration guidelines

---

## Git Workflow Strategy

### Branch Strategy (Git Flow)

```
main (production)
  ↓ merge from develop (with PR)
develop (staging)
  ↓ merge from feature (with PR)
feature/* (development)
  ↓ created from develop
  └─ feature/payment-endpoint
  └─ feature/user-auth
  └─ fix/bug-123
```

### Branch Naming Convention

```
feature/     - New features
fix/         - Bug fixes
docs/        - Documentation
refactor/    - Code improvement
chore/       - Maintenance
test/        - Tests
```

### Example Branch Names
```
feature/payment-processor
fix/authentication-bug
docs/api-documentation
refactor/database-queries
```

## Commit Strategy

### Commit Message Format
```
<type>: <subject>

<body>

<footer>
```

### Types
- `feat:` — New feature
- `fix:` — Bug fix
- `docs:` — Documentation
- `style:` — Code style (formatting)
- `refactor:` — Code refactoring
- `perf:` — Performance improvement
- `test:` — Adding/updating tests

### Examples
```
feat: Add payment processing service

fix: Resolve authentication token expiry

docs: Update API endpoints documentation

test: Add tests for payment validation
```

## Pull Request Process

### 1. Create Feature Branch
```
Feature idea
  ↓
Create feature branch from develop
  ↓
Work on feature
```

### 2. Commit Regularly
```
Write code
  ↓
Stage changes
  ↓
Commit with meaningful message
  ↓
Push to remote
```

### 3. Create Pull Request
```
Feature complete
  ↓
Push branch to remote
  ↓
Create PR (develop as base)
  ↓
Add title & description
```

### 4. Code Review
```
Team reviews PR
  ↓
Comments/suggestions
  ↓
Address feedback
  ↓
Push updates (auto-updates PR)
```

### 5. Merge
```
All reviews approved
  ↓
All checks pass
  ↓
Merge PR
  ↓
Delete branch
  ↓
Close related issues
```

## Team Collaboration

### Code Review Checklist
Before approving PR:
- [ ] Code follows patterns from AGENTS.md/CLAUDE.md
- [ ] Tests are included and passing
- [ ] No hardcoded values or credentials
- [ ] Error handling present
- [ ] Documentation updated if needed
- [ ] Commit messages are meaningful

### Review Etiquette
```
✅ "This looks good, but consider..."
✅ "Great work! One suggestion..."
❌ "This is wrong"

Always be constructive and helpful
```

### Conflict Resolution
```
If merge conflicts:
1. Pull latest develop
2. Resolve conflicts locally
3. Test thoroughly
4. Push resolved version
5. Merge PR
```

## Deployment Process

### Branching for Deployment
```
develop branch:
  → Merges auto-deploy to staging
  → Test there before moving to main

main branch:
  → Merges auto-deploy to production
  → Stable release version
```

### Pre-Deployment Checklist
- [ ] All tests passing
- [ ] Code reviewed and approved
- [ ] No console errors
- [ ] Environment variables configured
- [ ] Database migrations ready
- [ ] No breaking changes

### Deployment Steps
```
1. Create PR from develop to main
2. Code review
3. All checks pass
4. Merge to main
5. Monitor deployment
6. Verify in production
7. Close related issues
```

## Git Best Practices in Antigravity

### 1. Pull Before Starting Work
```
Antigravity → Pull (or Cmd+Shift+I)
```

### 2. Commit Often, Push Regularly
```
Every logical change = one commit
Push at end of day or frequently
```

### 3. Keep Branches Updated
```
If develop updated:
  Rebase feature branch
  Or merge develop into feature
```

### 4. Use Squash When Merging
```
Many small commits → 1 clean commit
Better history
Easier to understand
```

### 5. Delete Merged Branches
```
After merge → delete feature branch
Keeps repo clean
```

## Issue Management

### Linking Issues to PRs
```
In PR description:
Closes #123
Fixes #456
Related to #789
```

### Commit Messages with Issue Numbers
```
feat: Add payment (#123)

Adds payment processing service
Closes #123
```

## CI/CD Integration

### Automatic Checks (GitHub Actions / GitLab CI)
```
Every PR triggers:
  ✓ Linting
  ✓ Type checking
  ✓ Unit tests
  ✓ Integration tests
  ✓ Build check
```

### Merge Requirements
```
Before merging, must pass:
  ✓ All CI checks
  ✓ Code review approval
  ✓ No conflicts
  ✓ Branch protection rules
```

### Auto-Deployment
```
Push to develop:
  → CI runs tests
  → Deploy to staging
  → Health checks

Push to main:
  → CI runs tests
  → Deploy to production
  → Health checks
```

## Workflow: Antigravity + Codex + Cursor

### Complete Development Workflow

```
1. Idea/Issue Created
   └─ In GitHub/GitLab

2. Development
   ├─ Create feature branch (Antigravity)
   ├─ Code in Cursor or Codex
   └─ Commit frequently (Antigravity)

3. Testing
   ├─ Write tests (Cursor)
   ├─ Run tests locally
   └─ Ensure all pass

4. Push & Review
   ├─ Push to remote (Antigravity)
   ├─ Create PR (Antigravity)
   └─ Request review

5. Code Review
   ├─ Team reviews (Antigravity)
   ├─ Address feedback (Cursor/Codex)
   └─ Iterate

6. Merge & Deploy
   ├─ Approve & merge (Antigravity)
   ├─ Auto-deploy (CI/CD)
   └─ Verify in production
```

## Common Tasks

### Task: Create Feature Branch
```
In Antigravity:
1. Branches panel → Develop
2. Right-click → Create branch
3. Name: feature/my-feature
4. Create
```

### Task: Commit Changes
```
In Antigravity:
1. Bottom panel → Changes
2. Stage files
3. Write commit message (AI helps!)
4. Commit
5. Push (if ready)
```

### Task: Create Pull Request
```
In Antigravity:
1. Right panel → Create PR
2. Base: develop
3. Title & description
4. Create PR on GitHub/GitLab
```

### Task: Merge PR
```
After approval:
1. PR panel → Review
2. Resolve conflicts if any
3. Squash commits
4. Merge
5. Delete branch
```

## Tips for Smooth Collaboration

### 1. Communicate Changes
```
Tell team about:
- Database migrations
- Breaking changes
- New dependencies
- Deployment requirements
```

### 2. Keep PRs Focused
```
One feature per PR
Not multiple features
Easier to review
Easier to revert if needed
```

### 3. Code Review Turnaround
```
Aim for 24-hour reviews
Block team progress → notify
Review incrementally
```

### 4. Document Decisions
```
In PR description:
- Why this approach?
- Alternatives considered
- Testing done
- Known limitations
```

## Troubleshooting

### Issue: Merge Conflicts
```
Solution:
1. Antigravity shows conflicts
2. Resolve locally
3. Stage resolved files
4. Complete merge
```

### Issue: Accidentally Committed
```
Solution:
1. Right-click commit
2. Revert
3. Creates new commit undoing changes
```

### Issue: Branch Diverged
```
Solution:
1. Rebase on develop
2. Or merge develop into feature
3. Test thoroughly
4. Force push if needed
```

### Issue: Can't Push
```
Solution:
1. Pull latest first
2. Resolve conflicts
3. Commit merge
4. Push again
```

## Branch Protection Rules

### Recommended Settings (in GitHub/GitLab)

```
For develop branch:
  ✓ Require PR review
  ✓ Require status checks passed
  ✓ Require branches up to date
  ✗ Allow force push

For main branch:
  ✓ Require PR review (2+ reviewers)
  ✓ Require status checks passed
  ✓ Require branches up to date
  ✓ Require admin approval
  ✗ Allow force push
```

---

This file should be customized for your team. Update with:
- Your specific Git workflow
- Team review process
- Deployment strategy
- CI/CD pipeline details
- Branch protection rules
- Any team-specific policies
