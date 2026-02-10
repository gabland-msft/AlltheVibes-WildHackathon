# 🚀 CODESMASH - AGENTS.MD

**Building a self-organizing agent swarm.** Fast iteration. **ALWAYS branch + PR.** No exceptions.

---

## 🚨 MANDATORY WORKFLOW: BRANCH + PR

### ⚠️ **CRITICAL - READ THIS FIRST**

**EVERY piece of work MUST follow this workflow:**

```bash
# 1. ALWAYS start with pull and create a branch
git checkout main
git pull --rebase origin main
git checkout -b feature/your-feature-name

# 2. Claim work in beads
bd update <issue-id> --status=in_progress

# 3. Build the feature
# ... code, test, iterate ...

# 4. Commit your work
git add .
git commit -m "feat: descriptive commit message

Extended description if needed.

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"

# 5. Sync beads
bd sync

# 6. Push branch
git push -u origin feature/your-feature-name

# 7. Create PR (make it amusing for @shyamsridhar123!)
gh pr create --title "feat: ..." --body "..."

# 8. After PR is merged, close the issue
bd close <issue-id>
bd sync
```

### **Golden Rules - NO EXCEPTIONS:**

1. 🌿 **ALWAYS CREATE A BRANCH** - Never commit directly to main
2. 📝 **ALWAYS CREATE A PR** - Every change goes through pull request
3. 🎭 **MAKE PR NOTES AMUSING** - Entertain @shyamsridhar123
4. 🔄 **PULL BEFORE BRANCHING** - Start with latest main
5. 📦 **CLOSE BEADS ISSUES** - Update issue tracking when done

### **Why Branch + PR?**

- ✅ Code review and quality control
- ✅ Clear history of what changed and why
- ✅ Prevents breaking main branch
- ✅ Allows parallel development
- ✅ GitHub tracks progress via PRs
- ✅ Enables continuous integration checks

### **FAST ITERATION CYCLE:**

Work in short cycles, but ALWAYS on a branch:

```bash
# Cycle 1: Setup (30 seconds)
git checkout main && git pull --rebase
git checkout -b feature/awesome-thing
bd update codesmash-xxx --status=in_progress

# Cycle 2: Build (5-10 minutes)
# ... implement feature ...
npm test  # Always test!

# Cycle 3: Ship (1-2 minutes)
git add . && git commit -m "feat: awesome thing"
bd sync
git push -u origin feature/awesome-thing
gh pr create --title "..." --body "..."

# Cycle 4: Close (30 seconds, after PR merges)
bd close codesmash-xxx && bd sync
```

**Target**: Branch → Code → PR in under 15 minutes. Speed matters, but quality and process matter more.

---

## 🔐 REPOSITORY ACCESS (Microsoft EMU Users)

### **CRITICAL: EMU Account Limitations**

If you're using a Microsoft Enterprise Managed User account (like `gabland_microsoft`):

❌ **CANNOT** fork external repositories
❌ **CANNOT** access personal repos from work account
✅ **CAN** access repos as collaborators
✅ **CAN** access repos in Microsoft organization

### **Setup for External Repos (like AlltheVibes)**

**Step 1: Repo Owner Adds Collaborators**

Repo owner (@shyamsridhar123) must:
1. Go to repo **Settings** → **Collaborators**
2. Add team members' GitHub usernames
3. Grant **Write** access

**Step 2: Initialize Empty Repo**

```bash
# Repo owner initializes:
git clone https://github.com/shyamsridhar123/AlltheVibes-WildHackathon
cd AlltheVibes-WildHackathon
echo "# Project Name" > README.md
git add README.md
git commit -m "Initial commit"
git push origin main
```

**Step 3: Team Members Clone**

```bash
# After being added as collaborator:
cd /path/to/codesmash/src
git clone https://github.com/shyamsridhar123/AlltheVibes-WildHackathon allthevibes
cd allthevibes
# Start coding!
```

### **Alternative: Transfer to Microsoft Org**

For all-Microsoft teams, transfer repo to your org:
1. Repo Settings → Danger Zone → Transfer ownership
2. Transfer to Microsoft GitHub organization
3. All EMU users automatically have access

---

## 🎯 SPEED PATTERNS FOR CLAUDE CODE

### **Parallel Everything**

When multiple independent tasks exist:
```bash
# Create multiple issues at once using parallel subagents
# Example: "Create 5 feature issues for X, Y, Z in parallel"
```

Use Task tool with multiple agents running simultaneously. Don't wait.

### **Fast Feature Development**

1. **Pick work**: `bd ready` → grab lowest ID
2. **Claim it**: `bd update <id> --status=in_progress`
3. **Code fast**: Use subagents, parallel tools, no overthinking
4. **Commit early**: Don't wait for perfection
5. **Close fast**: `bd close <id>`
6. **PUSH**: Always push within 5 minutes

### **Quick Issue Creation**

```bash
# Create feature
bd create --title="Add login button" --type=feature --priority=2

# Create task (smaller scope)
bd create --title="Write test for login" --type=task --priority=2

# Create bug
bd create --title="Fix button alignment" --type=bug --priority=1
```

**Priority Scale**: 0=critical, 1=high, 2=medium, 3=low, 4=backlog

### **Dependencies (When Needed)**

```bash
# Feature blocks task (task depends on feature)
bd dep add codesmash-yyy codesmash-xxx  # yyy depends on xxx
```

Only use for true blockers. Otherwise, work in parallel!

---

## 🛠️ AVAILABLE SKILLS

Your `.claude/skills/` directory contains:

