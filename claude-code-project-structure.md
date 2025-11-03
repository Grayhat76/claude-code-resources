# Claude Code Example Project Structure

Complete example showing how to organize a project for optimal Claude Code usage.

---

## Complete Directory Tree

```
my-nextjs-app/
├── .claude/                           # Claude Code configuration
│   ├── CLAUDE.md                     # Main project context (REQUIRED)
│   ├── settings.json                 # Project-level settings
│   ├── .mcp.json                     # MCP server config (optional)
│   │
│   ├── commands/                     # Custom slash commands
│   │   ├── README.md                 # Command documentation
│   │   ├── frontend/                 # Frontend commands
│   │   │   ├── component.md          # /frontend:component
│   │   │   ├── page.md               # /frontend:page
│   │   │   └── hook.md               # /frontend:hook
│   │   ├── backend/                  # Backend commands
│   │   │   ├── endpoint.md           # /backend:endpoint
│   │   │   ├── service.md            # /backend:service
│   │   │   └── migration.md          # /backend:migration
│   │   └── testing/                  # Testing commands
│   │       ├── unit.md               # /testing:unit
│   │       └── e2e.md                # /testing:e2e
│   │
│   ├── agents/                       # Custom sub-agents
│   │   ├── README.md                 # Agent documentation
│   │   ├── test-agent.md             # @test-agent
│   │   ├── security-agent.md         # @security-agent
│   │   ├── code-reviewer.md          # @code-reviewer
│   │   ├── docs-agent.md             # @docs-agent
│   │   ├── performance-agent.md      # @performance-agent
│   │   ├── refactor-agent.md         # @refactor-agent
│   │   └── database-agent.md         # @database-agent
│   │
│   ├── skills/                       # Custom skills
│   │   └── company-patterns/         # Company-specific patterns
│   │       ├── skill.json            # Skill metadata
│   │       ├── README.md             # Skill documentation
│   │       ├── knowledge.md          # Core knowledge
│   │       ├── patterns.md           # Code patterns
│   │       └── examples/             # Example code
│   │           ├── api-pattern.ts
│   │           └── component-pattern.tsx
│   │
│   ├── output-styles/                # Custom output styles
│   │   ├── senior-engineer.md        # Engineering review style
│   │   └── beginner-friendly.md     # Educational style
│   │
│   ├── docs/                         # Additional documentation
│   │   ├── architecture.md           # Imported via @.claude/docs/architecture.md
│   │   ├── api-conventions.md        # API design patterns
│   │   ├── database-schema.md        # Database documentation
│   │   └── deployment.md             # Deployment procedures
│   │
│   └── templates/                    # Reusable templates
│       ├── component-template.tsx    # React component template
│       ├── api-route-template.ts     # API route template
│       └── test-template.test.ts     # Test file template
│
├── src/                              # Application source code
│   ├── app/                          # Next.js app directory
│   │   ├── (auth)/                   # Auth route group
│   │   │   ├── login/
│   │   │   │   └── page.tsx
│   │   │   └── register/
│   │   │       └── page.tsx
│   │   ├── (dashboard)/              # Dashboard route group
│   │   │   ├── dashboard/
│   │   │   │   └── page.tsx
│   │   │   └── settings/
│   │   │       └── page.tsx
│   │   ├── api/                      # API routes
│   │   │   ├── auth/
│   │   │   │   ├── login/
│   │   │   │   │   └── route.ts
│   │   │   │   └── register/
│   │   │   │       └── route.ts
│   │   │   └── users/
│   │   │       ├── route.ts          # GET /api/users
│   │   │       └── [id]/
│   │   │           └── route.ts      # GET /api/users/:id
│   │   ├── layout.tsx                # Root layout
│   │   └── page.tsx                  # Home page
│   │
│   ├── components/                   # React components
│   │   ├── ui/                       # Base UI components (shadcn)
│   │   │   ├── button.tsx
│   │   │   ├── input.tsx
│   │   │   ├── card.tsx
│   │   │   └── ...
│   │   ├── features/                 # Feature-specific components
│   │   │   ├── auth/
│   │   │   │   ├── LoginForm.tsx
│   │   │   │   ├── LoginForm.test.tsx
│   │   │   │   └── LoginForm.types.ts
│   │   │   └── dashboard/
│   │   │       ├── StatsCard.tsx
│   │   │       └── ActivityFeed.tsx
│   │   └── layouts/                  # Layout components
│   │       ├── MainLayout.tsx
│   │       └── DashboardLayout.tsx
│   │
│   ├── lib/                          # Shared utilities
│   │   ├── db/                       # Database utilities
│   │   │   ├── client.ts             # Prisma client
│   │   │   ├── queries.ts            # Shared queries
│   │   │   └── migrations.ts         # Migration helpers
│   │   ├── auth/                     # Auth utilities
│   │   │   ├── jwt.ts                # JWT helpers
│   │   │   ├── password.ts           # Password hashing
│   │   │   └── session.ts            # Session management
│   │   ├── api/                      # API utilities
│   │   │   ├── client.ts             # API client
│   │   │   ├── error.ts              # Error handling
│   │   │   └── response.ts           # Response formatting
│   │   └── utils/                    # General utilities
│   │       ├── format.ts             # Formatting helpers
│   │       ├── validate.ts           # Validation helpers
│   │       └── date.ts               # Date utilities
│   │
│   ├── hooks/                        # Custom React hooks
│   │   ├── useAuth.ts
│   │   ├── useUser.ts
│   │   └── useDebounce.ts
│   │
│   ├── types/                        # TypeScript definitions
│   │   ├── User.types.ts
│   │   ├── Auth.types.ts
│   │   ├── ApiResponse.types.ts
│   │   └── index.ts                  # Re-exports
│   │
│   ├── styles/                       # Global styles
│   │   ├── globals.css
│   │   └── theme.css
│   │
│   └── config/                       # Configuration
│       ├── site.ts                   # Site configuration
│       └── constants.ts              # App constants
│
├── prisma/                           # Prisma/Database
│   ├── schema.prisma                 # Database schema
│   ├── migrations/                   # Migration history
│   │   ├── 20250101_init/
│   │   │   └── migration.sql
│   │   └── 20250115_add_profiles/
│   │       └── migration.sql
│   └── seed.ts                       # Seed data
│
├── public/                           # Static files
│   ├── images/
│   └── fonts/
│
├── tests/                            # Test files
│   ├── unit/                         # Unit tests
│   │   ├── utils/
│   │   │   └── format.test.ts
│   │   └── lib/
│   │       └── auth.test.ts
│   ├── integration/                  # Integration tests
│   │   └── api/
│   │       └── auth.test.ts
│   ├── e2e/                          # E2E tests
│   │   └── auth-flow.spec.ts
│   └── fixtures/                     # Test fixtures
│       ├── users.ts
│       └── posts.ts
│
├── docs/                             # Project documentation
│   ├── API.md                        # API documentation
│   ├── ARCHITECTURE.md               # Architecture overview
│   ├── DEPLOYMENT.md                 # Deployment guide
│   └── CONTRIBUTING.md               # Contribution guidelines
│
├── scripts/                          # Utility scripts
│   ├── setup.sh                      # Development setup
│   ├── deploy.sh                     # Deployment script
│   └── seed-db.ts                    # Database seeding
│
├── .github/                          # GitHub configuration
│   ├── workflows/                    # GitHub Actions
│   │   ├── ci.yml                    # CI pipeline
│   │   └── deploy.yml                # Deployment workflow
│   └── PULL_REQUEST_TEMPLATE.md      # PR template
│
├── .env.example                      # Example environment variables
├── .env                              # Environment variables (DO NOT COMMIT)
├── .gitignore                        # Git ignore rules
├── .eslintrc.json                    # ESLint configuration
├── .prettierrc                       # Prettier configuration
├── tsconfig.json                     # TypeScript configuration
├── next.config.js                    # Next.js configuration
├── package.json                      # Dependencies
├── package-lock.json                 # Locked dependencies
├── tailwind.config.ts                # Tailwind configuration
└── README.md                         # Project overview
```

