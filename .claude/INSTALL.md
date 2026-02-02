# Installation Guide for Claude Code

## Quick Install

Copy and paste this into Claude Code:

```
Install the one-day-build skill from https://github.com/blizhan/one-day-build
```

The AI will automatically:
1. Clone the repository
2. Copy the skill to `~/.claude/skills/`
3. Verify the installation

## Manual Installation

### Step 1: Download the Repository

```bash
git clone https://github.com/blizhan/one-day-build.git
cd one-day-build
```

### Step 2: Install the Skill

```bash
# Copy to Claude skills directory
cp -r skill ~/.claude/skills/one-day-build
```

### Step 3: Verify Installation

The skill directory should look like:

```
~/.claude/skills/one-day-build/
├── SKILL.md
└── references/
    └── phases.md
```

Start Claude Code and run:

```
List available skills
```

You should see `one-day-build` in the list.

## Quick Download (without git)

```bash
curl -L https://github.com/blizhan/one-day-build/archive/refs/heads/main.zip -o one-day-build.zip
unzip one-day-build.zip
cp -r one-day-build-main/skill ~/.claude/skills/one-day-build
rm -rf one-day-build.zip one-day-build-main
```

## Using the Skill

Once installed, the skill automatically triggers when you say:

- "Let's build a [project] from scratch"
- "Help me architect a [system]"
- "Let's pair program on [idea]"

Examples:
- "Let's build a CLI tool for managing todos"
- "Help me architect a microservice for payments"
- "Let's pair program on a Chrome extension for bookmarks"

The AI will guide you through 6 phases over 5-8 hours:

| Phase | Duration | What You'll Do |
|-------|----------|----------------|
| 1. Intent | 30 min | Clarify requirements |
| 2. Architecture | 60-90 min | Design system |
| 3. Foundation | 2-3 hrs | Build first feature |
| 4. Refinement | 1-2 hrs | Fix bugs, refactor |
| 5. Testing | 60 min | Test infrastructure |
| 6. Docs | 30 min | Documentation |

## What You'll Get

After one session:
- ✓ One complete feature working
- ✓ Clean architecture with >80% test coverage
- ✓ Complete documentation (AGENTS.md, README, TODO)
- ✓ Foundation ready for extension

## Troubleshooting

**Skill not loading?**

1. Verify the directory:
   ```bash
   ls -la ~/.claude/skills/one-day-build
   ```

2. Check SKILL.md exists:
   ```bash
   cat ~/.claude/skills/one-day-build/SKILL.md | head -n 5
   ```

3. Restart Claude Code

**Still stuck?**

Open an issue: https://github.com/blizhan/one-day-build/issues

## Uninstalling

```bash
rm -rf ~/.claude/skills/one-day-build
```
