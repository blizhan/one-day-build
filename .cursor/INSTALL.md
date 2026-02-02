# Installation Guide for Cursor

## Quick Install

Copy and paste this into Cursor:

```
Install the one-day-build skill from https://github.com/blizhan/one-day-build
```

The AI will automatically fetch and set up the skill for you.

## Manual Installation

Cursor supports skills similar to OpenCode and Claude Code.

### Step 1: Download the Repository

```bash
git clone https://github.com/blizhan/one-day-build.git
cd one-day-build
```

### Step 2: Install the Skill

**Global Installation (Recommended):**
```bash
# Copy to Cursor global skills directory
cp -r skill ~/.cursor/skills/one-day-build
```

**Project-Specific Installation:**
```bash
# Copy to your project
mkdir -p .cursor/skills
cp -r skill .cursor/skills/one-day-build
```

### Step 3: Verify Installation

The skill directory should look like:

```
~/.cursor/skills/one-day-build/
├── SKILL.md
└── references/
    └── phases.md
```

## Quick Download (without git)

```bash
curl -L https://github.com/blizhan/one-day-build/archive/refs/heads/main.zip -o one-day-build.zip
unzip one-day-build.zip
cp -r one-day-build-main/skill ~/.cursor/skills/one-day-build
rm -rf one-day-build.zip one-day-build-main
```

## Using the Skill

Once installed, the skill automatically triggers when you say:

- "Let's build a [project] from scratch"
- "Help me architect a [system]"
- "Let's pair program on [idea]"

**Example prompts:**
- "Let's build a REST API for task management from scratch"
- "Help me architect a data pipeline for ETL"
- "Let's pair program on a browser extension"

Cursor's AI will follow the 6-phase workflow:

| Phase | Duration | Focus |
|-------|----------|-------|
| 1. Intent | 30 min | Requirements |
| 2. Architecture | 60-90 min | Design |
| 3. Foundation | 2-3 hrs | Implementation |
| 4. Refinement | 1-2 hrs | Polish |
| 5. Testing | 60 min | Coverage |
| 6. Docs | 30 min | Documentation |

## What You'll Build

In 5-8 hours:
- Working feature with real data
- Clean architecture (>80% test coverage)
- Complete docs (AGENTS.md, README, TODO)
- Foundation ready to extend

## Troubleshooting

**Skill not loading?**

1. Check the directory exists:
   ```bash
   ls -la ~/.cursor/skills/one-day-build
   ```

2. Verify SKILL.md is present:
   ```bash
   cat ~/.cursor/skills/one-day-build/SKILL.md | head -n 5
   ```

3. Restart Cursor

4. Try explicitly mentioning the skill:
   ```
   Use the one-day-build skill to help me build X
   ```

**Still having issues?**

Open an issue: https://github.com/blizhan/one-day-build/issues

## Alternative: Using .cursorrules

If you prefer the traditional `.cursorrules` approach:

```bash
cd /path/to/your/project
curl -L https://raw.githubusercontent.com/blizhan/one-day-build/main/skill/SKILL.md -o .cursorrules
```

Note: Skills directory is recommended for better organization and reusability across projects.

## Uninstalling

**Global:**
```bash
rm -rf ~/.cursor/skills/one-day-build
```

**Project-specific:**
```bash
rm -rf .cursor/skills/one-day-build
```
