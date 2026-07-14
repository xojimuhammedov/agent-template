# AI-Agent-Friendly Starter Template

This repository is a ready-to-use boilerplate/template for setting up an AI-agent-friendly developer ecosystem (documentation, lintable rules, and repeatable workflow skills) for any project.

You can clone this repository, push it to your own GitHub, or merge its files directly into your existing projects.

## Directory Structure Overview
```
├── AGENTS.md                          # Main agent entry point & Golden Rules
├── CODEX.md                          # Codex entry point (redirects to AGENTS.md)
├── .gitignore                         # Configured git ignore mappings
├── package.json                       # Scripts for sync & linting
├── .agents/
│   └── rules/                         # Canonical MDC rulecards (git-tracked)
│       ├── README.md                  # Rules directory index
│       ├── read-agents-md.mdc         # Directs agents to AGENTS.md
│       ├── doc-maintenance.mdc        # Enforces up-to-date documentation
│       └── typescript-best-practices.mdc  # Example TS rules
├── skills-contrib/                    # Canonical step-by-step workflow guidelines
│   └── create-pr/
│       └── SKILL.md                   # PR creation workflow skill
├── docs/                              # Deep-dive architecture and design specs
│   ├── README.md                      # Index of all project documentation
│   └── architecture/
│       └── overview.md                # Architectural design layout overview
└── scripts/
    └── sync-agent-rules.mjs           # CLI tool that generates symlinks for IDEs
```

## How to Implement in Your Project

### Option A: Use as a GitHub Template (For new projects)
1. Use this repository as a template on GitHub to create a new repo.
2. Run `npm install` or `pnpm install` to set up the rules symlink synchronization automatically.
3. Tailor `AGENTS.md` and the rules under `.agents/rules/` to fit your project.

### Option B: Merge into an Existing Project
Copy the files into your current workspace:
```bash
# Copy agents config, scripts, rules, skills, and docs
cp -R .agents skills-contrib docs scripts AGENTS.md CLAUDE.md /path/to/your/project/
```
Then, update your project's `.gitignore` and `package.json` to match the configuration templates provided in this repo.

## Synchronizing Rules
Agent harnesses (like Cursor and Claude Code) expect rules at `.cursor/rules` and `.claude/rules`. To keep rules centralized in one place (`.agents/rules/`) without duplication:
```bash
# Generate the IDE symlinks automatically
pnpm rules:sync

# Check if rules are in sync (runs on CI)
pnpm lint:rules:symlinks
```
These symlinks are gitignored to keep the repository history clean.
