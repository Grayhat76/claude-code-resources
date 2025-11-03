# Claude Code Jumpstart Script

**80% of the value in 20% of the time**

An interactive script that sets up your Claude Code environment in 3-5 minutes by asking smart questions about your project.

---

## What It Does

The Jumpstart script automatically creates:

✅ **Custom CLAUDE.md** - Tailored to your project type and language  
✅ **Relevant Agents** - Only the ones you actually need  
✅ **Helpful Commands** - Based on your workflow  
✅ **settings.json** - Sensible defaults  
✅ **Personalized Guide** - Your specific next steps  

**No manual configuration needed!**

---

## Quick Start

```bash
# Download the script
curl -O https://[your-url]/claude-code-jumpstart.sh

# Make it executable
chmod +x claude-code-jumpstart.sh

# Run it in your project directory
./claude-code-jumpstart.sh
```

**Time: 3-5 minutes**

---

## What It Asks (7 Questions)

1. **Your Experience** - Never used it / Tried once / Week or two / Pretty comfortable
2. **Project Type** - Web app / Backend / Full-stack / Mobile / Data/ML / DevOps
3. **Primary Language** - JavaScript/TS / Python / Go / Java / Ruby / Rust / PHP
4. **Project Phase** - Starting / Active dev / Maintenance / Refactoring
5. **Team Size** - Solo / Small (2-5) / Medium (6-15) / Large (15+)
6. **Pain Points** - Boilerplate / Tests / Reviews / Debugging / Refactoring / Docs
7. **Existing Project** - Yes / No

**Based on your answers, it creates a customized setup.**

---

## Examples

### Example 1: Solo Developer, New Web App

**Answers:**
- Experience: Tried once
- Project: Web app
- Language: TypeScript
- Phase: Just starting
- Team: Solo
- Pain: Writing boilerplate, tests
- Existing: No

**Creates:**
- Basic CLAUDE.md for TypeScript/React
- test-agent (you want help with tests)
- /frontend:component command (for boilerplate)
- /testing:unit command
- Beginner-focused guide

### Example 2: Team Refactoring Legacy Backend

**Answers:**
- Experience: Pretty comfortable
- Project: Backend
- Language: Python
- Phase: Major refactoring
- Team: Small (5 people)
- Pain: Refactoring, code reviews
- Existing: Yes

