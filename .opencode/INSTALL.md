# Installation Guide for OpenCode

## Quick Install

Copy and paste this into OpenCode:

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
cp -r skill ~/.config/opencode/skills/one-day-build

# Or for project-specific installation
mkdir -p .opencode/skills
cp -r skill .opencode/skills/one-day-build
```

### Step 3: Verify Installation

Start OpenCode and run:

```
List available skills
```

You should see `one-day-build` in the list.

## Quick Download (without git)

```bash
curl -L https://github.com/blizhan/one-day-build/archive/refs/heads/main.zip -o one-day-build.zip
unzip one-day-build.zip
cp -r one-day-build-main/skill ~/.config/opencode/skills/one-day-build
rm -rf one-day-build.zip one-day-build-main
```

## Using the Skill

Once installed, the skill automatically triggers when you say things like:

- "Let's build a stock price tracker from scratch"
- "Help me architect a REST API for user management"
- "Let's pair program on a data pipeline"

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
   ls ~/.config/opencode/skills/one-day-build
   ```

2. Verify SKILL.md is present:
   ```bash
   cat ~/.config/opencode/skills/one-day-build/SKILL.md | head -n 5
   ```

3. Restart OpenCode

**Still having issues?**

Open an issue at https://github.com/blizhan/one-day-build/issues

## What's Included

The `skill/` directory contains:
- `SKILL.md` - Core workflow (120 lines)
- `references/phases.md` - Detailed phase breakdowns (194 lines)

Total: 314 lines of guidance

## Uninstalling

```bash
rm -rf ~/.config/opencode/skills/one-day-build
```
