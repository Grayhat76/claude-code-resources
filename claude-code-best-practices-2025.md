# Claude Code Best Practices Guide (2025)
**The Complete Guide to Mastering AI-Assisted Development**

*Last Updated: November 1, 2025 | Version 2.1 | For Claude Code v1.0.124+*

---

## ⚡ TL;DR - Start Here (5 Minutes)

**The 5 Things That Actually Matter:**

1. **Create `.claude/CLAUDE.md`** - This file is 80% of success. [Jump to template](#4-claudemd---your-projects-north-star)
2. **Watch Your Context** - Run `/status` often. Clear at 80%. [Context guide](#5-context-management-strategies)
3. **Use Feature Branches** - Always. `git checkout -b feature/X`. [Git workflow](#7-git-integration--safety)
4. **Plan Before Coding** - Ask for plans on anything complex. [Planning guide](#6-planning-before-coding)
5. **Learn 5 Commands** - `/status`, `/clear`, `/rewind`, `/help`, `/permissions`

**Reality Check:**
- Week 1: Same productivity (learning curve)
- Week 2: +10-20% productivity
- Week 4: +20-30% with good habits
- Costs: $200/month (Max plan) + time investment

**When NOT to Use Claude Code:**
- Quick 1-line fixes (overhead not worth it)
- Learning a new codebase (read it yourself first)
- Highly sensitive security code (review extra carefully)
- When you need to understand every detail (AI can obscure learning)

[Skip to 30-minute setup →](#installation-quick-path)

---

## Table of Contents

### **Getting Started**
1. [What is Claude Code?](#1-what-is-claude-code)
2. [Installation & Setup](#2-installation--setup)
3. [Your First Session](#3-your-first-session)

### **Core Foundation**
4. [CLAUDE.md - Your Project's North Star](#4-claudemd---your-projects-north-star)
5. [Context Management Strategies](#5-context-management-strategies)
6. [Planning Before Coding](#6-planning-before-coding)

### **Essential Workflows**
7. [Git Integration & Safety](#7-git-integration--safety)
8. [The /rewind & Checkpoints System](#8-the-rewind--checkpoints-system)
9. [Custom Slash Commands](#9-custom-slash-commands)
10. [Custom Agents & Sub-agents](#10-custom-agents--sub-agents)

### **Advanced Features**
11. [Skills System (October 2025)](#11-skills-system-october-2025)
12. [Plugin System (October 2025)](#12-plugin-system-october-2025)
13. [MCP Servers](#13-mcp-servers)
14. [Testing Strategies](#14-testing-strategies)

### **IDE & Environment**
15. [VS Code & JetBrains Integration](#15-vs-code--jetbrains-integration)
16. [Output Styles & Educational Modes](#16-output-styles--educational-modes)
17. [Background Commands & Parallel Execution](#17-background-commands--parallel-execution)

### **Reference**
18. [Complete Command Reference](#18-complete-command-reference)
19. [Troubleshooting Guide](#19-troubleshooting-guide)
20. [Real-World Success Patterns](#20-real-world-success-patterns)
21. [Learning Roadmap](#21-learning-roadmap)

---

## 1. What is Claude Code?

### The Basics

**Claude Code** is an AI-powered coding assistant that runs in your terminal and integrates with your favorite IDEs. Think of it as a pair programmer that:
- Understands your entire codebase
- Makes surgical edits to your files
- Runs commands and tests
- Maintains context across long sessions
- Follows your project's conventions

### Key Capabilities (November 2025)

Claude Code is now generally available with Claude Opus 4 and Claude Sonnet 4 models. Opus 4 is the world's best coding model, achieving 72.5% on SWE-bench and 43.2% on Terminal-bench, with sustained performance on tasks requiring thousands of steps over several hours. Sonnet 4 scores 72.7% on SWE-bench and excels at autonomous multi-feature app development.

**Latest Features (as of v1.0.124):**
- **Claude 4 Models**: Opus 4 and Sonnet 4 with extended thinking
- **VS Code & JetBrains Extensions**: Native IDE integration (beta)
- **GitHub Integration**: Claude Code can respond to PR comments and fix CI errors
- **Checkpoints & /rewind**: Save progress and roll back instantly
- **Skills System**: Extensible knowledge modules
- **Plugin Marketplace**: Community-built extensions
- **Custom Agents**: Specialized sub-agents for specific tasks
- **Background Commands**: Run dev servers while Claude works
- **Output Styles**: Educational modes for learning
- **MCP Servers**: Extensible tool system

### Who Should Use Claude Code?

✅ **Perfect for:**
- Developers building new features
- Teams refactoring large codebases
- Solo developers learning new frameworks
- DevOps automating infrastructure
- Data scientists building pipelines

⚠️ **Learning curve:**
- Beginners: 1-2 weeks to proficiency
- Intermediate: 3-5 days to productivity
- Advanced: Immediate value, mastery in 1 week

### How Claude Code Compares

**vs GitHub Copilot:**

| Feature | Claude Code | GitHub Copilot |
|---------|-------------|----------------|
| Context Window | 1M tokens (entire codebase) | Limited (~20 files) |
| Agent Capabilities | Full terminal agent | Inline suggestions |
| Planning | Creates detailed plans | No planning |
| Cost | $20-200/mo | $10-20/mo |
| Learning Curve | Higher | Lower |
| Best For | Complex features, refactoring | Quick completions |

**vs Cursor:**

| Feature | Claude Code | Cursor |
|---------|-------------|--------|
| Context Window | 1M tokens | Large (~100 files) |
| Interface | Terminal + IDE extension | IDE replacement |
| Agent Capabilities | Full agent with tools | AI-enhanced editor |
| Cost | $20-200/mo | $20/mo |
| Flexibility | Any editor + terminal | Must use Cursor |
| Best For | Complex agent tasks | Integrated coding |

**vs Plain Claude API:**

| Feature | Claude Code | Claude API |
|---------|-------------|------------|
| Tools | File editing, bash, search | You build everything |
| Context Management | Built-in | Manual |
| Setup | Ready to use | Requires coding |
| Cost | Subscription | Pay per token |
| Best For | Development | Custom applications |

**The Truth:**
- Use **Copilot** for quick inline completions
- Use **Cursor** if you want an all-in-one IDE
- Use **Claude Code** for complex multi-file features and refactoring
- Use **Claude API** if you're building custom tools

Many devs use Claude Code + Copilot together.

---

## 2. Installation & Setup

### Installation Quick Path

**30-Minute Setup for Immediate Productivity**

```bash
# Step 1: Install (2 min)
npm install -g @anthropic-ai/claude-code

# Step 2: Start and authenticate (3 min)
claude
# Choose: Claude Max ($200/mo) or Pro ($20/mo)

# Step 3: Navigate to your project (1 min)
cd your-project

# Step 4: Create basic CLAUDE.md (10 min)
mkdir -p .claude
cat > .claude/CLAUDE.md << 'EOF'
# Project: [Your Project Name]

## Tech Stack
- [Your framework/language]
- [Your database]

## Important Patterns
- [Key convention 1]
- [Key convention 2]

## Commands
- `npm run dev` - Start server
- `npm test` - Run tests
EOF

# Step 5: First task (5 min)
claude
> Add a health check endpoint to my app

# You're productive! Now explore features as needed.
```

**Detailed Installation**

```bash
# Install Claude Code
npm install -g @anthropic-ai/claude-code

# Or via Homebrew (Mac)
brew install claude-code

# Verify installation
claude --version
```

### First-Time Setup

```bash
# Start Claude Code (will prompt for authentication)
claude

# Choose authentication method:
# 1. Claude Max subscription (recommended)
# 2. Claude Pro subscription
# 3. API key
# 4. AWS Bedrock
# 5. Google Cloud Vertex AI
```

### System Requirements

- **OS**: macOS, Linux, Windows (via WSL or native Git for Windows)
- **Node.js**: v18+ (v20+ recommended)
- **Terminal**: Any modern terminal (iTerm2, Warp, Windows Terminal, Ghostty)
- **Subscription**: Claude Pro, Max, Team, or Enterprise
- **Disk Space**: ~500MB for installation

### Windows Users

Claude Code now supports native Windows with Git for Windows required, introduced in v1.0.51

```bash
# Option 1: Native Windows (v1.0.51+)
# Install Git for Windows first
# Then: npm install -g @anthropic-ai/claude-code

# Option 2: WSL (recommended for best experience)
wsl --install
# Then install in WSL environment
```

---

## 3. Your First Session

### 5-Minute Quick Start

**Step 1: Navigate to your project**
```bash
cd ~/projects/my-app
```

**Step 2: Start Claude Code**
```bash
claude
```

**Step 3: Your first request**
```
> Add a health check endpoint to my Express app
```

**What happens next:**
1. Claude analyzes your codebase
2. Proposes changes with file diffs
3. You review and approve (or reject)
4. Changes are applied to your files
5. Claude can run tests to verify

### Understanding the Interface

```
┌─────────────────────────────────────────────────────┐
│ Context: 45,234 / 1,000,000 tokens (4.5%)         │ ← Status line
│ Cost: $0.23 | Active: 3m 42s                      │
└─────────────────────────────────────────────────────┘

Claude is thinking... ▓▒░                             ← Spinner

[Read] src/app.js (234 lines)                         ← Tool usage
[StrReplace] src/app.js:45-52                         
[Bash] npm test                                       

> Your prompt here█                                   ← Input area
```

**Key keyboard shortcuts:**
- `Enter`: Submit prompt
- `Ctrl+C`: Interrupt Claude
- `Ctrl+R`: View full transcript
- `Ctrl+O`: Toggle transcript view
- `Tab`: Autocomplete files/commands
- `Shift+Tab`: Toggle auto-accept for file edits
- `Ctrl+B`: Run background command

### Your First Real Task

Let's build a practical example:

```
> I need to add user authentication to my app. Here's what I need:
1. JWT-based authentication
2. Login and signup endpoints
3. Middleware to protect routes
4. Store users in the existing PostgreSQL database

Please create a plan first before making changes.
```

**What makes this a good prompt:**
- ✅ Clear objective
- ✅ Specific requirements
- ✅ Mentions existing context (PostgreSQL)
- ✅ Asks for a plan first

**What happens:**
1. Claude enters **plan mode** (shows thinking)
2. Presents a structured implementation plan
3. You approve or refine the plan
4. Claude implements step-by-step
5. Runs tests and validates changes

---

## 4. CLAUDE.md - Your Project's North Star

### Why CLAUDE.md Matters

**The Universal Truth:** Every successful Claude Code user emphasizes CLAUDE.md. It's the single most important file in your project for AI collaboration.

Think of CLAUDE.md as:
- Your project's README for AI
- A persistent memory across all conversations
- Documentation that enforces conventions
- A contract between you and Claude

### The Perfect CLAUDE.md Template

CLAUDE.md files can import other files by adding @path/to/file.md to load additional files on launch (introduced in v0.2.107)

```markdown
# Project: [Your App Name]

## Project Overview
Brief description of what this project does and its main purpose.

## Tech Stack
- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript 5.3
- **Database**: PostgreSQL 15 with Prisma ORM
- **Styling**: Tailwind CSS
- **Testing**: Jest + React Testing Library
- **Deployment**: Vercel

## Project Structure
\`\`\`
src/
├── app/              # Next.js app directory
├── components/       # React components
│   ├── ui/          # Shadcn/ui components
│   └── features/    # Feature-specific components
├── lib/             # Utility functions
├── hooks/           # Custom React hooks
└── types/           # TypeScript type definitions
\`\`\`

## Code Standards

### TypeScript
- Use strict mode
- Prefer interfaces over types for objects
- Always export types used in props
- Use const assertions for literal types

### React
- Functional components only (no class components)
- Use hooks for state management
- Components under 150 lines - extract if larger
- Props interface directly above component

### File Naming
- Components: PascalCase.tsx
- Hooks: camelCase.ts with "use" prefix
- Utils: camelCase.ts
- Types: PascalCase.types.ts

### Testing
- Unit tests for all utility functions
- Integration tests for API routes
- Test file naming: ComponentName.test.tsx

## Development Workflow

### Before Making Changes
1. Read existing code to understand patterns
2. Check for similar implementations
3. Propose plan before implementing
4. Run tests after changes

### Commands Available
- `npm run dev` - Start development server
- `npm test` - Run tests
- `npm run build` - Production build
- `npx prisma migrate dev` - Run database migrations

## Important Notes
- Never commit .env files
- Always use environment variables for secrets
- Keep component logic separate from UI
- Maintain accessibility (WCAG 2.1 AA)

## Current Focus
Working on: User authentication system
Next up: Dashboard analytics

## Import Additional Context
@.claude/database-schema.md
@.claude/api-conventions.md
```

### Creating Your CLAUDE.md

**Step 1: Generate initial version**
```bash
claude "Create a CLAUDE.md file for this project"
```

**Step 2: Refine it**
```bash
claude "Add our TypeScript conventions to CLAUDE.md"
```

**Step 3: Keep it updated**
```bash
# After major changes
> Update CLAUDE.md to reflect the new API structure
```

### Advanced CLAUDE.md Patterns

**1. Modular Documentation**
```markdown
# Main CLAUDE.md
@.claude/architecture.md
@.claude/api-design.md
@.claude/database-schema.md
@.claude/deployment.md
```

**2. Team-Specific Conventions**
```markdown
## Code Review Standards
- All PRs need 2 approvals
- Tests must pass CI
- No console.logs in production code
- Performance budget: <3s LCP

## Team Preferences
- Sarah prefers functional programming patterns
- Mike handles all database migrations
- Use linear tickets for all features
```

**3. Context for Complex Domains**
```markdown
## Domain Knowledge
### Healthcare Compliance
- All PHI must be encrypted at rest
- Audit logs required for data access
- HIPAA compliance checklist: [link]

### Financial Calculations
- Use Decimal.js for currency (never float)
- Always round to 2 decimal places
- Tax calculations in utils/tax.ts
```

---

## 5. Context Management Strategies

### The Core Problem

Auto-compact warning threshold increased from 60% to 80% in v1.0.51, with customizable cleanup period via settings.cleanupPeriodDays introduced in v0.2.117

**Context Management = Quality Control**

Claude has a 1M token context window, but filling it carelessly degrades output quality. The best developers treat context like a precious resource.

### The Golden Rules

**Rule #1: Never Exceed 80% Context**

Check frequently:
```bash
/status
```

Output shows:
```
Context: 756,234 / 1,000,000 tokens (75.6%)
Cost: $2.14 | Active: 23m 18s
Models: Sonnet 4
```

**Rule #2: Clear Context Between Features**

```bash
# Complete authentication feature
> Implementation looks good!

# Clear before starting next feature
/clear

# Start fresh
> Now let's build the payment processing system
```

**Rule #3: Use /compact for Mid-Task Context Reset**

```bash
# Context is filling up mid-feature
/compact Preserve authentication implementation decisions

# Claude summarizes and compresses context
# You keep working on the same feature
```

### Context Management Commands

Claude Code now supports /context command (v1.0.86) for detailed token breakdown across MCP tools, Custom Agents, and memory files to optimize performance

| Command | Purpose | When to Use | What It Preserves |
|---------|---------|-------------|-------------------|
| `/status` | View context usage | Check frequently | Nothing (view only) |
| `/context` | Debug context details | Optimize performance | Nothing (diagnostic) |
| `/clear` | Complete wipe | Between features | CLAUDE.md only |
| `/compact` | Smart summarization | Mid-feature | Recent decisions + CLAUDE.md |
| `/resume` | Return to old chat | Continue later | Full conversation |
| `/rewind` | Roll back changes | Undo mistakes | Previous state |

### The 4-Phase Context Reset Pattern

**Phase 1: Research (0-30% context)**
```bash
> Analyze the current authentication system
> Show me all files related to user sessions
> What security vulnerabilities do you see?
```

**Phase 2: Plan (30-50% context)**
```bash
> Create a detailed plan to migrate from cookies to JWT
> What are the breaking changes?
> How should we handle existing sessions?
```

**Clear context after approval:**
```bash
/clear
```

**Phase 3: Implement (0-80% context)**
```bash
> Implement the JWT authentication plan we discussed
# (CLAUDE.md preserves the plan)
```

**Phase 4: Validate (clear if needed)**
```bash
> Run all authentication tests
> Check for security issues
> Create migration documentation
```

### Advanced Context Techniques

**1. Strategic @-mentions**

```bash
# ❌ Bad: Loads entire file
> Fix the bug in @src/utils/api.ts

# ✅ Good: Precise context
> Fix the authentication bug in the fetchUser function
# Then @-mention only when Claude needs to see the file
```

**2. External Memory**

Keep notes outside Claude:
```bash
# In your editor
## Sprint Progress
- ✅ User authentication
- ✅ Password reset
- 🔄 Email verification (current)
- ⏳ OAuth integration

## Important Decisions
- Using Supabase Auth
- JWT tokens expire in 7 days
- Refresh tokens stored in httpOnly cookies
```

**3. Sub-agents for Isolation**

Custom subagents for specialized tasks released in v1.0.60, with @-mention support added in v1.0.62

```bash
# Main conversation stays clean
> @test-agent Run the full test suite and report failures

# Sub-agent handles it in separate context
```

---

## 6. Planning Before Coding

### The #1 Productivity Multiplier

**Research finding:** Developers who ask Claude to create plans first see **50-70% less rework** compared to those who start coding immediately.

### When to Use Plan Mode

✅ **Always plan for:**
- New features (>1 hour of work)
- Refactoring existing code
- Database schema changes
- API design
- Architecture decisions

⚠️ **Skip planning for:**
- Obvious bug fixes
- Tiny tweaks (<10 lines)
- Style/formatting changes
- Documentation updates

### Triggering Plan Mode

**Method 1: Explicit request**
```bash
> Create a plan to add real-time notifications using WebSockets
```

**Method 2: Thinking keywords**
```bash
> Think through how we should implement caching
```

Thinking mode can be triggered with keywords, with enhanced triggering reliability in v0.2.102, and can be temporarily disabled with /t in your prompt (v1.0.115)

**Thinking triggers:**
- "think"
- "think harder"  
- "ultrathink"
- "plan"
- "design"
- "architect"

**Method 3: /model settings**
```bash
# Run Opus only for planning, Sonnet for execution
/model
> Select "Opus Plan Mode" option
```

### The Perfect Planning Prompt

**❌ Bad:** "Add notifications"

**✅ Good:**
```
I need to add real-time notifications to my app. Before implementing,
please create a detailed plan that covers:

1. Architecture decision: WebSockets vs SSE vs polling
2. Technology choice and rationale
3. Database schema changes needed
4. Backend implementation steps
5. Frontend integration approach
6. Testing strategy
7. Deployment considerations
8. Potential gotchas or challenges

Consider that we're using:
- Next.js 14 (App Router)
- Postgres database
- Currently deployed on Vercel

Take your time thinking through this.
```

### What Good Plans Look Like

Claude will provide:
```markdown
# Real-Time Notifications Implementation Plan

## 1. Architecture Decision
**Recommendation: Server-Sent Events (SSE)**

Rationale:
- Vercel supports SSE in Edge Functions
- Simpler than WebSockets for uni-directional updates
- Better for our use case (server→client notifications)
- Fallback polling for older browsers

## 2. Database Schema

```sql
CREATE TABLE notifications (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id),
  type VARCHAR(50) NOT NULL,
  title TEXT NOT NULL,
  message TEXT,
  read BOOLEAN DEFAULT false,
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_notifications_user_unread 
  ON notifications(user_id, read, created_at);
```

## 3. Implementation Steps

### Backend (5 files to modify/create)
1. Create `/app/api/notifications/stream/route.ts`
   - SSE endpoint for real-time stream
2. Modify `lib/notifications.ts`
   - Add notification creation helper
3. Create `lib/notification-service.ts`
   - Pub/sub system for broadcasting
...

[Detailed step-by-step implementation]

## 4. Testing Approach
- Unit tests for notification creation
- Integration tests for SSE endpoint
- Load testing (1000 concurrent users)
...

## 5. Deployment Checklist
- [ ] Test on Vercel preview deployment
- [ ] Monitor Edge Function duration
- [ ] Set up error tracking for SSE failures
- [ ] Document for team
```

### Iterating on Plans

```bash
# Review the plan
> The SSE approach makes sense, but I'm worried about scaling.
> Can you revise to use Redis Pub/Sub instead?

# Claude revises the plan
# You approve when ready
> This looks perfect, let's implement it
```

### Plan Mode with Extended Thinking

Both Claude Opus 4 and Sonnet 4 support extended thinking with tool use in beta, allowing Claude to alternate between reasoning and using tools like web search to improve responses

**For complex architectural decisions:**
```bash
> [Extended thinking enabled]
> Think deeply about our microservices architecture.
> Should we continue with the current approach or migrate to
> a modular monolith? Consider: team size (5 devs), 
> deployment complexity, debugging difficulty, and our
> roadmap for the next 2 years.
```

Claude will:
1. Think through trade-offs deeply
2. Use web search for current best practices
3. Provide a nuanced recommendation
4. Show all reasoning steps

---

## 7. Critical Thinking: When Claude Code Gets It Wrong

### TL;DR
**Claude Code is a tool, not a magic wand. It makes mistakes. Here's how to catch them.**

- Always review AI-generated code
- Test edge cases yourself
- Security review everything
- Question over-complex solutions
- Verify dependencies are current

### Common Failure Modes

**Claude Code is genuinely bad at:**

1. **Security-Critical Code**
   ```typescript
   // Claude might suggest:
   const hash = crypto.createHash('md5').update(password).digest('hex');
   
   // Problem: MD5 is not secure for passwords
   // You should catch: Use bcrypt/scrypt/Argon2
   ```

2. **Performance Without Context**
   ```typescript
   // Claude might suggest loading everything:
   const allUsers = await db.users.findMany();
   const activeUsers = allUsers.filter(u => u.isActive);
   
   // Problem: Loads 1M+ users into memory
   // Better: Filter in database
   ```

3. **Outdated Patterns**
   - May suggest deprecated dependencies
   - May use old React patterns (class components)
   - May not know about recent library updates
   - **Always verify versions and APIs**

4. **Over-Engineering Simple Problems**
   ```typescript
   // You asked: "Add a logging function"
   // Claude creates: Abstract factory pattern with strategy injector
   // You needed: A simple console.log wrapper
   ```

### Red Flags to Watch For

**🚨 Stop and Review If You See:**

```typescript
// Using eval() or Function()
eval(userInput) // DANGER

// Regex from hell
const regex = /^(?:(?:(?:(?:(?:(?:[01]?\d|2[0-3]):)?(?:[0-5]?\d):)?(?:[0-5]?\d))$/
// If you can't explain it, don't use it

// Any crypto that looks simple
const encrypted = btoa(secret); // This is just base64, not encryption!

// Deprecated APIs
request.get() // npm 'request' is deprecated

// Suspiciously complex types
type ComplexType<T extends Record<string, unknown>> = 
  T extends infer U ? U extends Record<string, infer V> ? V : never : never;
// Can this be simpler?
```

### The Review Checklist

Before accepting ANY Claude-generated code:

1. **Does it match our patterns?**
   - Check against CLAUDE.md
   - Compare with existing code
   - Ask: "Would our team write it this way?"

2. **Is it secure?**
   - No eval, exec, or code generation
   - No hardcoded secrets
   - Proper input validation
   - Use @security-agent for critical code

3. **Is it testable?**
   - Can you write tests for this?
   - Are there too many dependencies?
   - Is it too coupled?

4. **Is it necessary?**
   - Could this be simpler?
   - Are we solving the right problem?
   - Is this premature optimization?

5. **Does it work?**
   - Run the tests
   - Test edge cases manually
   - Try to break it

### Case Studies: When Things Went Wrong

**Case 1: The Infinite Refactor**

```
User: "Improve code quality in this file"

Claude: [Rewrites entire 300-line module]

Problem: Changed working code unnecessarily
Broke existing integrations
Took 2 days to debug

Lesson: Be specific about WHAT to improve
Ask for a plan first
Keep changes incremental
```

**Case 2: The Security Hole**

```
User: "Add dynamic configuration loading"

Claude: [Suggests eval() for flexibility]

Problem: Remote code execution vulnerability
Would have failed security audit
Could expose entire system

Lesson: Always security review suggestions
Never trust AI for security-critical code
Use @security-agent
```

**Case 3: The Dependency Hell**

```
User: "Add GraphQL support"

Claude: [Installs 40 dependencies]

Problem: Dependency tree exploded
Conflicting peer dependencies
Build size increased 300%

Lesson: Review package.json changes
Question large dependency additions
Consider lighter alternatives
```

### When NOT to Use Claude Code

**Skip Claude Code for:**

- **Quick 1-liners**: `git checkout -b feature/X` - just type it
- **Syntax lookups**: "What's the syntax for..." - use docs, it's faster
- **Learning fundamentals**: If you're learning, code it yourself first
- **Ultra-sensitive code**: Payment processing, crypto - review extra carefully
- **Simple copy-paste**: Moving code around - your IDE is faster
- **Quick debugging**: Console.log debugging - faster to do manually

**Use Claude Code for:**

- New features (>30 min of work)
- Boilerplate generation
- Test writing
- Refactoring
- Documentation
- Complex algorithms you need explained

### Cost Reality Check

**Monthly Costs (Reality):**

| Usage Level | Subscription | API Usage | Total/Month |
|-------------|--------------|-----------|-------------|
| Light (1-2h/day) | $20 (Pro) | ~$30 | ~$50 |
| Medium (4-6h/day) | $200 (Max) | ~$100 | ~$300 |
| Heavy (8+h/day) | $200 (Max) | ~$200 | ~$400 |

**Team of 5 developers:**
- All Max: $1,000/month (subscriptions)
- API usage: $500-1,000/month
- **Total: $1,500-2,000/month**

**Is it worth it?**
- If 20% productivity gain saves 8 hours/dev/week
- 5 devs × 8 hours × $100/hour = $4,000/week saved
- Cost: $2,000/month ≈ $500/week
- **ROI: 8:1 if you actually get 20% gain**

**But:**
- Week 1-2: Productivity actually dips (learning)
- Realistic steady-state: 15-25% gain, not 50%
- Requires discipline and good habits
- Not every task benefits equally

### Debugging Claude Code Issues

**Claude produced bad code - recovery steps:**

```bash
# Step 1: Stop and assess
# Don't compound the problem

# Step 2: Quick rollback if obviously wrong
/rewind
# or
git checkout -- file.ts

# Step 3: If partially good, surgical fix
# Review the diff carefully
# Keep what works, fix what doesn't

# Step 4: Learn what went wrong
# Update CLAUDE.md with the pattern to avoid
# Add to project conventions
```

**When to start over vs iterate:**

```
Start Over If:
- Fundamental approach is wrong
- More broken than working
- Faster to rewrite than fix

Iterate If:
- Core logic is sound
- Just needs refinement
- Most of it works
```

---

## 8. Git Integration & Safety

### The Cardinal Rule

**Never commit directly to main/master. Always use feature branches.**

Claude Code makes hundreds of edits quickly. Git branches are your safety net.

### The Recommended Git Workflow

**Step 1: Start with a clean branch**
```bash
# Before starting Claude
git checkout -b feature/user-authentication
git push -u origin feature/user-authentication
```

**Step 2: Use Claude normally**
```bash
claude
> Implement JWT authentication system
```

**Step 3: Review changes frequently**
```bash
# In another terminal (or background)
git diff

# Or use your IDE's git UI
```

**Step 4: Commit incrementally**
```bash
# Don't wait for Claude to finish everything
git add src/auth/
git commit -m "Add JWT token generation"

git add src/middleware/
git commit -m "Add authentication middleware"
```

**Step 5: Create PR for review**
```bash
git push
# Create PR through GitHub/GitLab UI
```

### Git Worktrees for Parallel Work

**Advanced pattern for power users:**

```bash
# Setup
git worktree add ../myapp-feature feature/new-feature
git worktree add ../myapp-bugfix bugfix/critical-fix

# In different terminal windows
cd ../myapp-feature
claude "Implement new feature"

cd ../myapp-bugfix  
claude "Fix the critical bug"

# Both work in parallel without conflict
```

**Benefits:**
- Work on multiple features simultaneously
- Test branches side-by-side
- No context switching
- Easy comparison

### GitHub Integration (Beta)

Claude Code on GitHub is now in beta, allowing you to tag Claude Code on PRs to respond to reviewer feedback, fix CI errors, or modify code by running /install-github-app from within Claude Code

```bash
# Install GitHub app
/install-github-app

# Claude can now:
# - Respond to PR review comments
# - Fix CI/CD failures  
# - Make requested changes
# - Update based on feedback
```

**Usage on GitHub:**
```markdown
<!-- In a PR comment -->
@claude-code Please address the reviewer's concerns about
error handling and add more comprehensive tests
```

### Emergency Recovery

**If Claude makes unwanted changes:**

```bash
# Option 1: Git reset
git reset --hard HEAD

# Option 2: Rewind in Claude Code
/rewind
# Select the checkpoint before the bad changes

# Option 3: Specific file reset
git checkout HEAD -- src/problematic-file.ts
```

---

## 8. The /rewind & Checkpoints System

Checkpoints are one of the most requested features, allowing Claude Code to save progress and roll back instantly to a previous state, with a refreshed terminal interface introduced alongside the feature

### What Are Checkpoints?

**Checkpoints = Time Travel for Your Code**

Claude Code automatically creates checkpoints:
- Before major changes
- After completing sub-tasks
- At natural break points
- When you manually request them

### Using /rewind

**Basic usage:**
```bash
/rewind
```

**What you'll see:**
```
Available Checkpoints:

[1] 3 minutes ago - Before refactoring auth middleware
    Files changed: 3 | Lines added: 127 | Lines removed: 89
    
[2] 15 minutes ago - Completed JWT token generation  
    Files changed: 2 | Lines added: 234 | Lines removed: 12
    
[3] 28 minutes ago - Initial auth implementation plan
    Files changed: 0 | Lines added: 0 | Lines removed: 0
    
[4] 45 minutes ago - Added user model to database
    Files changed: 4 | Lines added: 156 | Lines removed: 23

Select checkpoint to restore (1-4): _
```

**Select a checkpoint:**
```bash
> 2  # Restores to "Completed JWT token generation"
```

### Manual Checkpoints

**Create checkpoints at critical moments:**
```bash
> Create a checkpoint named "Auth system complete before testing"
```

**Or inline:**
```bash
> Implement the payment processing. Create a checkpoint first.
```

### Rewind vs Git Reset

| Feature | /rewind | git reset |
|---------|---------|-----------|
| Speed | Instant | Fast |
| Granularity | Very fine | Commit-based |
| Conversation | Preserved | Lost |
| Context | Maintained | Separate |
| Scope | Project files | Git-tracked files |
| Best for | Rapid iteration | Formal changes |

**Use Both:**
```bash
# Rewind to test an approach
/rewind
> Try the alternative implementation

# Not working? Rewind again
/rewind

# When you find the right approach
git add .
git commit -m "Implement feature correctly"
```

### Advanced Checkpoint Patterns

**Pattern 1: Checkpoint-Test-Revert**
```bash
# Save current state
> Create checkpoint "before risky refactor"

# Try something experimental
> Refactor the entire authentication system to use Supabase

# Test it
> Run all tests

# If tests fail, revert
/rewind
# Select "before risky refactor"
```

**Pattern 2: A/B Comparison**
```bash
# Implementation A
> Implement caching using Redis

# Save it
> Create checkpoint "Redis implementation"

# Rewind to try alternative
/rewind

# Implementation B  
> Implement caching using in-memory solution

# Compare both approaches
# Choose the winner, rewind to it if needed
```

---

## 9. Custom Slash Commands

Custom slash commands released in v0.2.31, with markdown files in .claude/commands/ directories appearing as custom slash commands, and subdirectory namespacing restored in v1.0.45 (e.g., .claude/frontend/component.md becomes /frontend:component)

### What Are Slash Commands?

**Slash commands = Reusable prompts**

Instead of typing the same instructions repeatedly, save them as commands:
```bash
/component-create  # Your custom command
/api-endpoint      # Another custom command
/bug-fix          # Yet another
```

### Creating Custom Commands

**Step 1: Create .claude/commands/ directory**
```bash
mkdir -p .claude/commands
```

**Step 2: Create command files**

**File: `.claude/commands/component.md`**
```markdown
---
allowed-tools: [Read, StrReplace, Write]
argument-hint: component name
---

# React Component Template

Create a new React component named {{arg}} following our project conventions:

## Requirements
1. TypeScript with explicit prop types
2. Functional component with hooks
3. Styled with Tailwind CSS
4. Accessible (ARIA labels, keyboard nav)
5. Include Storybook story
6. Include unit tests

## File Structure
- Component: src/components/{{arg}}/{{arg}}.tsx
- Story: src/components/{{arg}}/{{arg}}.stories.tsx  
- Test: src/components/{{arg}}/{{arg}}.test.tsx
- Types: src/components/{{arg}}/{{arg}}.types.ts

## Template
Use our standard component template from src/components/_template/

Please create all files and implement a basic version.
```

**Step 3: Use your command**
```bash
> /component UserProfileCard
```

### Practical Command Examples

**1. API Endpoint Creator**

**File: `.claude/commands/api.md`**
```markdown
---
allowed-tools: [Read, StrReplace, Write, Bash]
---

# API Endpoint Generator

Create a new API endpoint with:
- Express route handler
- Input validation using Zod
- Error handling
- OpenAPI documentation
- Integration tests
- Rate limiting

Path: src/routes/{{arg}}.ts
```

**2. Database Migration**

**File: `.claude/commands/migration.md`**
```markdown
---
allowed-tools: [Read, Write, Bash]
---

# Database Migration Generator

Create a Prisma migration for: {{arg}}

Steps:
1. Modify schema.prisma
2. Generate migration: `npx prisma migrate dev --name {{arg}}`
3. Update seed data if needed
4. Create rollback plan
5. Test migration in development
```

**3. Bug Fix Protocol**

**File: `.claude/commands/bugfix.md`**
```markdown
---
allowed-tools: [Read, StrReplace, Grep, Bash]
---

# Bug Fix Protocol

Issue: {{arg}}

Process:
1. Reproduce the bug
2. Write failing test
3. Find root cause
4. Implement fix
5. Verify test passes
6. Check for similar issues
7. Update documentation if needed
```

### Organizing Commands with Subdirectories

```bash
.claude/
├── commands/
│   ├── frontend/
│   │   ├── component.md      # /frontend:component
│   │   ├── page.md          # /frontend:page
│   │   └── hook.md          # /frontend:hook
│   ├── backend/
│   │   ├── endpoint.md      # /backend:endpoint
│   │   ├── service.md       # /backend:service
│   │   └── migration.md     # /backend:migration
│   └── testing/
│       ├── unit.md          # /testing:unit
│       └── e2e.md           # /testing:e2e
```

Usage:
```bash
> /frontend:component LoginForm
> /backend:endpoint users/profile
> /testing:e2e checkout-flow
```

### Command Best Practices

**1. Include argument hints**
```markdown
---
argument-hint: endpoint name (e.g., users/profile)
---
```

**2. Specify allowed tools**
```markdown
---
allowed-tools: [Read, StrReplace, Write]
---
```

**3. Add examples**
```markdown
## Example Usage
/component-create UserAvatar
/component-create ProductCard variant=horizontal
```

**4. Reference project conventions**
```markdown
Follow conventions in CLAUDE.md, especially:
- File naming: PascalCase.tsx
- Export pattern: default export for components
- Props interface directly above component
```

---

## 11. Custom Agents & Sub-agents

### TL;DR
**Sub-agents = Specialized helpers that work in isolated context**

- Use for repetitive specialized tasks (testing, security, code review)
- Keeps main conversation clean
- Start with test-agent and code-reviewer
- Don't over-complicate with too many agents

### What Are Sub-agents?

Custom subagents for specialized tasks were released in v1.0.60, with @-mention support added in v1.0.62

**Sub-agents are specialized AI assistants** that work alongside your main Claude Code session.

| Feature | Main Claude | Sub-agent |
|---------|------------|-----------|
| Context Window | Shared | Isolated |
| Purpose | General development | Specific expertise |
| Tool Access | All tools | Restricted by design |
| Lifespan | Entire session | Task-specific |

### When to Use Sub-agents

**✅ USE Sub-agents For:**
- Code reviews (focus on quality)
- Security audits (think like attacker)
- Running tests (dedicated context)
- Documentation (consistent style)

**❌ DON'T Use Sub-agents For:**
- Every single task (over-engineering)
- Simple one-off requests
- When main Claude can do it easily

**Reality check:** Most developers use 2-4 agents max. Start with test-agent and code-reviewer.

### Essential Agents (Copy These)

We provide ready-to-use agents in `/agents/` directory:

**Core Set (Start Here):**
- **test-agent.md** - Runs tests, reports failures
- **code-reviewer.md** - Reviews code quality
- **security-agent.md** - Security audits

**Additional (Add As Needed):**
- docs-agent.md - Documentation
- performance-agent.md - Performance analysis
- refactor-agent.md - Code refactoring
- database-agent.md - Database work

### Quick Setup

```bash
# 1. Create agents directory
mkdir -p .claude/agents

# 2. Copy essential agents (from /agents/ directory)
cp agents/test-agent.md .claude/agents/
cp agents/code-reviewer.md .claude/agents/
cp agents/security-agent.md .claude/agents/

# 3. Use them
claude
> @test-agent Run all tests
> @code-reviewer Review my changes
```

### Creating Custom Agents

**File: `.claude/agents/my-agent.md`**

```markdown
---
name: My Agent
model: sonnet
allowed-tools: [Read, Bash]
description: Does something specific
---

# My Agent

You are a specialist in [domain].

## Your Job
1. [Specific task 1]
2. [Specific task 2]

## How to Report
- [Format guideline]
- [What to include]

## Limitations
- [What you can't do]
- [When to escalate]
```

**Model selection:**
- `sonnet` - Default, cost-effective
- `opus` - Only for critical/complex analysis

**Tool restrictions:**
- Limit tools to what agent needs
- Read-only agents: `[Read, Grep]`
- Test agents: `[Read, Bash, Grep, Write]`
- Never give all tools unless necessary

### Using Sub-agents Effectively

**Pattern 1: Parallel Work**
```bash
# Start test watcher
> @test-agent Watch tests in background

# Continue main work
> Implement user authentication
```

**Pattern 2: Specialized Review**
```bash
# After implementing feature
> @security-agent Audit the auth system
> @code-reviewer Review for code quality
```

**Pattern 3: Pipeline**
```bash
# Implement
> Add password reset feature

# Test
> @test-agent Test password reset

# Security
> @security-agent Check password reset security

# Document
> @docs-agent Document password reset flow
```

### Common Mistakes

**❌ Don't:**
- Create an agent for every tiny task
- Give agents too many tools
- Expect agents to share context with each other
- Use agents for simple one-line tasks

**✅ Do:**
- Start with 2-3 essential agents
- Restrict tools appropriately
- Use agents for repetitive specialized work
- Review agent output, don't blindly trust

### Agent vs Command vs Main Claude

| Use Case | Tool | Why |
|----------|------|-----|
| Generate React component | Command | Template-based, quick |
| Run comprehensive tests | Agent | Specialized analysis |
| Add simple endpoint | Main Claude | Straightforward task |
| Security audit | Agent | Focused expertise needed |
| Fix typo | Main Claude | Trivial, don't overcomplicate |

**Rule of thumb:** If you do it >10 times and it needs expertise, make an agent. If it's a template, make a command. If it's unique, use main Claude.

### Example Agent Files

See the `/agents/` directory for complete, production-ready agents:
- [test-agent.md](./agents/test-agent.md) - Test execution and analysis
- [code-reviewer.md](./agents/code-reviewer.md) - Code review
- [security-agent.md](./agents/security-agent.md) - Security audits

**Copy these into `.claude/agents/` in your project and customize as needed.**

---

## 12. Skills System (October 2025)

Skills released in v1.0.81 in August 2025, with project-level skills loading fixed in v1.0.4 for project scope settings

### What Are Skills?

**Skills = Installable knowledge modules**

Skills are packages that give Claude specialized knowledge:
- Programming language expertise (Python, Rust, Go)
- Framework knowledge (React Native, Django, Rails)
- Domain expertise (Machine Learning, Blockchain, DevOps)
- Tool proficiency (Docker, Kubernetes, Terraform)

**Think of skills as:**
- College courses for Claude
- Specialized training modules  
- Expertise add-ons

### Installing Skills

**Browse available skills:**
```bash
/skills browse
```

**Install a skill:**
```bash
/skills install python-advanced
/skills install react-native  
/skills install aws-devops
```

**View installed skills:**
```bash
/skills list
```

**Activate for session:**
```bash
/skills activate python-advanced
```

### Available Skill Categories

**Programming Languages:**
- `python-advanced` - Advanced Python patterns, asyncio, decorators
- `rust-systems` - Systems programming with Rust
- `go-concurrency` - Go concurrency patterns
- `typescript-advanced` - Advanced TypeScript types

**Frameworks:**
- `react-native` - React Native mobile development
- `django-advanced` - Django best practices
- `rails-patterns` - Ruby on Rails conventions
- `flutter-widgets` - Flutter UI development

**DevOps & Infrastructure:**
- `aws-devops` - AWS services and infrastructure
- `kubernetes-ops` - K8s deployment and management
- `docker-advanced` - Container optimization
- `terraform-iac` - Infrastructure as Code

**Domain Expertise:**
- `ml-engineering` - Machine Learning engineering
- `blockchain-solidity` - Smart contract development
- `data-engineering` - Data pipelines and ETL
- `security-audit` - Security best practices

### Creating Custom Skills

**Structure:**
```bash
.claude/skills/
└── my-custom-skill/
    ├── skill.json           # Metadata
    ├── README.md           # Documentation
    ├── knowledge.md        # Core knowledge
    ├── patterns.md         # Code patterns
    └── examples/           # Code examples
        ├── example1.ts
        └── example2.ts
```

**File: skill.json**
```json
{
  "name": "company-api-patterns",
  "version": "1.0.0",
  "description": "Our company's API development patterns",
  "author": "Engineering Team",
  "tags": ["api", "backend", "conventions"],
  "activationTriggers": [
    "api",
    "endpoint",
    "route"
  ]
}
```

**File: knowledge.md**
```markdown
# Company API Patterns

## Authentication
All API endpoints use JWT bearer tokens:
```typescript
Authorization: Bearer ${token}
```

## Response Format
Standard response envelope:
```typescript
{
  success: boolean
  data?: T
  error?: {
    code: string
    message: string
    details?: unknown
  }
  meta: {
    timestamp: string
    requestId: string
  }
}
```

## Error Codes
- `AUTH_001`: Invalid token
- `AUTH_002`: Expired token
- `VAL_001`: Validation error
- `SYS_001`: Internal server error

[... more patterns ...]
```

### Using Skills Effectively

**Automatic Activation:**
Skills auto-activate based on keywords:
```bash
# Triggers python-advanced skill
> Help me implement an async context manager in Python

# Triggers aws-devops skill
> Deploy this using AWS Lambda and API Gateway

# Triggers react-native skill
> Create a custom React Native component
```

**Manual Activation:**
```bash
# Activate specific skill
/skills activate ml-engineering

# Now Claude has ML expertise
> Implement a neural network for image classification
```

**Multiple Skills:**
```bash
/skills activate python-advanced ml-engineering aws-devops

# Now Claude knows Python + ML + AWS
> Build an ML inference API and deploy to AWS Lambda
```

### Skill Best Practices

**1. Install relevant skills once**
```bash
# In project root
/skills install react-native
/skills install typescript-advanced
/skills install jest-testing

# They'll auto-activate when relevant
```

**2. Create company-specific skills**
```bash
# Document your patterns as a skill
.claude/skills/company-conventions/
```

**3. Share skills with team**
```bash
# Commit skills to git
git add .claude/skills/
git commit -m "Add company API patterns skill"
```

**4. Version control skills**
```json
{
  "name": "company-patterns",
  "version": "2.1.0",
  "changelog": [
    "v2.1.0: Added GraphQL patterns",
    "v2.0.0: Breaking: New auth flow",
    "v1.0.0: Initial release"
  ]
}
```

---

## 12. Plugin System (October 2025)

Plugin System Released in v1.0.71 with /plugin install, /plugin enable/disable, /plugin marketplace commands for plugin management

### What Are Plugins?

**Plugins = Functional extensions for Claude Code**

While skills add *knowledge*, plugins add *capabilities*:
- New tools (linters, formatters, analyzers)
- Integrations (Jira, Linear, Slack)
- Custom workflows
- IDE enhancements
- Team utilities

### Plugin Marketplace

**Browse plugins:**
```bash
/plugin marketplace
```

**Categories:**
- **Development Tools**: Linters, formatters, generators
- **Integrations**: Project management, communication
- **Testing**: Test generators, coverage tools
- **Security**: Vulnerability scanners, secret detection
- **Productivity**: Time tracking, analytics
- **Team**: Onboarding helpers, documentation

### Installing Plugins

**From marketplace:**
```bash
/plugin install eslint-assistant
/plugin install jira-integration
/plugin install test-generator
```

**From GitHub:**
```bash
/plugin install https://github.com/user/claude-plugin.git
```

**From local:**
```bash
/plugin install ./local-plugin/
```

### Managing Plugins

**List installed:**
```bash
/plugin list
```

**Enable/disable:**
```bash
/plugin enable eslint-assistant
/plugin disable jira-integration
```

**Update:**
```bash
/plugin update eslint-assistant
/plugin update --all
```

**Remove:**
```bash
/plugin remove eslint-assistant
```

### Popular Plugins

**1. eslint-assistant**
```bash
/plugin install eslint-assistant

# Usage
> @eslint Fix all linting errors in src/
```

**2. test-generator**
```bash
/plugin install test-generator

# Usage  
> @testgen Generate tests for src/auth/jwt.ts
```

**3. jira-integration**
```bash
/plugin install jira-integration

# Configuration
/plugin config jira-integration
> Enter Jira URL: https://company.atlassian.net
> Enter API token: [token]

# Usage
> Create a Jira ticket for this bug
> @jira Update ticket ENG-123 with current progress
```

**4. pr-reviewer**
```bash
/plugin install pr-reviewer

# Usage
> @pr-review Review the current changes
```

**5. performance-analyzer**
```bash
/plugin install performance-analyzer

# Usage
> @perf Analyze bundle size and suggest optimizations
```

### Creating Custom Plugins

**Plugin structure:**
```bash
my-plugin/
├── package.json
├── index.js
├── tools/
│   ├── my-tool.js
│   └── another-tool.js
└── README.md
```

**File: package.json**
```json
{
  "name": "claude-plugin-custom",
  "version": "1.0.0",
  "claudePlugin": {
    "version": "1.0",
    "tools": ["tools/my-tool.js"],
    "commands": ["commands/my-command.md"],
    "agents": ["agents/my-agent.md"]
  }
}
```

**File: tools/my-tool.js**
```javascript
module.exports = {
  name: 'custom_tool',
  description: 'Does something useful',
  parameters: {
    type: 'object',
    properties: {
      input: { type: 'string' }
    }
  },
  
  async execute(params) {
    // Your tool logic
    return {
      success: true,
      output: 'Result here'
    }
  }
}
```

### Plugin Security

**⚠️ Security Considerations:**

1. **Review before installing**
   - Check source code on GitHub
   - Read permissions required
   - Verify author reputation

2. **Limit permissions**
   ```bash
   # Plugins request permissions
   > Plugin 'xyz' requests:
   > - Read files
   > - Run bash commands  
   > - Access environment variables
   > 
   > Allow? (y/n)
   ```

3. **Use official plugins first**
   - Anthropic-verified plugins
   - Community-recommended plugins
   - Starred/forked plugins

4. **Audit regularly**
   ```bash
   /plugin audit
   # Shows all plugin permissions
   ```

### Plugin Best Practices

**1. Install plugins at project level**
```bash
# In .claude/settings.json
{
  "plugins": [
    "eslint-assistant",
    "test-generator",
    "jira-integration"
  ]
}
```

**2. Share plugin configs with team**
```bash
# Commit plugin configuration
git add .claude/plugins/
git commit -m "Add team plugin config"
```

**3. Create organization plugins**
```bash
# Internal plugins for your company
org-plugins/
├── company-linter/
├── deployment-helper/
└── ticket-manager/
```

---

## 13. MCP Servers

MCP project scope allows adding MCP servers to .mcp.json files and committing them to repositories (v0.2.50), with remote MCP servers (SSE and HTTP) supporting OAuth in v1.0.27

### What Are MCP Servers?

**MCP = Model Context Protocol**

MCP servers are external tools that extend Claude's capabilities:
- Database access
- API integrations
- Custom business logic
- External data sources
- Third-party services

**Think of MCP as:**
- USB ports for Claude Code
- Plugin APIs
- External function calls

### Common MCP Servers

**Official Anthropic MCPs:**
- `@anthropic-ai/mcp-server-filesystem` - File system access
- `@anthropic-ai/mcp-server-fetch` - HTTP requests
- `@anthropic-ai/mcp-server-sqlite` - SQLite database
- `@anthropic-ai/mcp-server-postgres` - PostgreSQL database

**Community MCPs:**
- `mcp-server-github` - GitHub API integration
- `mcp-server-slack` - Slack messaging
- `mcp-server-linear` - Linear project management
- `mcp-server-aws` - AWS service calls

### Installing MCP Servers

**Method 1: Interactive wizard**
```bash
claude mcp add
```

**Method 2: Direct install**
```bash
# Install from npm
npm install -g @anthropic-ai/mcp-server-postgres

# Configure
claude mcp add postgres
```

**Method 3: Project-level**
```bash
# .mcp.json in project root
{
  "mcpServers": {
    "postgres": {
      "command": "mcp-server-postgres",
      "args": [],
      "env": {
        "DATABASE_URL": "${DATABASE_URL}"
      }
    }
  }
}
```

### Configuring MCP Servers

**View MCP configuration:**
```bash
/mcp
```

**Configure environment:**
```bash
# .env file
DATABASE_URL=postgresql://localhost:5432/mydb
GITHUB_TOKEN=ghp_xxxxxxxxxxxxx
SLACK_TOKEN=xoxb-xxxxxxxxxxxxx
```

**Test MCP connection:**
```bash
/mcp test postgres
```

### Using MCP Servers

**Once configured, Claude can use them automatically:**

```bash
# Database queries (via postgres MCP)
> Query the users table for accounts created this week

# GitHub operations (via github MCP)  
> Create a new issue in the repo

# Slack messages (via slack MCP)
> Send a message to #engineering channel about deployment
```

### Advanced MCP Configuration

**OAuth for remote MCPs:**
Remote MCP servers (SSE and HTTP) now support OAuth (v1.0.27), with OAuth authentication server discovery added in v1.0.35

```json
{
  "mcpServers": {
    "github-oauth": {
      "command": "mcp-server-github",
      "oauth": {
        "authorizationUrl": "https://github.com/login/oauth/authorize",
        "tokenUrl": "https://github.com/login/oauth/access_token",
        "clientId": "${GITHUB_CLIENT_ID}",
        "scopes": ["repo", "read:user"]
      }
    }
  }
}
```

**Multiple config files:**
MCP supports multiple config files with --mcp-config file1.json file2.json (v1.0.73)

```bash
claude --mcp-config .mcp.json --mcp-config .mcp.local.json
```

**Custom headers:**
```json
{
  "mcpServers": {
    "internal-api": {
      "transport": "sse",
      "url": "https://internal.company.com/mcp",
      "headers": {
        "Authorization": "Bearer ${API_TOKEN}",
        "X-Team": "engineering"
      }
    }
  }
}
```

### Creating Custom MCP Servers

**Minimal MCP server (Node.js):**
```javascript
#!/usr/bin/env node
import { Server } from '@modelcontextprotocol/sdk/server/index.js';
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';

const server = new Server({
  name: 'custom-mcp',
  version: '1.0.0',
});

// Define tools
server.setRequestHandler('tools/list', async () => ({
  tools: [{
    name: 'custom_action',
    description: 'Does something useful',
    inputSchema: {
      type: 'object',
      properties: {
        input: { type: 'string' }
      }
    }
  }]
}));

// Handle tool calls
server.setRequestHandler('tools/call', async (request) => {
  if (request.params.name === 'custom_action') {
    // Your logic here
    return {
      content: [{ 
        type: 'text', 
        text: 'Result here' 
      }]
    };
  }
});

// Start server
const transport = new StdioServerTransport();
await server.connect(transport);
```

**Package it:**
```json
{
  "name": "mcp-server-custom",
  "version": "1.0.0",
  "bin": {
    "mcp-server-custom": "./index.js"
  },
  "dependencies": {
    "@modelcontextprotocol/sdk": "^1.0.0"
  }
}
```

### MCP Best Practices

**1. Use project-level configs**
```bash
# Commit .mcp.json to git
# Team shares same MCP configuration
```

**2. Secure credentials**
```bash
# Never commit .env files
# Use environment variables
# Rotate tokens regularly
```

**3. Test MCPs separately**
```bash
# Test MCP before using in Claude
mcp-server-postgres test
```

**4. Monitor MCP usage**
```bash
/mcp stats
# Shows call counts, errors, latency
```

---

## 14. Testing Strategies

### The TDD Workflow with Claude

**Test-Driven Development = Write tests first**

This workflow produces the highest quality code:

**Step 1: Write test first**
```bash
> Create a failing test for the user registration endpoint
```

**Step 2: Run test (should fail)**
```bash
> Run the test - it should fail
```

**Step 3: Implement feature**
```bash
> Now implement the registration endpoint to make the test pass
```

**Step 4: Run test (should pass)**
```bash
> Run the test again - it should pass now
```

**Step 5: Refactor if needed**
```bash
> Refactor the implementation to improve code quality
```

### Complete Testing Prompt

```bash
> I need comprehensive testing for the authentication system.

Please create:

1. Unit tests for:
   - JWT token generation
   - Token validation  
   - Password hashing
   - User model methods

2. Integration tests for:
   - /auth/register endpoint
   - /auth/login endpoint
   - /auth/refresh endpoint
   - Protected route middleware

3. E2E tests for:
   - Complete registration flow
   - Login and token refresh
   - Password reset flow

Use:
- Jest as test framework
- Supertest for API testing
- Mock external dependencies
- Aim for >90% coverage

After creating tests, run them and fix any failures.
```

### Testing Patterns

**Pattern 1: Test sub-agent**
```bash
# Create dedicated test agent
> @test-agent Run all tests and report detailed results

# Main Claude continues working  
> Implement the password reset feature
```

**Pattern 2: Test-driven refactoring**
```bash
# Ensure tests exist
> Check test coverage for auth module

# If coverage low
> Add tests to bring coverage to >90%

# Then refactor safely
> Refactor auth module for better maintainability

# Verify tests still pass
> Run all tests
```

**Pattern 3: Automated test generation**
```bash
# After implementing feature
> Generate comprehensive tests for what we just built

# Review generated tests
> @test-agent Review the generated tests for completeness
```

### Testing Tools Integration

**Jest configuration:**
```bash
> Setup Jest with TypeScript support and coverage reporting
```

**Playwright for E2E:**
```bash
> Configure Playwright for E2E testing of our Next.js app
```

**Storybook for components:**
```bash
> Add Storybook stories for all UI components
```

### Testing Metrics

**Track improvements:**
```bash
# Before Claude Code
Coverage: 45%
Tests: 234
Time to write tests: ~40% of dev time

# After Claude Code
Coverage: 92%
Tests: 876
Time to write tests: ~15% of dev time (auto-generated + reviewed)
```

---

## 15. VS Code & JetBrains Integration

New beta extensions for VS Code and JetBrains integrate Claude Code directly into your IDE, with Claude's proposed edits appearing inline in your files, streamlining review and tracking within the familiar editor interface

### Installing IDE Extensions

**VS Code:**
```bash
# Install extension
# Open VS Code, press Cmd+P (Mac) or Ctrl+P (Win)
> ext install anthropic.claude-code

# Or install from terminal while in project
cd your-project
code --install-extension anthropic.claude-code
```

**JetBrains (IntelliJ, WebStorm, PyCharm):**
```bash
# Settings → Plugins → Marketplace
# Search: "Claude Code"
# Install and restart IDE
```

### Using Claude Code in Your IDE

**1. Start Claude Code in terminal**
```bash
# In VS Code integrated terminal
claude

# Claude detects IDE and enables integration
```

**2. Inline diffs**
```
When Claude proposes changes, they appear as inline diffs:

// Before
function authenticate(user) {
  return user.password === hash;
}

// Claude's proposed change (highlighted in IDE)
function authenticate(user, password) {
  return await bcrypt.compare(password, user.passwordHash);
}
```

**3. Accept/Reject in IDE**
```
[Accept] [Reject] [Accept All] [Show in Terminal]
     ↑ Click directly in your IDE
```

**4. Track changes**
```
Your IDE's git integration shows Claude's changes
Your existing git workflow continues normally
```

### IDE Integration Features

**Syntax highlighting:**
- All diffs use your theme
- Language-specific highlighting
- Semantic tokens

**Navigation:**
- Jump to changes with keyboard
- Review changes one by one
- See full context of edits

**Testing:**
- Run tests from IDE
- See results inline
- Quick-fix failed tests

**Debugging:**
- Set breakpoints normally
- Debug Claude's code
- Step through generated logic

### Best Practices for IDE Usage

**1. Terminal + IDE split**
```
┌──────────────────────────────────────┐
│  VS Code                             │
├──────────────────────────────────────┤
│  Code files (top)                    │
│  ▼ Shows Claude's diffs inline       │
│                                      │
├──────────────────────────────────────┤
│  Terminal (bottom)                   │
│  ▶ Claude Code running here          │
└──────────────────────────────────────┘
```

**2. Use keyboard shortcuts**
```
Cmd+Shift+A (Mac) / Ctrl+Shift+A (Win)
→ Accept Claude's current change

Cmd+Shift+R (Mac) / Ctrl+Shift+R (Win)
→ Reject Claude's current change
```

**3. Review in IDE, discuss in terminal**
```
Terminal: "Add error handling"
IDE: Review proposed error handling code
Terminal: "That looks good"
```

**4. Combine with git tools**
```
IDE Git integration → See all changes
GitLens → Blame and history
Git diff tool → Compare versions
```

---

## 16. Output Styles & Educational Modes

Released output styles in v1.0.81, including new built-in educational output styles "Explanatory" and "Learning"

### What Are Output Styles?

**Output styles = How Claude explains code**

Different styles for different contexts:
- **Standard**: Concise, professional
- **Explanatory**: Detailed with reasoning
- **Learning**: Educational with concepts
- **Terse**: Minimal, code-only
- **Verbose**: Maximum detail

### Activating Output Styles

**View available styles:**
```bash
/output-styles
```

**Activate a style:**
```bash
/output-style explanatory
```

**Or inline:**
```bash
> In learning mode: Explain how JWT authentication works
```

### Output Style Examples

**Standard (default):**
```bash
> Add input validation

Claude:
Added Zod validation schema in src/validation/user.ts
Updated API route to use validation
Returns 400 for invalid input
```

**Explanatory:**
```bash
/output-style explanatory
> Add input validation

Claude:
I'll add input validation using Zod for several reasons:

1. Type safety: Zod provides runtime type checking that 
   matches our TypeScript types
2. Error messages: It generates user-friendly validation errors
3. Transformation: Can coerce and transform inputs automatically

Implementation:
- Created UserSchema in src/validation/user.ts
  - Validates email format, password strength
  - Trims whitespace, lowercases email
- Updated src/app/api/users/route.ts
  - Parses request body with UserSchema
  - Returns detailed errors on validation failure
- Added unit tests in src/validation/user.test.ts

This approach catches invalid data early, provides clear 
feedback to users, and maintains type safety throughout.
```

**Learning:**
```bash
/output-style learning
> Add input validation

Claude:
## Input Validation - Concepts & Implementation

### Why We Validate Input
Input validation is crucial for three reasons:
1. Security (prevent injection attacks)
2. Data integrity (ensure correct format)
3. User experience (clear error messages)

### Validation Approaches

**Client-side validation**
Pros: Immediate feedback, reduced server load
Cons: Can be bypassed, not secure alone

**Server-side validation** ← What we're implementing
Pros: Secure, authoritative
Cons: Slightly slower feedback

### Implementation with Zod

Zod is a TypeScript-first validation library that:
- Infers TypeScript types from schemas
- Provides runtime validation
- Generates detailed error messages

[... detailed explanation with code examples ...]

### Key Concepts Applied
- Schema definition
- Runtime type checking
- Error handling
- Type inference

### Next Steps to Learn
- Study Zod documentation for advanced schemas
- Explore validation patterns in other languages
- Learn about sanitization vs validation
```

### Custom Output Styles

**Create your own style:**

**File: `.claude/output-styles/senior-engineer.md`**
```markdown
---
name: Senior Engineer
description: Code reviews like a senior engineer
---

# Senior Engineer Output Style

When reviewing or creating code:

1. **Critique**: Point out potential issues
   - Performance concerns
   - Security implications
   - Maintainability problems
   - Edge cases

2. **Rationale**: Explain technical decisions
   - Why this approach over alternatives
   - Trade-offs made
   - Long-term implications

3. **Best Practices**: Reference standards
   - Industry conventions
   - Team patterns
   - Design principles

4. **Improvement Suggestions**: Offer enhancements
   - Optimization opportunities
   - Architecture improvements
   - Testing recommendations

Format: Direct, technical, assumes expertise
```

**Activate:**
```bash
/output-style senior-engineer
> Review this authentication implementation
```

### When to Use Each Style

| Style | Use Case | Example |
|-------|----------|---------|
| Standard | Daily work | "Add feature X" |
| Explanatory | Complex features | "Refactor auth system" |
| Learning | Teaching juniors | "Explain async/await" |
| Terse | Quick fixes | "Fix typo" |
| Verbose | Critical systems | "Implement payment processing" |

---

## 17. Background Commands & Parallel Execution

Background commands released in v1.0.71: press Ctrl-b to run any Bash command in the background so Claude can keep working, great for dev servers, tailing logs, etc.

### What Are Background Commands?

**Problem**: Claude can't work while dev servers run
**Solution**: Background commands

```bash
# Old way (blocked)
> Run npm run dev
[Claude waits forever for server to finish]

# New way (background)
> Run npm run dev in background
[Server runs, Claude continues working]
```

### Using Background Commands

**Method 1: Explicit request**
```bash
> Start the development server in the background
```

**Method 2: Keyboard shortcut**
```bash
# Type your command
npm run dev

# Press Ctrl+B before Enter
# Command runs in background
```

**Method 3: Automatic (long-running commands)**
Auto-background long-running bash commands instead of killing them, customizable with BASH_DEFAULT_TIMEOUT_MS environment variable (v1.0.90)

```bash
# These auto-background:
> npm run dev        (dev servers)
> npm run watch      (file watchers)  
> tail -f logs.txt   (log tailing)
> docker-compose up  (containers)
```

### Managing Background Processes

**View running processes:**
```bash
/background
```

**Output shows:**
```
Background Processes:
[1] npm run dev (PID: 12345)
    Status: Running
    Started: 5m ago
    Output: Server running on http://localhost:3000

[2] npm run test:watch (PID: 12346)
    Status: Running  
    Started: 2m ago
    Output: Watching for file changes...
```

**Kill a process:**
```bash
> Kill background process 1

# Or from terminal
kill 12345
```

**View process output:**
```bash
> Show output from background process 1
```

### Practical Background Workflows

**1. Full-stack development**
```bash
# Start backend server
> Run npm run server in background

# Start frontend dev server  
> Run npm run client in background

# Start database
> Run docker-compose up -d postgres in background

# Now Claude can work on features while everything runs
> Implement the user profile page
```

**2. Watch-and-develop**
```bash
# Start test watcher
> Run npm run test:watch in background

# Start build watcher
> Run npm run build:watch in background

# Develop with live feedback
> Refactor the authentication module

# Tests and builds update automatically
```

**3. Log monitoring**
```bash
# Tail application logs
> Run tail -f /var/log/app.log in background

# Tail error logs
> Run tail -f /var/log/error.log in background

# Monitor while developing
> Implement new feature

# Check logs periodically
> Show recent output from log processes
```

### Advanced Background Patterns

**Pattern 1: Development environment setup**
```bash
> Start my full development environment:
> 1. Backend server (port 3000) in background
> 2. Frontend dev server (port 3001) in background  
> 3. Database (docker compose) in background
> 4. Redis (docker) in background
> 5. Email service (Mailhog) in background
>
> Then implement the password reset feature
```

**Pattern 2: Continuous testing**
```bash
# Start test watcher
> @test-agent Watch all tests in background

# Develop with confidence
> Refactor the payment processing module

# Tests alert if anything breaks
```

**Pattern 3: Build optimization**
```bash
# Start production build in background
> Run npm run build:prod in background

# Work on something else
> Fix the bug in the dashboard

# Check build status later
> Is the production build done?
```

---

## 18. Complete Command Reference

### Essential Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/status` | View context & cost | `/status` |
| `/context` | Debug context usage | `/context` |
| `/clear` | Wipe conversation | `/clear` |
| `/compact` | Summarize context | `/compact Focus on auth` |
| `/resume` | Return to old chat | `/resume` |
| `/rewind` | Roll back changes | `/rewind` |
| `/help` | Show all commands | `/help` |

### Model & Performance

| Command | Purpose | Example |
|---------|---------|---------|
| `/model` | Change model | `/model` → Select Opus 4 |
| `/cost` | View usage costs | `/cost` |
| `/upgrade` | Upgrade subscription | `/upgrade` |

### Project Management

| Command | Purpose | Example |
|---------|---------|---------|
| `/add-dir` | Add working directory | `/add-dir ../other-project` |
| `/permissions` | Manage tool permissions | `/permissions` |
| `/statusline` | Customize status line | `/statusline` |
| `/terminal-setup` | Configure terminal | `/terminal-setup` |

### Memory & Context

| Command | Purpose | Example |
|---------|---------|---------|
| `/memory` | Edit memory files | `/memory` |
| `/todos` | List current todos | `/todos` |
| `/export` | Export conversation | `/export` |

### Testing & Quality

| Command | Purpose | Example |
|---------|---------|---------|
| `/doctor` | Diagnose issues | `/doctor` |
| `/mcp` | Manage MCP servers | `/mcp` |

### Skills & Plugins

| Command | Purpose | Example |
|---------|---------|---------|
| `/skills` | Manage skills | `/skills browse` |
| `/plugin` | Manage plugins | `/plugin marketplace` |
| `/agents` | Manage custom agents | `/agents` |

### GitHub Integration

| Command | Purpose | Example |
|---------|---------|---------|
| `/install-github-app` | Install GitHub app | `/install-github-app` |
| `/pr-comments` | Comment on PRs | Internal use |

### Output & Display

| Command | Purpose | Example |
|---------|---------|---------|
| `/output-style` | Change output style | `/output-style learning` |
| `/vim` | Enable vim bindings | `/vim` |
| `/background` | View background processes | `/background` |

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Enter` | Submit prompt |
| `Ctrl+C` | Interrupt Claude |
| `Ctrl+R` | Toggle transcript |
| `Ctrl+O` | Show full transcript |
| `Ctrl+B` | Run command in background |
| `Ctrl+_` | Undo prompt input |
| `Ctrl+Z` | Suspend Claude Code |
| `Tab` | Autocomplete |
| `Shift+Tab` | Toggle auto-accept edits |
| `Esc` | Cancel/Exit dialog |

**Vim mode (after `/vim`):**
- `h/j/k/l` - Navigation
- `i` - Insert mode
- `Esc` - Normal mode
- `u` - Undo
- `c/f/F/t/T` - Vim motions

---

## 19. Troubleshooting Guide

### Common Issues & Solutions

#### 1. Context Window Full

**Symptom:**
```
Warning: Context window at 85%
```

**Solution:**
```bash
# Option 1: Clear context
/clear

# Option 2: Compact intelligently
/compact Preserve recent implementation decisions

# Option 3: Finish current task first
> Complete the current feature
/clear
> Start next feature
```

#### 2. Claude Makes Unwanted Changes

**Symptom:**
Code changes you didn't approve

**Solution:**
```bash
# Option 1: Rewind
/rewind
# Select checkpoint before changes

# Option 2: Git reset
git reset --hard HEAD

# Option 3: Specific file reset
git checkout HEAD -- file.ts

# Prevention:
# - Use feature branches
# - Review diffs before accepting
# - Enable auto-accept only for trusted operations
```

#### 3. Tests Failing After Changes

**Symptom:**
Claude's code breaks existing tests

**Solution:**
```bash
# Step 1: Identify failures
> Run tests and show failures

# Step 2: Ask Claude to fix
> Fix the failing tests

# Step 3: If unfixable, rewind
/rewind

# Prevention:
# - Run tests before major changes
# - Use TDD approach
# - Have @test-agent monitor tests
```

#### 4. MCP Server Connection Issues

**Symptom:**
```
Error: MCP server 'postgres' failed to start
```

**Solution:**
```bash
# Check MCP status
/mcp

# Test connection
/mcp test postgres

# View detailed logs
claude --mcp-debug

# Fix common issues:
# - Check DATABASE_URL environment variable
# - Verify server is running
# - Check permissions
# - Update MCP server: npm update -g mcp-server-postgres
```

#### 5. Performance Degradation

**Symptom:**
Claude becomes slow or unresponsive

**Solution:**
```bash
# Check context usage
/status

# Likely causes:
# 1. Context >80% → /compact or /clear
# 2. Many background processes → /background and kill unused
# 3. Large files in context → Be selective with @-mentions
# 4. Too many MCP servers → /mcp and disable unused

# Nuclear option:
/clear
# Start fresh session
```

#### 6. IDE Integration Not Working

**Symptom:**
Diffs don't appear in VS Code/JetBrains

**Solution:**
```bash
# Check extension installed
# VS Code: Cmd+Shift+X → Search "Claude Code"
# JetBrains: Settings → Plugins → Search "Claude Code"

# Restart IDE and Claude Code
# 1. Close Claude Code terminal
# 2. Restart IDE
# 3. Open project terminal
# 4. Start: claude

# Check Claude detected IDE
> Am I connected to an IDE?

# Manual connection
export CLAUDE_CODE_AUTO_CONNECT_IDE=true
claude
```

#### 7. Authentication Issues

**Symptom:**
```
Error: Authentication failed
```

**Solution:**
```bash
# Re-authenticate
claude --logout
claude

# Check subscription
# Visit: https://claude.ai/settings

# API key issues
export ANTHROPIC_API_KEY=your-key
claude

# Bedrock/Vertex issues
# Check AWS/GCP credentials
aws configure
# or
gcloud auth application-default login
```

### Diagnostic Commands

**Full system check:**
```bash
/doctor
```

**Detailed context analysis:**
```bash
/context
```

**MCP health:**
```bash
/mcp

# For each server
/mcp test postgres
/mcp test github
```

**Permission issues:**
```bash
/permissions
```

---

## 20. Real-World Success Patterns

### Pattern 1: Greenfield Project Kickstart

**Scenario**: Starting a new project from scratch

**Workflow:**
```bash
# Day 1: Setup
> Initialize a Next.js 14 project with TypeScript, Tailwind, 
> and Prisma. Use App Router. Create initial folder structure.
> Add CLAUDE.md documenting our conventions.

# Day 1: Database
> Design database schema for a task management app with:
> - Users (auth with NextAuth)
> - Projects  
> - Tasks
> - Comments
> Create Prisma schema and initial migration.

# Day 2: Authentication
> Implement complete authentication system:
> - Email/password signup/login
> - JWT tokens
> - Password reset flow
> - Protected API routes
> - Session management

# Day 3-4: Core Features
> Implement CRUD operations for projects and tasks
> Add real-time updates with Server-Sent Events
> Create beautiful UI with Shadcn components

# Day 5: Polish
> Add error handling, loading states, and form validation
> Write comprehensive tests
> Deploy to Vercel
```

**Result**: MVP in 5 days vs typical 2-3 weeks

### Pattern 2: Legacy Code Refactoring

**Scenario**: Modernizing old codebase

**Workflow:**
```bash
# Phase 1: Understanding
> Analyze the current architecture of this Express app
> Identify technical debt and code smells
> Create a refactoring plan

# Phase 2: Tests First
> Create comprehensive tests for existing functionality
> Aim for >80% coverage before refactoring
> Document current behavior

# Phase 3: Incremental Refactoring
/clear

> Following the plan, refactor the authentication module
> from callbacks to async/await
> Ensure all tests pass

/clear

> Refactor database layer to use Prisma instead of raw SQL
> Migrate one table at a time
> Tests must keep passing

# Continue module by module with /clear between each
```

**Result**: Rakuten validated Opus 4's capabilities with a demanding open-source refactor running independently for 7 hours with sustained performance

### Pattern 3: Bug Investigation & Fix

**Scenario**: Production bug needs quick resolution

**Workflow:**
```bash
# Step 1: Reproduce
> Help me reproduce this bug: Users report session expires 
> randomly on the dashboard. 

> Check: Session config, token expiration, refresh logic

# Step 2: Root Cause
> I can reproduce it. Session expires when user is idle for
> exactly 15 minutes. Find why this happens.

# Step 3: Fix with Tests
> Create a failing test that reproduces this bug
> Then fix the bug
> Test should pass

# Step 4: Verify
> Run full test suite
> Check for similar issues in other parts of code
> Create documentation for the fix
```

**Result**: Bug fixed in 30 minutes with tests

### Pattern 4: Feature Addition to Existing App

**Scenario**: Add complex feature to mature codebase

**Workflow:**
```bash
# Step 1: Planning
> I need to add a notification system to our app.
> First, analyze our architecture and create a detailed plan
> considering: real-time requirements, scalability, existing 
> tech stack (Next.js, Postgres, Redis available)

# Review plan, iterate if needed

# Step 2: Branch Strategy
git checkout -b feature/notifications
git push -u origin feature/notifications

# Step 3: Incremental Implementation
/clear

> Implement Phase 1 from the plan: Database schema
/rewind  # Create checkpoint

> Implement Phase 2: Backend API
/rewind  # Create checkpoint

> Implement Phase 3: Frontend components
/rewind  # Create checkpoint

> Implement Phase 4: Real-time SSE integration

# Step 4: Testing & Review
> @test-agent Create comprehensive tests for notifications

# Step 5: PR & Deploy
> Create PR description documenting the implementation
```

**Result**: Complex feature in 2 days vs 1-2 weeks

### Pattern 5: Team Onboarding

**Scenario**: New developer joining the team

**Workflow:**
```bash
# Create onboarding guide
> Create a comprehensive onboarding guide for new developers
> Include: setup instructions, architecture overview, 
> coding conventions, development workflow, testing strategy

# Generate skills for company conventions
> Create a Claude Code skill from our coding conventions
> Save as .claude/skills/company-patterns/

# Create helper agents
> Create a @docs-agent that knows our codebase and can
> answer questions about architecture and conventions

# New developer uses
claude
> @docs-agent Explain how authentication works in this app
> @docs-agent Where should I put new API routes?
```

**Result**: New developers productive in days vs weeks

### Measured Outcomes from Real Teams

**Startup (5 developers):**
- 30% faster feature delivery
- 50% reduction in bugs
- 80% increase in test coverage
- 2x more documentation

**Enterprise (50+ developers):**
- 20% productivity increase
- 60% faster onboarding
- 40% less time in code review
- 90% of conventions followed

**Solo Developer:**
- 3x project velocity
- Better code quality
- Consistent documentation
- More time for learning

---

## 21. Learning Roadmap

### Week 1: Foundations

**Day 1-2: Setup & Basics**
- [ ] Install Claude Code
- [ ] Complete first session tutorial
- [ ] Create basic CLAUDE.md
- [ ] Try 5-10 simple requests

**Day 3-4: Context Management**
- [ ] Practice /clear, /compact, /resume
- [ ] Monitor context with /status
- [ ] Understand the 80% rule
- [ ] Practice the 4-phase workflow

**Day 5-7: Git Integration**
- [ ] Create feature branches workflow
- [ ] Practice /rewind
- [ ] Set up checkpoints
- [ ] Try git worktrees

**Goals**: Comfortable with basic workflow

### Week 2: Core Productivity

**Day 1-2: Planning**
- [ ] Practice plan-before-code workflow
- [ ] Try thinking modes
- [ ] Create 3 detailed plans
- [ ] Iterate on plans

**Day 3-4: Custom Commands**
- [ ] Create .claude/commands/
- [ ] Build 5 custom commands
- [ ] Organize commands in subdirectories
- [ ] Share commands with team (if applicable)

**Day 5-7: Documentation**
- [ ] Expand CLAUDE.md
- [ ] Add architecture docs
- [ ] Document conventions
- [ ] Create @-importable files

**Goals**: 2x faster than without Claude Code

### Week 3: Advanced Features

**Day 1-2: Sub-agents**
- [ ] Create @test-agent
- [ ] Create @security-agent
- [ ] Practice parallel work
- [ ] Build agent pipeline

**Day 3-4: Skills & Plugins**
- [ ] Install relevant skills
- [ ] Try 3-5 plugins
- [ ] Create custom skill
- [ ] Share skills with team

**Day 5-7: IDE Integration**
- [ ] Install VS Code/JetBrains extension
- [ ] Practice inline diffs
- [ ] Configure shortcuts
- [ ] Optimize split-screen workflow

**Goals**: Mastery of advanced features

### Week 4: Optimization & Mastery

**Day 1-2: Performance**
- [ ] Optimize context usage
- [ ] Master background commands
- [ ] Fine-tune output styles
- [ ] Build efficient workflows

**Day 3-4: Team Patterns**
- [ ] Create team CLAUDE.md
- [ ] Build team commands
- [ ] Setup shared skills
- [ ] Document team workflow

**Day 5-7: Personal System**
- [ ] Refine personal workflow
- [ ] Create personal commands
- [ ] Build personal agents
- [ ] Measure productivity gains

**Goals**: Consistent 30%+ productivity increase

### Mastery Checklist

**Foundations:**
- ✅ CLAUDE.md is comprehensive and updated
- ✅ Use feature branches for all work
- ✅ Context management is automatic
- ✅ Checkpoints created at critical points

**Productivity:**
- ✅ Always plan before implementing
- ✅ Custom commands for repetitive tasks
- ✅ Sub-agents for parallel work
- ✅ Tests written with/before code

**Advanced:**
- ✅ IDE integration is seamless
- ✅ Skills installed and effective
- ✅ Plugins enhance workflow
- ✅ MCP servers for integrations

**Team:**
- ✅ Team conventions documented
- ✅ Shared commands and skills
- ✅ Consistent coding standards
- ✅ Knowledge sharing system

### Next-Level Patterns

**After mastering basics, explore:**

1. **Agent Orchestration**
   - Multiple agents working together
   - Complex agent pipelines
   - Agent specialization

2. **Custom Tooling**
   - Build MCP servers
   - Create plugins
   - Develop skills

3. **Workflow Automation**
   - Pre-commit hooks with Claude
   - CI/CD integration
   - Automated documentation

4. **Team Scaling**
   - Onboarding automation
   - Code review assistance
   - Knowledge management

---

## Conclusion

### The Claude Code Philosophy

**1. Context is King**
- Maintain CLAUDE.md religiously
- Manage context window carefully
- Clear between features

**2. Plan Before Coding**
- Always plan complex changes
- Iterate on plans
- Implement incrementally

**3. Safety First**
- Use feature branches
- Create checkpoints
- Review all changes

**4. Continuous Learning**
- Skills for knowledge
- Plugins for tools
- Agents for specialization

### Success Formula

```
Success = 
  (Great CLAUDE.md) 
  × (Context Management) 
  × (Planning Discipline)
  × (Git Safety)
  × (Right Tools)
  × (Consistent Practice)
```

### Getting Help

**Official Resources:**
- Documentation: https://docs.claude.com/claude-code
- Changelog: https://claudelog.com/claude-code-changelog/
- Support: https://support.claude.com

**Community:**
- Reddit: r/ClaudeCode
- GitHub Issues: github.com/anthropics/claude-code
- Discord: Anthropic community

**This Guide:**
- Updated: November 2025
- Version: 2.1
- Target: Claude Code v1.0.124+

---

## Appendix: Quick Reference Cards

### Emergency Quick Commands

```bash
# Something went wrong
/rewind                    # Roll back changes
git reset --hard HEAD      # Nuclear git reset

# Context issues
/clear                     # Fresh start
/compact                   # Smart compression

# Performance issues
/status                    # Check usage
/context                   # Debug details

# Get help
/help                      # All commands
/doctor                    # Diagnose issues
```

### Daily Workflow Template

```bash
# Morning startup
cd project
git pull
git checkout -b feature/new-feature
claude

# Work session
> [Describe feature]
# Review plan, iterate
# Implement incrementally
# Test continuously

# Afternoon
/rewind                    # Checkpoint
# Continue working
git add .
git commit -m "Implement X"

# End of day
git push
# Create PR
/export                    # Save conversation
```

### Context Management Cheatsheet

| Usage | Action |
|-------|--------|
| 0-30% | Work freely |
| 30-50% | Plan carefully |
| 50-80% | Watch closely |
| 80%+ | /compact or /clear |
| 100% | Must /clear |

### File Organization

```
project/
├── .claude/
│   ├── CLAUDE.md              # Project knowledge
│   ├── settings.json          # Project settings
│   ├── commands/              # Custom commands
│   │   ├── frontend/
│   │   ├── backend/
│   │   └── testing/
│   ├── agents/                # Custom agents
│   │   ├── test-agent.md
│   │   ├── security-agent.md
│   │   └── docs-agent.md
│   ├── skills/                # Custom skills
│   │   └── company-patterns/
│   └── output-styles/         # Custom styles
├── .mcp.json                  # MCP configuration
└── .env                       # Environment (DO NOT COMMIT)
```

---

*Built by developers, for developers. May your code be clean and your context window free.*

**Happy coding with Claude Code! 🚀**
