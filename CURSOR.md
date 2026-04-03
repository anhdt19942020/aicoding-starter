# Global Agent Instructions — Cursor IDE

**Location:** Project root `CURSOR.md` (auto-read by Cursor)
**Purpose:** Project instructions for Cursor users

These instructions extend the global patterns from [LEARNING-ROADMAP.md](./LEARNING-ROADMAP.md).

## IDE-Specific Guidelines

### Cursor Features to Use
- **Cmd+K / Ctrl+K:** Code generation (in editor)
- **Cmd+L / Ctrl+L:** Chat panel (ask questions)
- **Cmd+Shift+I / Ctrl+Shift+I:** Code search (natural language)

### When to Use Each Feature

**Code Generation (Cmd+K):**
```
"Create a React component for user login"
"Add error handling to this function"
"Refactor this to use hooks"
```

**Chat Panel (Cmd+L):**
```
"How do we handle authentication?"
"What's the pattern for API errors?"
"Why is this not working?"
```

**Code Search:**
```
"How do we create new services?"
"Where are payment-related functions?"
"Show me examples of error handling"
```

## Code Quality in Cursor

### Before Accepting Generated Code
- [ ] Check against project patterns
- [ ] Verify it matches CLAUDE.md patterns
- [ ] Review type hints
- [ ] Check error handling
- [ ] Run tests if generated

### Maintaining Consistency
- Keep CLAUDE.md updated with patterns
- Provide code examples in CLAUDE.md
- Reference CLAUDE.md in Cursor chat
- Review generated code critically

## Testing in Cursor

### Generate Tests
```
Cmd+K: "Write tests for this function"
Cursor generates test file
Review → Run → Commit
```

### Run Tests in Terminal
```
Cmd+` : Open terminal
npm test / npm run test
```

## File Organization

Files Cursor reads:
- `CLAUDE.md` — Project instructions (this file)
- `.cursorignore` — Files to ignore
- Source code (for context)

Files to exclude:
- `.env` — Credentials
- `.git/` — Large
- `node_modules/` — Dependencies

## Performance Tips

### Cursor Optimization
1. Keep CLAUDE.md under 50KB
2. Use inline comments for complex logic
3. Close unused files
4. Restart Cursor if slow

### Context Management
1. Provide specific file context
2. Reference CLAUDE.md patterns
3. Show examples when asking for code
4. Use comments to clarify intent

## Workflow Recommendations

### Small Changes
```
Cmd+K inline → Generate → Accept → Done
```

### Large Features
```
1. Cmd+L: Ask about approach
2. Break into steps
3. Cmd+K: Generate each step
4. Review & test
5. Commit
```

### Debugging
```
1. Cmd+L: Describe the issue
2. Cursor explains
3. Cmd+K: Generate fix
4. Test fix
5. Commit
```

## Integrating with Other Tools

### Cursor + Codex CLI
```
Cursor: UI/Components
Codex: Backend/Services
Both: Check CLAUDE.md + AGENTS.md
```

### Cursor + Antigravity
```
Cursor: Development
Antigravity: Git management
Commit from Cursor
Manage PR in Antigravity
```

## Project Patterns to Follow

(Add your project-specific patterns here:)
- Service/Repository/DTO structure
- React hooks patterns
- Error handling approach
- Testing strategy
- API response format

## Code Examples

(Add code examples for common patterns:)

### Example: Create Endpoint
```typescript
// Controller
@Post()
async create(@Body() dto: CreateDto) {
  return this.service.create(dto);
}

// Service
async create(dto: CreateDto) {
  // Implementation
}
```

### Example: React Component
```typescript
export function MyComponent({ prop }: Props) {
  const [state, setState] = useState();

  return <div>{/* JSX */}</div>;
}
```

## Before Committing

- [ ] All generated code reviewed
- [ ] Tests written and passing
- [ ] Pattern consistency checked
- [ ] No console errors
- [ ] Code follows CLAUDE.md

## Tips for Best Results

1. **Be specific:** "Create a Button component with Tailwind and props types"
2. **Provide context:** "Following our authentication pattern..."
3. **Reference examples:** "Like the UserService we created"
4. **Iterate:** Ask for improvements → Cmd+K → refine

---

This file should be customized for your project. Update it with:
- Your actual patterns
- Code examples
- Service structure
- Testing approach
- Any project-specific guidelines
