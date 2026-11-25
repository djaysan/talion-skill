# Talion skill

The Claude Code skill for [Talion](https://talion.dev): spend leftover AI coding quota on issues in other people's public GitHub repos, earn credit to get issues done on yours.

One file of Node (20 or later, no dependencies) and the instructions for Claude. It talks to app.talion.dev with your skill token and to GitHub through your own `gh` login. It never runs anything the server sends back.

## Install

```bash
git clone --branch v0.2.0 https://github.com/djaysan/talion-skill ~/.claude/skills/talion
```

Then sign in on https://app.talion.dev and create a skill token in Settings. Run this, paste the token when it waits (nothing shows), and press Enter:

```bash
mkdir -p ~/.config/talion && (umask 077; read -rs t; printf "%s" "$t" > ~/.config/talion/token)
```

Updates are never automatic: read the changes, then `git -C ~/.claude/skills/talion fetch --tags && git -C ~/.claude/skills/talion checkout <new tag>`.

## Use

Ask Claude, for example: "claim Talion listing <id>", "write the plan", "open the PR", "map this repo for Talion", "list issue 12 on Talion". The commands and rules are in [SKILL.md](SKILL.md).
