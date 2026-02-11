# Installation Guide for Codex

## Quick Install

Copy and paste this into Codex:

```
Install the one-day-build skill from https://github.com/blizhan/one-day-build
```

The AI will automatically:
1. Clone the repository
2. Copy the skill to the appropriate location
3. Verify the installation

## Manual Installation

### Step 1: Download the Repository

```bash
git clone https://github.com/blizhan/one-day-build.git
cd one-day-build
```

### Step 2: Install the Skill

```bash
# Copy to global skills directory
cp -r skill ~/.codex/skills/one-day-build
```

### Step 3: Verify Installation

The skill directory should look like:

```
~/.codex/skills/one-day-build/
├── SKILL.md
└── references/
    └── phases.md
```

## Quick Download (without git)

```bash
curl -L https://github.com/blizhan/one-day-build/archive/refs/heads/main.zip -o one-day-build.zip
unzip one-day-build.zip
cp -r one-day-build-main/skill ~/.codex/skills/one-day-build
rm -rf one-day-build.zip one-day-build-main
```

## Using the Skill

Once installed, the skill automatically triggers when you say:

- "Let's build a [project] from scratch"
- "Help me architect a [system]"
- "Let's pair program on [idea]"

Examples:
- "Let's build a CLI tool for file organization from scratch"
- "Help me architect a data pipeline for ETL"
- "Let's pair program on a browser extension"

The AI will guide you through 6 phases:
1. Intent Clarification (30 min)
2. Architecture Design (60-90 min)
3. Foundation Implementation (2-3 hrs)
4. Problem-Driven Refinement (1-2 hrs)
5. Testing Architecture (60 min)
6. Documentation Sync (30 min)

## Troubleshooting

**Skill not loading?**

1. Check the skill directory exists:
   ```bash
   ls ~/.codex/skills/one-day-build
   ```

2. Verify SKILL.md is present:
   ```bash
   cat ~/.codex/skills/one-day-build/SKILL.md | head -n 5
   ```

3. Restart Codex

**Still having issues?**

Open an issue at https://github.com/blizhan/one-day-build/issues

## What's Included

The `skill/` directory contains:
- `SKILL.md` - Core workflow
- `references/phases.md` - Detailed phase breakdowns

## Uninstalling

```bash
rm -rf ~/.codex/skills/one-day-build
```
