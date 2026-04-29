# Hackathon Skill

Ship faster at hackathons. This skill gives Claude the full context it needs to guide you from "we have a hackathon" to "we just submitted" -- without losing momentum.

Built for the 4-hour crunch. Works for solo hackers and teams.

Made by [Ian Too](https://iantoo.space)

---

## What It Does

Once installed, Claude becomes your hackathon coach, project manager, and coding co-pilot. It walks through every phase in order:

| Phase | What Happens |
|-------|-------------|
| 1. Intake | Paste a URL or text -- Claude reads the brief and summarizes the requirements |
| 2. Team Formation | Collect names, roles, and GitHub handles. Get a clean team roster |
| 3. Idea Selection | Each member shares an idea. Claude scores them and recommends one |
| 4. Dev Setup | Repo structure, git commands, and tasks broken down per person |
| 5. Build | On-demand help with code, bugs, and integration |
| 6. Presentation | Slide outline and talking points tailored to your judging criteria |
| 7. Submission | Checklist, artifact drafting, and a submission-ready README |

## Team Mode

This skill is designed for teams working in parallel:

1. One member creates the GitHub repo and commits the skill
2. Each teammate installs it in their own Claude Code session
3. Everyone works with Claude at the same time -- the repo is the shared source of truth
4. Phase outputs (TEAM.md, IDEA.md, TASKS.md, etc.) get committed and stay visible to all

## Installation

```bash
claude skills install https://shipables.dev/skills/hackathon
```

Or from local file:

```bash
claude skills install hackathon-skill.skill
```

### Claude.ai / Other Agents

Upload the `hackathon-skill.skill` file via your agent's skill settings.

## Files Included

```
hackathon-skill/
├── SKILL.md                    -- Main skill (all 7 phases)
├── README.md                   -- This file
└── references/
    ├── github-setup.md         -- Git commands for repo and collaborator setup
    └── phase-templates.md      -- Ready-to-commit markdown templates
```

## Requirements

- Works in Claude Code, Claude.ai, and any coding agent that supports skills
- GitHub CLI (`gh`) optional but recommended for repo creation
- No other dependencies

## Usage

Just start talking:

> "We have a hackathon this weekend, help us get organized."
> "I'm doing a solo hackathon, here's the brief: [paste]"
> "We're mid-hackathon and need to pick an idea."

Claude will detect where you are and jump into the right phase.

---

Made with love for hackers. Ship something great.
