# AlltheVibes Agent Swarm Project

## Primary Working Directory

**CRITICAL**: This is the primary repository for the AlltheVibes hackathon agent swarm project.

**Working Directory**: `/Users/gabland-msft/Library/CloudStorage/OneDrive-Microsoft/Repos/codesmash/AlltheVibes-WildHackathon`

## Repository Structure

This repository is a **git submodule** inside the parent `codesmash` repo:

```
codesmash/                           # Parent repo (gabland-msft/codesmash)
└── AlltheVibes-WildHackathon/      # THIS REPO (submodule)
    ├── .git -> ../.git/modules/AlltheVibes-WildHackathon
    ├── src/                         # Agent swarm source code
    ├── .claude/                     # Claude Code configuration
    └── ...
```

## Git Remotes

- **origin**: `https://github.com/gabland-msft/AlltheVibes-WildHackathon.git` (your fork)
- **upstream**: `https://github.com/shyamsridhar123/AlltheVibes-WildHackathon.git` (Shyam's repo)

## Workflow

### For ALL Agents (AI and Human)

**ALWAYS work in this directory:**
```bash
cd /Users/gabland-msft/Library/CloudStorage/OneDrive-Microsoft/Repos/codesmash/AlltheVibes-WildHackathon
```

**NEVER work in the parent `codesmash` directory for this project.**

### Creating PRs

All PRs must target the **upstream** repository:
- **Base**: `shyamsridhar123/AlltheVibes-WildHackathon` (main branch)
- **Head**: `gabland-msft/AlltheVibes-WildHackathon` (your feature branch)

```bash
# Create PR
gh pr create \
  --repo shyamsridhar123/AlltheVibes-WildHackathon \
  --base main \
  --head gabland-msft:feature/your-branch \
  --title "feat: amazing feature" \
  --body "Your amusing PR description for @shyamsridhar123"
```

## Common Pitfalls

❌ **WRONG**: Working in `/Users/.../codesmash/` directory
✅ **CORRECT**: Working in `/Users/.../codesmash/AlltheVibes-WildHackathon/` directory

❌ **WRONG**: PRs to `gabland-msft/codesmash`
✅ **CORRECT**: PRs to `shyamsridhar123/AlltheVibes-WildHackathon`

## Auto-Configuration

When agents start, they should:
1. Change to this directory first
2. Verify git remote points to correct upstream
3. Pull latest changes from upstream
4. Create feature branch from main
