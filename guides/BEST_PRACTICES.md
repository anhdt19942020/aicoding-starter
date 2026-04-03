# Codex CLI Best Practices

Production-tested patterns for effective AI-assisted development with Codex CLI.

---

## Session Management

### ✅ DO: Resume for Continuity
```bash
# When continuing work
codex resume --last

# When returning to project after days
codex resume --last

# When context needs refreshing
codex start  # New session if too much context
```

### ❌ DON'T: Lose Session Context
```bash
# DON'T close terminal without noting session
# DO: Run `codex ls` to see recent sessions
codex ls

# DON'T: Start new session for every task
# DO: Keep related work in same session
codex resume --last
```

### Session Organization
```bash
# List all sessions
codex ls

# Find session from specific date
codex ls --filter="2026-04-03"

# Resume with specific ID (if needed)
codex resume <SESSION_ID>

# Each resumed session maintains full history
```

---

## AGENTS.md Best Practices

### ✅ DO: Keep it Comprehensive
```markdown
# Good AGENTS.md
- Project overview (type, path, port)
- Architecture (modules, patterns, layers)
- Key domains (features, services)
- Common tasks with CODE EXAMPLES
- Error handling strategy
- Run commands
- Before committing checklist
```

### ✅ DO: Include Code Examples
```markdown
## Create New Endpoint
1. Create DTO with validation
2. Create Controller method
3. Create Service method
4. Add route to module
5. Run tests

## Example:

```typescript
// 1. DTO
export class CreatePaymentDto {
  @IsNumber()
  amount: number;
}

// 2. Controller
@Post()
create(@Body() dto: CreatePaymentDto) {
  return this.paymentService.create(dto);
}
```
```

**Why:** Codex uses these examples to understand your patterns.

### ✅ DO: Explain Architecture Decisions
```markdown
## Why Service Layer?
- Reusable business logic
- Testable without HTTP context
- Can be called from Controllers, Jobs, Events

## Why DTOs?
- Type-safe validation
- Serialization control
- API contract clarity
```

### ✅ DO: Update AGENTS.md as Architecture Evolves
```bash
# When adding new patterns
# When changing database structure
# When establishing new conventions

git add AGENTS.md
git commit -m "docs: Update AGENTS.md with new payment pattern"
```

### ❌ DON'T: Hardcode Sensitive Data
```markdown
❌ DON'T:
PAYOO_API_KEY=your-key-here
MYSQL_PASSWORD=password123

✅ DO:
# Use environment variables (.env)
# Document which env vars are needed
# Exclude .env from git
```

### ❌ DON'T: Make AGENTS.md Too Long
```
Size limit: 65KB (project_doc_max_bytes)

If too long:
- Move detailed guides to separate files
- Link to them in AGENTS.md
- Keep AGENTS.md as overview + quick reference
```

---

## Workflow Optimization

### Session Flow
```
Day 1 - Morning:
├─ codex start
├─ Read AGENTS.md (auto-loaded)
├─ Understand architecture
└─ "Create new payment endpoint"
   └─ Codex generates code based on patterns

Day 1 - Afternoon:
├─ codex resume --last
├─ "Review and test the endpoint"
└─ Continue from exact point

Day 2 - Morning:
├─ codex resume --last
├─ Context fully loaded (no re-explanation)
└─ "Move to next feature"
```

### Batch Related Tasks
```bash
# ✅ GOOD: Keep related work in one session
codex resume --last
# "Create payment service, test it, create API endpoint"
# All in same context, builds on each other

# ❌ AVOID: Jumping between unrelated domains
codex start  # Only if switching to completely different domain
# "Now work on authentication"
```

### Context Awareness
```
Each request should reference previous work:

❌ "Create a user service"
✅ "Create a user service following the payment service pattern"

❌ "Make an API endpoint"
✅ "Create GET /users/:id endpoint matching our RestController pattern"

❌ "Write tests"
✅ "Write unit tests for UserService mocking repositories"
```

---

## Code Review & Quality

### Before Committing
```markdown
## Codex-Assisted Review

1. Ask: "Review this code for quality"
   - Codex checks against AGENTS.md patterns
   - Suggests improvements
   - Validates architecture

2. Ask: "Create tests for this feature"
   - Codex generates tests based on patterns
   - Follows testing style in AGENTS.md

3. Ask: "Check for common issues"
   - N+1 queries
   - Missing error handling
   - Security issues
```

### Using Skills
```bash
# Codex has 60+ built-in skills
# Reference in your requests:

"Review this code using code-review-checklist skill"
"Create tests following testing-patterns skill"
"Check database design using database-design skill"
```

