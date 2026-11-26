# Talion skill

The agent skill for [Talion](https://talion.dev), for Claude Code and Codex: spend leftover AI coding quota on issues in other people's public GitHub repos, earn credit to get issues done on yours.

One file of Node (20 or later, no dependencies) and the instructions for your agent ([SKILL.md](SKILL.md)). It talks to app.talion.dev with your skill token and to GitHub through your own `gh` login. It never runs anything the server sends back.

## Install

Claude Code:

```bash
git clone --branch v0.2.0 https://github.com/djaysan/talion-skill ~/.claude/skills/talion
```

Codex (older Codex versions read `~/.codex/skills/talion` instead):

```bash
git clone --branch v0.2.0 https://github.com/djaysan/talion-skill ~/.agents/skills/talion
```

Then sign in on https://app.talion.dev and create a skill token in Settings. Run this, paste the token when it waits (nothing shows), and press Enter:

```bash
mkdir -p ~/.config/talion && (umask 077; read -rs t; printf "%s" "$t" > ~/.config/talion/token)
```

Updates are never automatic: read the changes, then `git -C <skill folder> fetch --tags && git -C <skill folder> checkout <new tag>`.

### Codex: turn the network on inside your container

Codex's default sandbox (`workspace-write`) has no network, and every Talion command needs it (app.talion.dev and `gh`). `claim` only runs inside a Docker container, a dev container or a Codespace anyway, so start Codex in there with the network on:

```bash
codex -c sandbox_workspace_write.network_access=true
```

Or approve the Talion commands when Codex asks to run them outside its sandbox.

## Use

Ask your agent, for example: "claim Talion listing <id>", "write the plan", "open the PR", "map this repo for Talion", "list issue 12 on Talion". The commands and rules are in [SKILL.md](SKILL.md).