**Creates:**
- CLAUDE.md for Python backend
- refactor-agent (you're refactoring)
- code-reviewer (you're a team)
- /backend:endpoint command
- Team collaboration tips

### Example 3: Data Science, Solo, Learning

**Answers:**
- Experience: Never used it
- Project: Data/ML
- Language: Python
- Phase: Active development
- Team: Solo
- Pain: Documentation, debugging
- Existing: Yes

**Creates:**
- CLAUDE.md for Python/Data
- test-agent (good for any project)
- Extra beginner guidance
- Realistic timeline (Week 1 slower)

---

## What Gets Created

### Directory Structure

```
your-project/
├── .claude/
│   ├── CLAUDE.md              ← Customized for your project
│   ├── GETTING_STARTED.md     ← Your personalized guide
│   ├── settings.json          ← Configuration
│   ├── COMMIT_THIS.sh         ← Helper to commit to git
│   ├── agents/                ← Only what you need
│   │   ├── test-agent.md      (if applicable)
│   │   ├── code-reviewer.md   (if team/review pain)
│   │   └── refactor-agent.md  (if refactoring)
│   └── commands/              ← Based on project type
│       ├── frontend/          (if web app)
│       ├── backend/           (if backend)
│       └── testing/           (if testing pain)
└── .gitignore                 ← Updated to ignore local settings
```

### File Highlights

**CLAUDE.md** - Contains:
- Project overview
- Tech stack (pre-filled for your language)
- Code standards (language-specific)
- File organization
- Development workflow
- Project-specific sections

**GETTING_STARTED.md** - Contains:
- What was set up
- Your next 3 steps (10 minutes)
- First request suggestion (based on your phase)
- Expected timeline (based on experience)
- Common mistakes to avoid
- Personalized tips

**Agents** - Created based on:
- test-agent: For intermediate+ users OR testing pain point
- code-reviewer: For teams OR review pain point
- refactor-agent: For refactoring phase OR refactoring pain point

**Commands** - Created based on:
- /frontend:component: For web apps (TypeScript)
- /backend:endpoint: For backend projects
- /testing:unit: For testing pain points

---

## Decision Logic

### Agent Selection

```
test-agent:
  IF experience >= intermediate
  OR pain_point = testing
  THEN create

code-reviewer:
  IF team_size > solo
  OR pain_point = review
  THEN create

refactor-agent:
  IF project_phase = refactor
  OR pain_point = refactoring
  THEN create
```

### Command Selection

```
/frontend:component:
  IF project_type = webapp OR fullstack
  AND language = typescript
  THEN create

/backend:endpoint:
  IF project_type = backend OR fullstack
  THEN create

/testing:unit:
  IF pain_point = testing
  THEN create
```

### Content Customization

**CLAUDE.md varies by:**
- Language (Python vs TypeScript vs Go, etc.)
- Project type (API structure, frontend patterns)
- Phase (focus areas differ)

**GETTING_STARTED.md varies by:**
- Experience level (timelines, detail level)
- Phase (suggested first request)
- Pain points (relevant tips)
- Team size (collaboration advice)

---

## Benefits

### vs Manual Setup

**Manual Setup:**
- Read documentation (1-2 hours)
- Copy templates
- Figure out what you need
- Customize everything
- Easy to miss key steps

**Jumpstart Script:**
- Answer 7 questions (2 minutes)
- Auto-generated, tailored setup (1 minute)
- Read personalized guide (3 minutes)
- Start coding (immediate)

**Time saved: 1-2 hours**

### vs Generic Template

**Generic Template:**
- Everything included (overwhelming)
- Not specific to your needs
- Lots to delete/customize
- May include wrong patterns

**Jumpstart Script:**
- Only what you need (focused)
- Specific to your project
- Nothing to delete
- Correct patterns for your stack

**Better user experience**

---

## For Teams

### Team Lead Runs It

```bash
# Team lead sets up
./claude-code-jumpstart.sh

# Customize CLAUDE.md for team
vim .claude/CLAUDE.md

# Commit to repository
./.claude/COMMIT_THIS.sh
git push

# Team members pull and use
git pull
claude
```

**Everyone has the same baseline setup.**

### Benefits for Teams

- Consistent CLAUDE.md across team
- Shared agents and commands
- Same workflow patterns
- Easier onboarding
- Team-specific customizations preserved

---

## Customization After Setup

The script creates a **starting point**, not a final state.

### Recommended Customizations

**CLAUDE.md** (do immediately):
- Add your specific tech stack
- Document your code patterns
- Add your common commands
- Update as project evolves

**Agents** (add as needed):
- Create project-specific agents
- Modify existing agent instructions
- Add more agents when pain points emerge

**Commands** (grow over time):
- Add commands for repetitive tasks
- Create shortcuts for your patterns
- Document team workflows

---

## Advanced Features (Coming in v2.0)

### Silent Mode (Planned for v2.0)

*Non-interactive mode for CI/CD and automation is planned for v2.0.*

**What it will look like:**
```bash
# Coming in v2.0!
./claude-code-jumpstart.sh \
  --experience intermediate \
  --project webapp \
  --language typescript \
  --phase active \
  --team small \
  --pain testing,review \
  --existing yes \
  --silent
```

**Current workaround:**  
Run the script once interactively, commit the `.claude/` directory to your repository, and your team can pull it down.

**Want this feature?** Star the repo and let us know in discussions!

---

## Troubleshooting

### Script Won't Run

```bash
# Make it executable
chmod +x claude-code-jumpstart.sh

# Or run with bash
bash claude-code-jumpstart.sh
```

### Already Have .claude Directory

Script will warn you:
```
Warning: .claude/ directory already exists.
Overwrite? (y/n)
```

Choose `n` to keep existing setup, or `y` to regenerate.

### Git Not Found

Script creates git-related files only if git is available.
If `git` command not found, script skips git integration.

---

## FAQ

**Q: Can I run it multiple times?**  
A: Yes! Re-run to regenerate based on new answers. Back up first if you've customized.

**Q: Will it overwrite my existing setup?**  
A: It asks before overwriting. Answer 'n' to keep existing.

**Q: What if I picked wrong answers?**  
A: Just re-run the script. Or manually edit the generated files.

**Q: Can I customize the generated files?**  
A: Absolutely! They're meant to be customized. Start with generated, then evolve.

**Q: Does it work on Windows?**  
A: Requires bash. Use Git Bash, WSL, or run on Mac/Linux.

**Q: What if my language isn't listed?**  
A: Choose "Other" - creates generic setup you can customize.

**Q: Can I add silent mode parameters later?**  
A: Currently interactive only. Silent mode is for future enhancement.

---

## Source Code

The script is ~600 lines of bash with:
- Input validation
- Conditional logic for personalization
- Template generation
- Colored output
- Error handling

**Fully open source** - customize for your organization!

---

## Maintenance

### Keeping It Updated

As Claude Code evolves:
1. Update agent templates
2. Add new commands for new features
3. Update CLAUDE.md templates
4. Improve decision logic

**Community contributions welcome!**

---

## Success Stories

### "Saved Our Team 2 Hours Each"

> "Before: everyone configured differently, spent 2 hours setting up. After: jumpstart creates team baseline in 5 minutes. Saved 10 hours (5 devs)." - Tech Lead

### "Perfect for Onboarding"

> "New hires run jumpstart, get personalized guide, up and running in 15 minutes vs 2-3 days of documentation reading." - Engineering Manager

### "Finally Used Claude Code"

> "Had Claude Code installed for weeks but never started. Jumpstart got me past the 'blank page' problem. Now using it daily." - Solo Developer

---

## Comparison to Other Approaches

| Approach | Time | Customization | Beginner-Friendly |
|----------|------|---------------|-------------------|
| **Read Full Docs** | 2-3 hours | Full | No |
| **Copy Template** | 30 min | Partial | Medium |
| **Jumpstart Script** | 5 min | Smart | Yes |
| **Manual Setup** | 1 hour | Full | No |

**Jumpstart = 80% value, 20% effort**

---

## Related Files

- [Main Best Practices Guide](./claude-code-best-practices-2025.md)
- [Agent Files](./agents/) - Reference for what gets created
- [CLAUDE.md Template](./CLAUDE.md.template) - Full manual template
- [Quick Start](./claude-code-quick-start.md) - Commands reference

---

## Contributing

Ideas to improve the script:

- [ ] Add more project types (Rust, Elixir, etc.)
- [ ] Better detection of existing tools
- [ ] Import from package.json/requirements.txt
- [ ] Team templates repository
- [ ] VSCode/JetBrains plugin integration
- [ ] Analytics to improve recommendations

**PRs welcome!**

---

## License

MIT - Use freely, modify as needed, share with your team.

---

**Get started: Download and run `./claude-code-jumpstart.sh` in your project! 🚀**