### Code Consistency
```
Keep consistent patterns by:
1. Documenting patterns in AGENTS.md
2. Referencing patterns in requests
3. Asking Codex to follow patterns
4. Reviewing generated code for consistency
```

---

## Team Collaboration

### Sharing AGENTS.md
```bash
# In your project repo
git add AGENTS.md
git commit -m "docs: Project instructions for Codex"
git push

# Team members
git pull
codex start  # Auto-reads AGENTS.md
# Same context as rest of team!
```

### Consistent Context
```
All team members see:
✅ Same AGENTS.md
✅ Same architecture
✅ Same patterns
✅ Same conventions

Result: Consistent code quality across team
```

### Handling AGENTS.md Updates
```bash
# When architecture changes
1. Update AGENTS.md
2. Commit to git
3. Team pulls latest
4. Next codex session loads new AGENTS.md

# All new work follows updated patterns
```

---

## Performance & Efficiency

### Token Efficiency
```
Session 1:
- Load AGENTS.md: ~2,000 tokens
- Your requests: ~500 tokens
- Codex response: ~1,000 tokens
Total: ~3,500 tokens per session

Continuing in same session:
- Your request: ~500 tokens
- Codex response: ~1,000 tokens
Total: ~1,500 tokens (43% less!)

Benefit of resuming: Save 67% tokens
```

### Model Selection
```
For different tasks:

Simple tasks (bugs, refactoring):
→ Use o4-mini (cheapest, fast)

Complex decisions (architecture, design):
→ Use o3 (extended thinking)

Set in ~/.codex/config.toml:
[model]
default = "o4-mini"
# or "o3" or "gpt-4o"
```

### Context Compaction
```
Codex auto-compacts long sessions:
- Summarizes early conversation
- Keeps recent context detailed
- Preserves token efficiency

If needed, manually:
codex resume --fresh  # Start new session
```

---

## Common Mistakes & Solutions

### ❌ Mistake: Starting New Session Every Time
```
Problem:
- Context not preserved
- Have to re-explain architecture
- Wasted tokens

Solution:
codex resume --last  # Keep context
```

### ❌ Mistake: AGENTS.md Too Vague
```
Problem:
"Use good patterns"
"Follow best practices"

Solution:
"Use Service layer for business logic"
"Dispatch events for side effects"
"Use DTOs for API validation"
```

### ❌ Mistake: Not Updating AGENTS.md
```
Problem:
- New team members confused
- Architecture outdated
- Inconsistent code

Solution:
- Update AGENTS.md when patterns change
- Review with team
- Commit to git
```

### ❌ Mistake: Mixing Model Capabilities
```
Problem:
Using o4-mini for complex architecture

Solution:
For complex decisions: use o3 (extended thinking)
For simple tasks: use o4-mini (cheaper)
```

---

## Advanced Techniques

### Multi-Step Development
```
Session with multiple related tasks:

1. "Create PaymentEntity with relationships"
   ↓
2. "Generate migration for PaymentEntity"
   ↓
3. "Create PaymentService with create() method"
   ↓
4. "Create PaymentController with POST endpoint"
   ↓
5. "Write unit tests for PaymentService"
   ↓
6. "Create integration tests for payment endpoint"

All in same session - full context preserved!
```

### Incremental Refinement
```
Session with iterative improvement:

1. "Create basic payment flow"
   (Codex generates initial implementation)

2. "Add error handling"
   (Codex enhances previous code)

3. "Add validation"
   (Codex validates inputs)

4. "Add logging"
   (Codex logs operations)

5. "Optimize queries"
   (Codex fixes N+1 queries)

Each step builds on previous - no re-context needed
```

### Parallel Concerns
```
Single session covering multiple concerns:

1. Service implementation + Tests
   "Create UserService and its unit tests"

2. API endpoint + Validation
   "Create UserController endpoint with validation"

3. Database + Migrations
   "Create User entity and migration"

All connected, consistent context
```

---

## Checklist: Session Management

```
Before Starting New Session:
□ Did I use `codex resume --last`? (Keep context)
□ Is this related to previous work? (Use same session)
□ Does AGENTS.md need updating? (Keep it fresh)

During Session:
□ Am I asking specific questions? (With patterns referenced)
□ Is code following AGENTS.md patterns? (Ask to verify)
□ Are tests being written? (For critical features)

Before Committing:
□ Has Codex reviewed code? (Against patterns)
□ Do tests pass? (Run npm test / php artisan test)
□ Is AGENTS.md still accurate? (Update if needed)

Before Pushing:
□ Has code review happened? (With quality checklist)
□ Is AGENTS.md committed? (If changed)
□ Are sensitive files excluded? (.git/info/exclude)
```

---

**Master these practices → Maximize productivity with Codex CLI! 🚀**
