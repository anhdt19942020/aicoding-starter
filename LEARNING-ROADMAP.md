# Learning Roadmap — Codex CLI Mastery

Progressive learning path from setup to production mastery (2-4 hours total).

---

## 📚 Learning Path

### Phase 1: Foundation (30 minutes)
Master the basics before diving into projects.

**1. Installation** [INSTALLATION.md](./INSTALLATION.md)
- Install Codex CLI
- Setup API key
- Verify installation
- ✅ **Check:** `codex --version` works

**2. Core Concepts** [README.md](./README.md)
- Understand AGENTS.md
- Understand .codex/config.toml
- Understand session management
- ✅ **Check:** Can explain what AGENTS.md is

**3. Getting Started** [GETTING_STARTED.md](./GETTING_STARTED.md)
- Complete step-by-step setup
- Copy first project template
- Customize AGENTS.md
- ✅ **Check:** `codex start` launches successfully

---

### Phase 2: Hands-On Practice (60 minutes)
Build confidence with real development.

**4. Choose & Setup Project** [templates/](./templates/)
Pick one:
- Laravel API → `templates/laravel-project/`
- NestJS API → `templates/nestjs-project/`
- Next.js App → `templates/nextjs-project/`

Activities:
- Copy template to your project
- Customize AGENTS.md
- Setup git with .git/info/exclude
- ✅ **Check:** Project ready, `codex start` loads context

**5. Session Management**
- Start: `codex start`
- Resume: `codex resume --last`
- List: `codex ls`
- Continue developing

Activities:
- Create new endpoint/component
- Request code review from Codex
- Write tests
- Commit changes
- ✅ **Check:** Can resume sessions with full context

**6. Code Quality**
- Ask Codex to review code
- Check against AGENTS.md patterns
- Request test generation
- Debug issues with Codex help

Activities:
- "Review this code"
- "Create tests for this"
- "Why is this failing?"
- ✅ **Check:** Code passes review, tests pass

---

### Phase 3: Advanced Usage (45 minutes)
Optimize workflow and collaborate with team.

**7. Best Practices** [guides/BEST_PRACTICES.md](./guides/BEST_PRACTICES.md)
- Session optimization
- Token efficiency
- Code quality patterns
- Error handling

Activities:
- Understand hybrid memory (global + project)
- Learn when to start fresh vs resume
- Understand context preservation
- ✅ **Check:** Can explain session optimization

**8. Team Collaboration**
- Commit AGENTS.md to git
- Share project instructions
- Team reads same AGENTS.md
- Consistent patterns across team

Activities:
- Add team members
- Clone project
- `codex start` (same context as team)
- Verify consistency
- ✅ **Check:** Team has same context, consistent code

**9. Production Deployment**
- Prepare for production
- Security checklist
- Environment variables
- Deployment strategy

Activities:
- Update AGENTS.md for production
- Review security patterns
- Setup CI/CD integration
- Test production workflow
- ✅ **Check:** Ready for production deployment

---

### Phase 4: Mastery (30-45 minutes)
Compare tools, understand tradeoffs, optimize choices.

**10. Codex vs Claude Code** [guides/CODEX_vs_CLAUDE.md](./guides/CODEX_vs_CLAUDE.md)
- Understand both tools
- Know when to use each
- Can use both together

Activities:
- Read comparison guide
- Understand cost/benefit
- Identify use cases for Codex
- Understand when to use Claude Code
- ✅ **Check:** Can explain when to use Codex vs Claude

**11. MCP Integration** (Advanced)
- Database access via MCP servers
- External API integration
- Real-time data fetching

Activities:
- Setup MCP server (if applicable)
- Use for database queries
- Extend Codex capabilities
- ✅ **Check:** Can integrate MCP servers

**12. Troubleshooting & Optimization**
- Common issues and solutions
- Performance optimization
- Cost optimization
- Session management tuning

Activities:
- Debug session issues
- Optimize token usage
- Understand pricing
- Archive old sessions
- ✅ **Check:** Can solve common problems

---

## ⏱️ Time Allocation

```
Total: 2-4 hours (depending on experience level)

Phase 1 (Foundation):        30 min
  ├─ Installation           10 min
  ├─ Core Concepts          10 min
  └─ Getting Started        10 min

Phase 2 (Practice):         60 min
  ├─ Setup Project          20 min
  ├─ Session Management     20 min
  └─ Code Quality           20 min

Phase 3 (Advanced):         45 min
  ├─ Best Practices         15 min
  ├─ Team Collaboration     15 min
  └─ Production Setup       15 min

Phase 4 (Mastery):          30-45 min
  ├─ Codex vs Claude        15 min
  ├─ MCP Integration        10 min
  └─ Optimization           5-20 min
```

