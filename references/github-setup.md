# GitHub Setup Reference

Commands and instructions for setting up the hackathon repo and inviting collaborators.

---

## Step 1: Create the Repo (Repo Creator Only)

Run these commands in your terminal:

```bash
# 1. Create a new directory and initialize git
mkdir [your-project-name]
cd [your-project-name]
git init

# 2. Create initial files
echo "# [Project Name]" > README.md
git add README.md
git commit -m "Initial commit"

# 3. Create the repo on GitHub (requires GitHub CLI)
gh repo create [your-project-name] --public --source=. --remote=origin --push

# OR — if you prefer the web UI:
# Go to https://github.com/new, create the repo, then:
git remote add origin https://github.com/[your-username]/[your-project-name].git
git branch -M main
git push -u origin main
```

---

## Step 2: Add Collaborators

### Via GitHub CLI (one per line):
```bash
gh api repos/[owner]/[repo]/collaborators/[github-username] \
  --method PUT \
  --field permission=push
```

Repeat for each teammate's GitHub username.

### Via Web UI:
1. Go to your repo on GitHub
2. Settings → Collaborators → Add people
3. Enter each teammate's GitHub username or email
4. Set permission to **Write**

Teammates will receive an email invite — they must accept before they can push.

---

## Step 3: Install the Hackathon Skill (Each Team Member)

Each team member should do this in their own environment:

### In Claude Code:
```bash
# From the repo root, create the skill directory
mkdir -p .claude/skills/hackathon

# Copy the SKILL.md into place
# (If your team has committed the skill to the repo, just pull and it's there)
# Otherwise, install from the .skill file:
claude skills install hackathon.skill
```

Or if you're installing from Shipables:
```bash
claude skills install https://shipables.dev/skills/hackathon
```

### Verify it's loaded:
Start a new Claude Code session and say:
> "We're doing a hackathon, help me get started."

Claude should pick up the skill automatically.

---

## Step 4: Commit the Skill to the Repo (Optional but Recommended)

This way everyone on the team gets it automatically when they clone/pull:

```bash
# After installing the skill:
git add .claude/
git commit -m "Add hackathon skill for team"
git push
```

---

## Step 5: Clone the Repo (All Other Team Members)

```bash
git clone https://github.com/[owner]/[repo-name].git
cd [repo-name]

# Pull latest
git pull origin main
```

---

## Commit Workflow During the Hackathon

Keep everyone in sync with short, frequent commits:

```bash
# Before starting a task
git pull origin main

# After finishing something
git add .
git commit -m "[YourName]: [what you did]"
git push origin main

# If you get a conflict
git pull --rebase origin main
# Resolve conflicts, then:
git rebase --continue
git push
```

**Convention for commit messages:**
```
[Name]: Short description of what changed
```
Examples:
- `Alice: Add authentication endpoint`
- `Bob: Fix mobile layout on results page`
- `Team: Integrate frontend with backend API`

---

## Troubleshooting

**"Permission denied" when pushing:**
→ Make sure the repo creator has accepted your collaborator invite (check email)

**"Merge conflict":**
→ Run `git pull --rebase origin main`, fix the conflict markers in the file, then `git add . && git rebase --continue`

**"gh: command not found":**
→ Install GitHub CLI: https://cli.github.com/ — or just use the GitHub web UI for repo creation and collaborator management