---

## File Examples

### .claude/CLAUDE.md (Abbreviated)

```markdown
# Project: TaskFlow

## Project Overview
TaskFlow is a modern task management application built with Next.js 14.

## Tech Stack
- Framework: Next.js 14 (App Router)
- Language: TypeScript 5.3
- Database: PostgreSQL 15 with Prisma
- Styling: Tailwind CSS
- Auth: NextAuth.js

## Code Standards

### File Naming
- Components: PascalCase.tsx
- Utilities: camelCase.ts
- Hooks: camelCase.ts with "use" prefix

### TypeScript
- Use interfaces for objects
- Props interface above component
- Avoid 'any' type

## Development Workflow
1. Create feature branch
2. Implement with tests
3. Run full test suite
4. Create PR

## Commands
- `npm run dev` - Start dev server
- `npm test` - Run tests
- `npm run build` - Production build

## Import Additional Context
@.claude/docs/architecture.md
@.claude/docs/api-conventions.md
```

### .claude/settings.json

```json
{
  "allowedTools": ["Read", "StrReplace", "Write", "Bash", "Grep"],
  "autoAccept": {
    "Bash": ["npm test", "npm run lint"],
    "Read": ["*"],
    "StrReplace": ["src/**/*.ts", "src/**/*.tsx"]
  },
  "ignorePatterns": [
    "node_modules/**",
    "dist/**",
    "build/**",
    ".next/**"
  ],
  "outputStyle": "standard",
  "spinnerTipsEnabled": true
}
```