---

## 📖 Documentation Map

```
START HERE
    ↓
README.md ..................... Overview
    ↓
INSTALLATION.md ............... Install & setup
    ↓
GETTING_STARTED.md ............ Step-by-step guide
    ↓
Choose Template ............... Pick tech stack
    ↓
AGENTS.md ..................... Project instructions
    ↓
BEST_PRACTICES.md ............. Production patterns
    ↓
CODEX_vs_CLAUDE.md ............ When to use what
    ↓
TROUBLESHOOTING ............... Fix problems
```

---

## ✅ Mastery Checklist

### Foundation Level ✓
- [ ] Codex CLI installed and working
- [ ] API key configured
- [ ] Understand AGENTS.md purpose
- [ ] Can start new session

### Intermediate Level ✓
- [ ] Can resume sessions with full context
- [ ] Can customize AGENTS.md for project
- [ ] Can request code review from Codex
- [ ] Can write tests with Codex help
- [ ] Commit code following patterns

### Advanced Level ✓
- [ ] Session management optimized
- [ ] Team shares same AGENTS.md
- [ ] Production patterns applied
- [ ] Error handling complete
- [ ] Tests have good coverage

### Expert Level ✓
- [ ] Know when to use Codex vs Claude
- [ ] Token efficiency optimized
- [ ] MCP servers integrated
- [ ] Team workflows streamlined
- [ ] Can solve complex problems autonomously

---

## 🎯 Self-Assessment Quiz

### After Phase 1
```
Q1: What is AGENTS.md?
A: Project instructions auto-read by Codex

Q2: Where should .env be excluded?
A: .git/info/exclude

Q3: How do you resume work?
A: codex resume --last
```

### After Phase 2
```
Q4: How do sessions preserve context?
A: Full conversation history stored locally

Q5: What should code review check?
A: Patterns match AGENTS.md, tests exist, error handling

Q6: Where should business logic go?
A: Services, not Controllers
```

### After Phase 3
```
Q7: How do teams collaborate?
A: Share AGENTS.md in git, everyone has same context

Q8: When should you start fresh session?
A: When switching to completely different domain

Q9: What's the benefit of AGENTS.md?
A: No re-explaining architecture, consistent patterns
```

### After Phase 4
```
Q10: When is Codex better than Claude Code?
A: Complex reasoning (o3), direct DB access (MCP)

Q11: How to optimize tokens?
A: Resume sessions, use o4-mini for simple tasks

Q12: What's session compaction?
A: Summarizes old context to preserve tokens
```

---

## 📚 Additional Resources

### Official Documentation
- [OpenAI Codex Docs](https://developers.openai.com/codex/)
- [MCP Specification](https://spec.modelcontextprotocol.io/)

### Similar Projects
- [Claude-Howto](https://github.com/luongnv89/claude-howto) — Claude Code guide
- [OpenAI Cookbook](https://github.com/openai/openai-cookbook) — Examples

### Community
- GitHub Discussions
- Stack Overflow `[openai-codex]`
- OpenAI Community Forum

---

## 🚀 Next Steps

### After Completing Roadmap

1. **Start Your Project**
   ```bash
   cd ~/your-project
   codex start
   ```

2. **Reference BEST_PRACTICES.md**
   - Follow production patterns
   - Optimize session usage
   - Write quality code

3. **Share with Team**
   - Commit AGENTS.md
   - Train team on patterns
   - Build consistent culture

4. **Keep Learning**
   - Read guides as needed
   - Update AGENTS.md when patterns evolve
   - Experiment with new features

---

## 💡 Pro Tips

1. **Create a bookmark** to this learning roadmap
2. **Revisit phases** when learning new tech stacks
3. **Customize templates** for your workflow
4. **Share findings** with your team
5. **Update AGENTS.md** as architecture evolves

---

**Ready to master Codex CLI?** Start with [INSTALLATION.md](./INSTALLATION.md) → [README.md](./README.md) → [GETTING_STARTED.md](./GETTING_STARTED.md) 🚀

Estimated time to mastery: **2-4 hours**
