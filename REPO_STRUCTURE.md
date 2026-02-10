# Repository Structure Guide

## 🎯 The Setup

This repository (`AlltheVibes-WildHackathon`) is where the **agent swarm platform** is being built for the hackathon.

### Repository Hierarchy

```
📁 codesmash/                                    # Parent repository
│   ├── .git/                                    # Parent git directory
│   │   └── modules/
│   │       └── AlltheVibes-WildHackathon/      # Submodule git data
│   ├── .beads/                                  # Beads issue tracking (shared)
│   ├── .claude/                                 # Claude Code skills
│   │   └── skills/                              # Shared skills
│   └── AlltheVibes-WildHackathon/              # 👈 THIS IS WHERE YOU WORK!
│       ├── .git                                 # Points to parent's modules/
│       ├── .claude/
│       │   └── project.md                       # Project-specific config
│       ├── src/                                 # Agent swarm source code
│       │   ├── agents/                          # Agent implementations
│       │   ├── services/                        # Services (OpenAI, MessageBus, etc.)
│       │   ├── db/                              # Database clients (Redis, Neo4j)
│       │   └── types/                           # TypeScript types
│       ├── README.md                            # This project's README
│       └── REPO_STRUCTURE.md                    # This file
```

## 🔧 Git Configuration

### Remotes

When you run `git remote -v` inside `AlltheVibes-WildHackathon/`:

```
origin    https://github.com/gabland-msft/AlltheVibes-WildHackathon.git (fetch)
origin    https://github.com/gabland-msft/AlltheVibes-WildHackathon.git (push)
upstream  https://github.com/shyamsridhar123/AlltheVibes-WildHackathon.git (fetch)
upstream  https://github.com/shyamsridhar123/AlltheVibes-WildHackathon.git (push)
```

- **origin** = Your fork (where you push your branches)
- **upstream** = Shyam's repository (where PRs are created)

### Why This Structure?

1. **codesmash** is your personal agent swarm experimentation repo
2. **AlltheVibes-WildHackathon** is the hackathon project (team collaboration)
3. They're linked as submodule so you can work on both
4. PRs for hackathon work go to Shyam's repo, not yours

## 📋 Workflow for Agents

### Starting Work

```bash
# 1. Navigate to the correct directory
cd /Users/gabland-msft/Library/CloudStorage/OneDrive-Microsoft/Repos/codesmash/AlltheVibes-WildHackathon

# 2. Ensure you're on main and up-to-date
git checkout main
git pull upstream main
git push origin main  # Sync your fork

# 3. Create feature branch
git checkout -b feature/your-awesome-feature

# 4. Claim work in beads (if using beads)
bd update <issue-id> --status=in_progress
```

### Completing Work

```bash
# 1. Commit your changes
git add .
git commit -m "feat: your awesome feature

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"

# 2. Push to YOUR fork (origin)
git push -u origin feature/your-awesome-feature

# 3. Create PR to UPSTREAM (Shyam's repo)
gh pr create \
  --repo shyamsridhar123/AlltheVibes-WildHackathon \
  --base main \
  --head gabland-msft:feature/your-awesome-feature \
  --title "feat: ..." \
  --body "Amusing description for @shyamsridhar123"

# 4. Close beads issue
bd close <issue-id>
bd sync
```

## 🚨 CRITICAL: Directory Awareness

### For AI Agents

**ALWAYS verify you're in the correct directory before starting work:**

```bash
pwd
# Expected: /Users/gabland-msft/Library/CloudStorage/OneDrive-Microsoft/Repos/codesmash/AlltheVibes-WildHackathon

git remote -v | grep upstream
# Expected: upstream https://github.com/shyamsridhar123/AlltheVibes-WildHackathon.git
```

If you're not in the right place, **STOP** and change directory first.

### Common Mistakes

| ❌ Wrong | ✅ Correct |
|---------|-----------|
| Working in `/path/to/codesmash/` | Working in `/path/to/codesmash/AlltheVibes-WildHackathon/` |
| PRs to `gabland-msft/codesmash` | PRs to `shyamsridhar123/AlltheVibes-WildHackathon` |
| Using `origin` for PRs | Using `upstream` for PRs |
| Forgetting to pull from upstream | Always pull upstream first |

## 🔄 Syncing with Upstream

Regularly sync your fork with Shyam's repository:

```bash
cd /Users/gabland-msft/Library/CloudStorage/OneDrive-Microsoft/Repos/codesmash/AlltheVibes-WildHackathon

# Fetch latest from upstream
git fetch upstream

# Update your main branch
git checkout main
git merge upstream/main
git push origin main

# Rebase your feature branch if needed
git checkout feature/your-branch
git rebase main
```

## 📦 Dependencies & Build

This project uses:
- **TypeScript** for type-safe development
- **Node.js** for runtime
- **Vitest** for testing
- **Docker Compose** for infrastructure (Redis, Neo4j)

```bash
# Install dependencies
npm install

# Run tests
npm test

# Build
npm run build

# Start infrastructure
docker-compose up -d
```

## 🎓 Learning Resources

- **AGENTS.md** - Branch + PR workflow (MANDATORY reading!)
- **README.md** - Project overview and vision
- **TEAM_SETUP.md** - Team collaboration guide
- **.claude/project.md** - Claude Code configuration

## 🆘 Troubleshooting

### "I'm in the wrong directory!"

```bash
# Quick fix
cd /Users/gabland-msft/Library/CloudStorage/OneDrive-Microsoft/Repos/codesmash/AlltheVibes-WildHackathon
```

### "My PR went to the wrong repo!"

Close the PR and recreate with correct upstream:
```bash
gh pr close <wrong-pr-number>
gh pr create --repo shyamsridhar123/AlltheVibes-WildHackathon ...
```

### "I can't push to upstream!"

You should **never** push directly to upstream. Always:
1. Push to origin (your fork)
2. Create PR from origin to upstream

---

**Remember**: The correct working directory is your anchor. When in doubt, verify with `pwd` and `git remote -v`! ⚓