### .claude/.mcp.json

```json
{
  "mcpServers": {
    "postgres": {
      "command": "mcp-server-postgres",
      "args": [],
      "env": {
        "DATABASE_URL": "${DATABASE_URL}"
      }
    },
    "github": {
      "command": "mcp-server-github",
      "env": {
        "GITHUB_TOKEN": "${GITHUB_TOKEN}"
      }
    }
  }
}
```

### .claude/commands/frontend/component.md

```markdown
---
allowed-tools: [Read, Write, StrReplace]
argument-hint: component name (e.g. UserCard)
---

# React Component Generator

Create a new React component named {{arg}} following our patterns:

1. Functional component with TypeScript
2. Props interface directly above
3. Styled with Tailwind
4. Include test file
5. Export from index.ts

Location: src/components/features/{{arg}}/
```

### .claude/agents/test-agent.md

```markdown
---
name: Test Agent
model: sonnet
allowed-tools: [Read, Bash, Grep]
description: Runs tests and reports failures
---

# Test Agent

Run tests and provide detailed analysis of failures.

Commands:
- `npm test` - Run all tests
- `npm run test:coverage` - Coverage report

Report format:
- Summary (passed/failed/skipped)
- Detailed failures with fixes
- Coverage analysis
```

---

## Environment Setup

### .env.example

```bash
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/taskflow

# Authentication
NEXTAUTH_SECRET=your-secret-here
NEXTAUTH_URL=http://localhost:3000

# API Keys
STRIPE_SECRET_KEY=sk_test_...
SENDGRID_API_KEY=SG....

# Feature Flags
ENABLE_BETA_FEATURES=false
```

### .gitignore

```
# Dependencies
node_modules/
/.pnp
.pnp.js

# Testing
/coverage

# Next.js
/.next/
/out/
/build

# Production
/dist

# Misc
.DS_Store
*.pem

# Debug
npm-debug.log*
yarn-debug.log*

# Local env files
.env
.env*.local

# IDE
.vscode/
.idea/
*.swp
*.swo

# Claude Code (optional - you may want to commit some)
# .claude/settings.json  # Keep this private if has secrets
```

---

## Quick Start for This Project

```bash
# 1. Clone repository
git clone https://github.com/you/taskflow.git
cd taskflow

# 2. Install dependencies
npm install

# 3. Setup environment
cp .env.example .env
# Edit .env with your values

# 4. Setup database
npx prisma migrate dev
npx prisma db seed

# 5. Start development
npm run dev

# 6. Start Claude Code
claude
```

---

## Claude Code Workflow for This Project

### Starting Work

```bash
# 1. Feature branch
git checkout -b feature/task-attachments

# 2. Start Claude
claude

# 3. First prompt
> I need to add file attachments to tasks. Create a plan that includes:
> - Database schema changes
> - API endpoints for upload/download
> - Frontend components
> - S3 integration
```

### During Development

