# Codex CLI vs Claude Code

Comparison of OpenAI Codex CLI and Anthropic Claude Code for AI-assisted development.

---

## Quick Comparison

| Feature | Codex CLI | Claude Code |
|---------|-----------|-------------|
| **Provider** | OpenAI | Anthropic |
| **Models** | GPT-4o, o3, o4-mini | Claude Haiku/Sonnet/Opus |
| **Project File** | AGENTS.md | CLAUDE.md |
| **Config** | .codex/config.toml | .claude/settings.json |
| **Session Resume** | `codex resume --last` | In-app resume |
| **Skills** | 60+ built-in | Customizable |
| **MCP Support** | Full MCP servers | Limited MCP |
| **Cost** | Pay-per-token (o3/o4) | Subscription or pay-per-token |
| **Setup Complexity** | Moderate | Lower |
| **Context Window** | Large (200K+) | Large (200K+) |
| **Reasoning** | o3: extended thinking | Claude 3.5 extended thinking |

---

## Codex CLI Strengths

### ✅ Advanced Reasoning
- **o3 Model:** Extended thinking for complex problems
- **o4 Model:** Latest frontier model (when available)
- Better for algorithmic problems, architectural decisions

### ✅ MCP Servers Integration
- Direct database access via MCP servers
- GitHub API integration
- Real-time external data fetching
- Advanced tooling support

### ✅ Session Management
- Explicit session control (`codex resume`, `codex ls`)
- Full session history preserved
- Can resume specific sessions by ID
- Session compaction for context management

### ✅ Project Autonomy
- AGENTS.md is auto-read
- No need to paste context repeatedly
- Better for long-term projects

### ✅ Cost Efficiency (for some use cases)
- o4-mini: cheaper and faster
- Good for high-volume tasks
- Pay-per-token (transparent)

---

## Claude Code Strengths

### ✅ Ease of Setup
- Integrated into IDE (VS Code)
- No separate terminal/CLI needed
- Simpler initial configuration

### ✅ Natural Conversation
- More natural dialogue style
- Better at explaining decisions
- Good for teaching/learning

### ✅ Tool Integration
- Direct file reading/writing in IDE
- Real-time preview servers
- Git integration built-in
- Slash commands for workflows

### ✅ Memory System
- Persistent memory files across sessions
- Global vs project-specific memory
- Hybrid approach for knowledge reuse

### ✅ Skills System
- Customizable reusable prompts
- Easier to create project-specific skills
- Skill chaining and composition

### ✅ Stable Pricing
- Consistent subscription (if on Claude Pro)
- Predictable costs
- Works with any Claude model

---

## When to Use Each

### Use **Codex CLI** When:
```
✅ Need extended reasoning (o3 model)
✅ Working with complex algorithms
✅ Need direct database/API access (MCP servers)
✅ Want explicit session control
✅ Multiple long-running projects
✅ Team collaboration with shared AGENTS.md
✅ Cost-sensitive at scale
```

### Use **Claude Code** When:
```
✅ Want integrated IDE experience
✅ Need file reading/writing in IDE
✅ Prefer drag-and-drop setup
✅ Want persistent memory system
✅ Working with preview servers
✅ Learning/teaching code patterns
✅ Single-focus workflow
```

### Use **Both** When:
```
✅ Complex backend (Codex) + frontend (Claude Code)
✅ Team: some prefer CLI, some prefer IDE
✅ Need both reasoning and tool integration
✅ Want flexibility across projects
✅ Leverage different model strengths
```

---

## Project File Comparison

### Claude Code: CLAUDE.md
```markdown
# Quick Reference
- Memory location
- Available skills
- Dev servers
- Common tasks
- Links to memory

Local documentation, not committed to git
```

### Codex CLI: AGENTS.md
```markdown
# Architecture & Instructions
- Project overview
- Architecture patterns
- Key domains
- Common tasks with code
- Error handling
- Run commands
- Checklist

Committed to git, shared with team
```

**Key Difference:** Claude Code uses separate memory files + CLAUDE.md, while Codex uses single AGENTS.md file.

---

## Setup Comparison

### Claude Code
```
1. Create .claude/launch.json      ← Dev servers
2. Create .claude/settings.json    ← Hooks
3. Create .claude/skills/          ← Project skills
4. Create ~/.claude/memory/        ← Global memory
5. Create CLAUDE.md                ← Quick reference
```

