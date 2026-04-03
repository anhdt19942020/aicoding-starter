# Global Agent Instructions

**Location:** `~/.codex/AGENTS.md`
**Purpose:** Shared instructions for ALL projects

These guidelines apply across all projects. Project-specific instructions extend and override these.

## Workflow Rules

### Code Quality
- ✅ Type hints on ALL parameters and return types
- ✅ Follow existing patterns in codebase
- ✅ Write tests for new business logic
- ✅ No business logic in Controllers/Handlers
- ✅ Delegate to Services for logic
- ✅ Use dependency injection

### Architecture Patterns
- ✅ Service layer for business logic
- ✅ Repository pattern for database access
- ✅ DTO pattern for data transfer
- ✅ Enum pattern for status/type values
- ✅ Event-driven for side effects
- ✅ Middleware for cross-cutting concerns

### API Design
- ✅ Consistent response format: `{ data, meta }` for success
- ✅ Error format: `{ message, errors, statusCode }` for failures
- ✅ Correct HTTP status codes (200, 201, 400, 401, 403, 404, 422, 500)
- ✅ Validate all input at system boundaries
- ✅ Authenticate all protected routes
- ✅ Check authorization before returning resources

### Database Management
- ✅ Write `up()` AND `down()` in migrations
- ✅ Test rollback: `migration:run` → `migration:revert` → `migration:run`
- ✅ Add indexes on foreign keys and query fields
- ✅ Use eager loading to prevent N+1 queries
- ✅ Wrap multi-step operations in transactions
- ✅ No hardcoded data in migrations

### Security
- ✅ No credentials in AGENTS.md or code
- ✅ Use environment variables for secrets
- ✅ Validate and sanitize all inputs
- ✅ Use prepared statements (ORM handles this)
- ✅ Check authorization on all resource access
- ✅ Log security-relevant operations

### Testing Strategy

**Unit Tests**
- Test isolated logic (Services, Utilities)
- Mock external dependencies
- Fast execution (< 1s per test)

**Integration Tests**
- Test full workflows (API → Service → Database)
- Use real database (rollback after)
- Include happy path and error cases

**Test Coverage**
- New logic requires tests
- Aim for 80%+ critical path coverage
- Test both success and failure paths

### Git & Commits
- ✅ Meaningful commit messages (Conventional Commits)
- ✅ One logical change per commit
- ✅ Test before committing
- ✅ No large files or credentials

### Code Review Checklist
Before committing, check:
- [ ] Type hints everywhere
- [ ] Tests exist and pass
- [ ] No business logic in Controllers
- [ ] Migrations have rollback
- [ ] Database queries optimized (no N+1)
- [ ] Error handling present
- [ ] No hardcoded values or credentials
- [ ] Patterns match project conventions

## Session Management

### Resuming Sessions
```bash
codex resume --last           # Continue last session
codex resume <SESSION_ID>     # Resume specific session
codex ls                      # List recent sessions
```

### Session Context
- Codex maintains full conversation history
- Previous explanations not needed
- Architecture already understood
- Continue from exact stopping point

### When to Start Fresh
- New feature with different context
- Major refactoring
- Different domain (e.g., switching from payment to academic)
- Session too long (auto-compacted)

## Common Questions

### "How do I...?"
1. Check project AGENTS.md first
2. Look for existing similar code
3. Ask Codex for help with reference to patterns

### "Why did you...?"
1. Codex explains decisions based on patterns
2. Request clarification if unclear
3. Update AGENTS.md if you disagree with approach

### "Can we use...?"
1. Check architecture section of AGENTS.md
2. If not mentioned, discuss before implementing
3. Update AGENTS.md after decision

## Performance Tips

### Token Efficiency
- Load AGENTS.md once per session
- Reference existing patterns
- Use skills for checklists
- Avoid re-explaining context

### Session Continuity
- Resume sessions instead of starting fresh
- Codex remembers previous work
- No token waste on re-context

### Code Generation
- Request specific implementations
- Provide code examples when needed
- Ask for multiple approaches for complex decisions

## Integration Notes

### Available Skills
Codex has 60+ built-in skills. Use when needed:
- `/code-review-checklist` — Code quality
- `/testing-patterns` — Test structure
- `/database-design` — Schema design
- And many more...

### MCP Servers
External integrations available:
- GitHub API access
- MongoDB operations
- MySQL database access
- Sequential thinking (o3 model)
- See MCP_GUIDE.md for details

## Final Reminders

✅ **Codex auto-reads this file** → No need to paste
✅ **Session history is preserved** → Resume efficiently
✅ **Multiple projects supported** → Each has own AGENTS.md
✅ **Team-friendly** → Commit AGENTS.md, exclude .codex/

---

**Next:** Read project-specific AGENTS.md when switching projects.