```bash
# Tests in background
> @test-agent Watch tests while I work

# Implement incrementally
> Implement the database schema first
/rewind  # Checkpoint

> Now implement the upload API
/rewind  # Checkpoint

> Now add the frontend component
```

### Before Committing

```bash
# Security check
> @security-agent Audit the file upload feature

# Code review
> @code-reviewer Review all changes for this feature

# Full test run
> @test-agent Run full test suite with coverage

# Documentation
> @docs-agent Document the new attachment API
```

---

## Team Conventions

### Branch Naming
- `feature/description` - New features
- `bugfix/description` - Bug fixes
- `hotfix/description` - Critical fixes
- `refactor/description` - Code refactoring

### Commit Messages
```
feat: add file attachments to tasks
fix: resolve upload timeout issue
docs: document attachment API
refactor: simplify auth middleware
test: add e2e tests for attachments
```

### Pull Request Process
1. Create feature branch
2. Implement with tests
3. Run full CI locally
4. Create PR with description
5. Address review comments
6. Merge after approval

---

## Directory Purpose Guide

### /.claude/
**Purpose**: Claude Code configuration and extensions  
**Commit**: Yes (helps whole team)  
**Contains**: CLAUDE.md, commands, agents, skills

### /src/app/
**Purpose**: Next.js pages and API routes  
**Pattern**: File-system based routing  
**Note**: Use route groups () for organization

### /src/components/
**Purpose**: React components  
**Organization**:
- ui/ - Base components (buttons, inputs)
- features/ - Feature components (auth, dashboard)
- layouts/ - Page layouts

### /src/lib/
**Purpose**: Shared utilities and business logic  
**Note**: Framework-agnostic when possible

### /src/hooks/
**Purpose**: Custom React hooks  
**Pattern**: Start with "use" prefix

### /src/types/
**Purpose**: TypeScript type definitions  
**Pattern**: One file per domain (User.types.ts)

### /prisma/
**Purpose**: Database schema and migrations  
**Note**: Never edit migrations after applying

### /tests/
**Purpose**: All test files  
**Organization**: Mirror src/ structure

### /docs/
**Purpose**: Project documentation  
**Target**: Developers (technical docs)

---

## Common Workflows

### Creating a New Feature

```bash
# 1. Branch
git checkout -b feature/notifications

# 2. Plan in Claude
claude
> Create a plan for push notifications

# 3. Database first
> Implement notification schema
npx prisma migrate dev --name add_notifications

# 4. API
> Create notification API endpoints

# 5. Frontend
> Create notification UI components

# 6. Test
> @test-agent Test notification feature

# 7. Review
> @code-reviewer Review all changes

# 8. Commit
git add .
git commit -m "feat: add push notifications"
```

### Fixing a Bug

```bash
# 1. Branch
git checkout -b bugfix/login-redirect

# 2. Reproduce
claude
> Help me reproduce the login redirect bug

# 3. Write test
> Create a failing test that reproduces this bug

# 4. Fix
> Fix the bug while keeping tests passing

# 5. Verify
> @test-agent Run all tests including the new one

# 6. Commit
git commit -m "fix: resolve login redirect issue"
```

### Refactoring

```bash
# 1. Tests first
> @test-agent Ensure >80% coverage on auth module

# 2. Refactor
> @refactor-agent Refactor auth module to reduce complexity

# 3. Verify
> @test-agent Ensure all tests still pass

# 4. Performance
> @performance-agent Compare before/after performance
```

---

## Best Practices Checklist

### Project Setup
- [ ] CLAUDE.md is comprehensive
- [ ] Custom commands for repetitive tasks
- [ ] Sub-agents for specialized work
- [ ] Settings.json configured
- [ ] .gitignore includes .env

### Development
- [ ] Feature branches always
- [ ] Tests before/during implementation
- [ ] Checkpoints at critical points
- [ ] Clear context between features
- [ ] Monitor context usage

### Code Quality
- [ ] Follow project patterns
- [ ] Type safety (no 'any')
- [ ] Error handling
- [ ] Tests > 80% coverage
- [ ] No hardcoded secrets

### Team Collaboration
- [ ] Commit .claude/ configuration
- [ ] Clear commit messages
- [ ] PR descriptions
- [ ] Code reviews
- [ ] Documentation updates

---

**This structure scales from small projects to large enterprise applications!**
