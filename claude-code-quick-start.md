# Claude Code Quick Start Cheat Sheet

**Version**: v1.0.124+ | **Updated**: November 2025 | **Print this for reference!**

---

## 🚀 Installation

```bash
# Install
npm install -g @anthropic-ai/claude-code

# Start
claude

# Choose: Claude Max, Pro, or API key
```

---

## ⚡ Your First 5 Commands

```bash
# 1. Check status
/status

# 2. Get help
/help

# 3. Clear context between features
/clear

# 4. Roll back mistakes
/rewind

# 5. View available commands
# (Tab completion works!)
```

---

## 📝 Essential Workflow

### The Golden Pattern

```bash
# 1. Start on feature branch
git checkout -b feature/my-feature

# 2. Start Claude
claude

# 3. Ask for a plan first
> Create a plan to implement user authentication

# 4. Review plan, then implement
> That plan looks good, let's implement it

# 5. Create checkpoints
> Create a checkpoint "auth complete"

# 6. Test continuously
> Run all tests

# 7. Commit often
git add .
git commit -m "Implement auth"

# 8. Clear between features
/clear
```

---

## 🎯 Context Management

| Context | Action |
|---------|--------|
| 0-30% | ✅ Work freely |
| 30-50% | ⚠️ Plan carefully |
| 50-80% | 🔶 Watch closely |
| 80%+ | 🚨 `/compact` or `/clear` |

```bash
# Check often!
/status
```

---

## 🛠️ Essential Commands

### Navigation
- `Tab` - Autocomplete files/commands
- `Ctrl+C` - Interrupt Claude
- `Ctrl+R` - View full transcript
- `Ctrl+B` - Run command in background

### Context
- `/status` - View context usage
- `/context` - Debug context details
- `/clear` - Wipe conversation
- `/compact` - Smart summarization
- `/rewind` - Roll back changes

### Project
- `/add-dir` - Add working directory
- `/permissions` - Manage tool access
- `/memory` - Edit memory files

### Models
- `/model` - Switch models (Opus 4 / Sonnet 4)
- `/cost` - View usage costs

---

## 📁 File Structure

```
your-project/
├── .claude/
│   ├── CLAUDE.md              ← START HERE!
│   ├── settings.json
│   ├── commands/
│   │   ├── component.md
│   │   └── api.md
│   └── agents/
│       ├── test-agent.md
│       └── security-agent.md
├── .mcp.json                  ← MCP config
└── .gitignore                 ← Add .env
```

---

## 📄 Create CLAUDE.md

**This is the #1 most important file!**

```markdown
# Project: [Name]

## Tech Stack
- Framework: Next.js 14
- Language: TypeScript
- Database: PostgreSQL
- Styling: Tailwind CSS

## Code Standards
- Use functional components
- Props interface above component
- Max 150 lines per file
- Tests required for all features

## Commands
- `npm run dev` - Start server
- `npm test` - Run tests
```

---

## 🎨 Good Prompts

### ❌ Bad
```
Add auth
```

### ✅ Good
```
I need to add JWT authentication to my Express app.

Requirements:
1. Login and signup endpoints
2. Password hashing with bcrypt
3. JWT token generation
4. Middleware to protect routes
5. Store users in PostgreSQL

Please create a plan first, then implement.
```

---

## 🔧 Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Enter` | Submit |
| `Ctrl+C` | Interrupt |
| `Ctrl+R` | Toggle transcript |
| `Ctrl+O` | Full transcript |
| `Ctrl+B` | Background command |
| `Ctrl+_` | Undo input |
| `Tab` | Autocomplete |
| `Shift+Tab` | Toggle auto-accept |
| `Esc` | Cancel dialog |

---

## 🐛 Emergency Recovery

```bash
# Something went wrong?

# Option 1: Rewind in Claude
/rewind
# Select checkpoint

# Option 2: Git reset
git reset --hard HEAD

# Option 3: Specific file
git checkout HEAD -- file.ts
```

---

## 🎓 Day 1 Checklist

- [ ] Install Claude Code
- [ ] Authenticate (Max/Pro/API)
- [ ] Navigate to your project
- [ ] Create `.claude/CLAUDE.md`
- [ ] Run first request: "Create a hello world endpoint"
- [ ] Check `/status` frequently
- [ ] Create a feature branch
- [ ] Practice `/rewind`

---

## 💡 Pro Tips

### 1. Always Plan Complex Features
```bash
> Think through how we should implement caching
# Wait for plan
> That looks good, implement it
```

### 2. Use Feature Branches
```bash
git checkout -b feature/X  # ALWAYS
# Never work on main
```

### 3. Checkpoint Critical Moments
```bash
> Create checkpoint "before risky refactor"
# Try something
# Didn't work?
/rewind
```

### 4. Clear Between Features
```bash
> Feature X is complete!
/clear
> Now let's build feature Y
```

### 5. Monitor Context
```bash
# Add this to your workflow:
# Check every 10-15 minutes
/status
```

---

## 🔗 Quick Links

- **Docs**: https://docs.claude.com/claude-code
- **Changelog**: https://claudelog.com/claude-code-changelog/
- **Support**: https://support.claude.com
- **Community**: r/ClaudeCode

---

## 📊 What to Expect

### Week 1
- Learning curve: Moderate
- Productivity: Same as normal
- Best practices: Basic

### Week 2
- Learning curve: Comfortable
- Productivity: +20%
- Best practices: Intermediate

### Week 4
- Learning curve: Proficient
- Productivity: +30-50%
- Best practices: Advanced

---

## ⚠️ Common Mistakes

1. **Not creating CLAUDE.md** ← Most common!
2. Working directly on main branch
3. Ignoring context warnings
4. Not planning complex features
5. Forgetting to `/clear` between features
6. Not reviewing diffs before accepting
7. Treating Claude like Google (be specific!)

---

## 🎯 Success Formula

```
Great CLAUDE.md
    +
Context Management
    +
Planning First
    +
Feature Branches
    +
Consistent Practice
    =
30-50% Productivity Gain
```

---

## 📞 Getting Help

```bash
# Built-in diagnostics
/doctor

# Check what Claude knows
> What do you know about this project?

# Ask for clarification
> Can you explain that approach in more detail?
```

---

**Print this, pin it near your desk, refer to it often!**

*Happy coding! 🚀*