- **bd**: Beads issue management commands
- **git**: Git workflow helpers
- **subagent**: Parallel agent management
- **tech-lead**: Architecture & planning
- **creating-skills**: Meta - create new skills
- **mcp-dev**: MCP development tools
- **msr-search**: Search utilities
- **testing-mcp**: Testing helpers

**Use skills**: Just reference them like `/bd`, `/git`, etc. in conversation.

---

## 💡 CODESMASH BEST PRACTICES

### **DO:**
✅ Commit every 5 minutes, no matter what
✅ Work on multiple features in parallel
✅ Use beads for tracking discovered work
✅ Push frequently to stay synced
✅ Close issues immediately when done
✅ Use WIP commits if not finished
✅ Keep commits small and atomic
✅ Use parallel subagents for independent tasks

### **DON'T:**
❌ Wait for perfection before committing
❌ Hoard changes locally
❌ Block others by keeping branches
❌ Overthink architecture
❌ Write extensive documentation during codesmash
❌ Refactor during active development
❌ Create complex dependency chains

---

## 🎪 MULTIPLAYER COORDINATION

### **Merge Conflicts (They WILL Happen)**

```bash
# When pull fails with conflicts:
git pull --rebase
# Fix conflicts in editor
git add .
git rebase --continue
git push
```

**Stay calm**. Conflicts are normal in codesmash. Fix fast, move on.

### **Claim Your Territory**

```bash
# Before starting work on a file/feature:
bd create --title="Working on auth module" --type=task --priority=1
bd update <id> --status=in_progress
# This signals to others: "I'm here!"
```

### **Sync Status**

```bash
# Check what others are working on:
bd list --status=in_progress
bd stats  # Overview of project health
```

---

## 🏃 SPRINT MODES

### **Solo Sprint** (You alone for 30 min)
- Create 6-8 issues (one per 5-min cycle)
- Work through them sequentially
- Close and push each cycle

### **Team Sprint** (Multiple devs)
- Create issues collaboratively
- Use `bd ready` to find available work
- Coordinate via beads status
- Accept merge conflicts as life

### **Feature Rush** (Build one big thing fast)
- Break into small tasks
- Set up dependency chain
- Multiple people work on unblocked tasks
- Integrate frequently

---

## 🚨 EMERGENCY PATTERNS

### **"I Broke Main!"**

```bash
# Immediately fix or revert:
git revert HEAD  # If last commit is bad
# OR
git reset --hard HEAD~1  # If not pushed yet
git push --force  # Only if nobody pulled

# Create issue to fix properly:
bd create --title="Fix broken feature X" --type=bug --priority=0
```

### **"Massive Merge Conflict!"**

```bash
# Nuclear option (use sparingly):
git fetch origin
git reset --hard origin/main
# Start over with your changes
```

### **"Out of Sync!"**

```bash
bd sync --status  # Check sync state
bd sync          # Force sync
git pull --rebase
git push
```

---

## 📊 MONITORING PROGRESS

```bash
# Quick health check:
bd stats

# What's ready to work on?
bd ready

# What am I working on?
bd list --status=in_progress

# What's blocked?
bd blocked

# Everything open:
bd list --status=open
```

---

## 🎓 COMMIT MESSAGE SHORTCUTS

Keep them FAST but descriptive:

```
feat: add login button
fix: button alignment
test: add auth tests
docs: update readme
refactor: cleanup utils
wip: login flow (incomplete)
chore: update deps
```

**Format**: `type: description` (lowercase, no period)

---

## 🏁 END OF CODESMASH

When the event ends:

```bash
# 1. Close all your in-progress work
bd list --status=in_progress
bd close <id1> <id2> <id3> ...

# 2. Create issues for incomplete work
bd create --title="TODO: finish X" --type=task --priority=3

# 3. Final sync
bd sync
git pull --rebase
git push

# 4. Victory! 🎉
bd stats
```

---

## 🤖 CLAUDE CODE SPECIFIC TIPS

### **For Claude:**

When user says "work on next feature":
1. Run `bd ready`
2. Pick lowest ID
3. Run `bd show <id>` to understand it
4. Run `bd update <id> --status=in_progress`
5. Implement quickly
6. Commit & push within 5 min
7. Run `bd close <id>`
8. Repeat!

### **Creating Multiple Issues:**

User: "Create 5 features for auth system"

**You should:**
- Use parallel subagents or Task tool to create all 5 at once
- Set appropriate dependencies
- Return list of created IDs

### **Parallel Development:**

When multiple files/features are independent:
- Launch multiple Task tool agents in parallel
- Each agent works on separate issue
- Merge all changes together
- Single commit with all changes

---

## 📚 QUICK REFERENCE

| Command | Purpose |
|---------|---------|
| `bd ready` | Find work to do |
| `bd show <id>` | View issue details |
| `bd update <id> --status=in_progress` | Claim work |
| `bd close <id>` | Complete work |
| `bd create --title="..." --type=feature --priority=2` | New issue |
| `bd sync` | Sync beads with git |
| `bd stats` | Project overview |
| `bd blocked` | See blocked issues |
| `git add . && git commit -m "..."` | Commit changes |
| `git pull --rebase && git push` | Sync with main |

---

## 🎯 SUCCESS METRICS

- **Commits per hour**: Aim for 12+ (one every 5 min)
- **Issues closed**: As many as possible
- **Merge conflicts resolved**: Badge of honor
- **Time to push**: < 5 minutes always
- **Fun level**: Maximum! 🚀

---

**Remember**: Perfect is the enemy of done. Ship it! 🚢