### Codex CLI
```
1. Create .codex/config.toml       ← Project config
2. Create ~/.codex/AGENTS.md       ← Global instructions
3. Create AGENTS.md                ← Project instructions
4. Codex auto-reads both AGENTS files
```

**Complexity:** Claude Code has more files, Codex is simpler.

---

## Cost Comparison

### Codex CLI (OpenAI Models)
```
o4-mini:  ~$0.00005 / 1K input tokens   (cheapest)
GPT-4o:   ~$0.003 / 1K input tokens
o3:       ~$0.02 / 1K input tokens      (expensive, powerful)

Example: 100K token session
- o4-mini: ~$5
- GPT-4o: ~$300
- o3: ~$2,000
```

### Claude Code
```
Claude Haiku:    ~$0.00080 / 1K input tokens
Claude Sonnet:   ~$0.003 / 1K input tokens
Claude Opus:     ~$0.015 / 1K input tokens

Subscription: Claude Pro = $20/month (unlimited use)
API: Pay-per-token
```

**Verdict:** Claude Pro subscription better for daily use. Codex o4-mini cheaper for high-volume scripting.

---

## Integration Scenarios

### Backend Development
**Best: Codex CLI**
- o3 model for architecture decisions
- Direct database access (MCP)
- Session management for long work
- AGENTS.md shared with team

### Full-Stack Development
**Best: Both**
- Codex for backend (complex, reasoning)
- Claude Code for frontend (tools, preview)
- Share AGENTS.md + CLAUDE.md
- Different workflows for each

### Team Development
**Best: Codex + Claude hybrid**
```
Backend Team (5 devs):
- Use Codex CLI
- Shared AGENTS.md in git
- MCP servers for databases
- o4-mini for speed, o3 for complex tasks

Frontend Team (3 devs):
- Use Claude Code
- Shared CLAUDE.md in git
- Preview servers for testing
- Better for component/UI work

DevOps:
- Codex CLI for infrastructure
- MCP servers for cloud APIs
- Extended thinking for architecture
```

---

## Migration Path

### From Claude Code → Codex
1. Keep CLAUDE.md (local reference)
2. Create AGENTS.md (shared with team)
3. Copy patterns from memory files
4. Switch: `codex start` instead of Claude Code
5. Resume: `codex resume --last`

### From Codex → Claude Code
1. Export session history if needed
2. Create `~/.claude/memory/` from AGENTS.md
3. Create `.claude/skills/` from your patterns
4. Create CLAUDE.md for quick reference
5. Open in VS Code: Claude Code

### Running Both
```bash
# Terminal 1: Codex CLI for backend
codex start

# Terminal 2: VS Code with Claude Code for frontend
code .
# Use Claude Code for component work
```

---

## Recommendation Matrix

```
┌─────────────────────────┬─────────────┬─────────────┐
│ Use Case                │   Codex     │  Claude     │
├─────────────────────────┼─────────────┼─────────────┤
│ Complex Algorithms      │  ⭐⭐⭐⭐⭐  │  ⭐⭐⭐⭐    │
│ API/Backend Design      │  ⭐⭐⭐⭐⭐  │  ⭐⭐⭐⭐    │
│ React/Frontend Dev      │  ⭐⭐⭐     │  ⭐⭐⭐⭐⭐  │
│ Database Operations     │  ⭐⭐⭐⭐⭐  │  ⭐⭐⭐⭐    │
│ IDE Integration         │  ⭐⭐       │  ⭐⭐⭐⭐⭐  │
│ File Management         │  ⭐⭐⭐     │  ⭐⭐⭐⭐⭐  │
│ Testing/Debugging       │  ⭐⭐⭐⭐    │  ⭐⭐⭐⭐⭐  │
│ Quick Setup             │  ⭐⭐⭐     │  ⭐⭐⭐⭐⭐  │
│ Team Collaboration      │  ⭐⭐⭐⭐⭐  │  ⭐⭐⭐⭐    │
│ Cost Efficiency         │  ⭐⭐⭐⭐    │  ⭐⭐⭐⭐    │
└─────────────────────────┴─────────────┴─────────────┘
```

---

**Bottom Line:** Codex CLI for backend/DevOps work, Claude Code for full-stack development. Best of both worlds = use both together!
