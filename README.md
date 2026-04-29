# Chrome Extension Agent Skill

An agent skill for building, testing, packaging, debugging, renaming, and preparing Chrome extensions for the Chrome Web Store.

This repository uses the `SKILL.md` format supported by agent tools such as Claude and Codex.

## Install

### Claude

Clone or copy this repository into Claude's personal skills directory using a folder name that matches the skill name:

```bash
mkdir -p ~/.claude/skills
git clone <repo-url> ~/.claude/skills/chrome-extension
```

Claude discovers personal skills from `~/.claude/skills/`. The directory name should match the `name` field in `SKILL.md`, which is `chrome-extension`.

### Codex

Install this skill from the repository:

```bash
codex skill install <repo-url>
```

Or install from a local checkout:

```bash
codex skill install /path/to/chrome-extension-skill
```

## What It Helps With

- Reading `manifest.json` as the source of truth for extension metadata, permissions, popup, background worker, and icons.
- Testing Chrome extensions with the repo's existing scripts and Chrome for Testing.
- Packaging Web Store upload zips with `manifest.json` at the archive root.
- Preparing screenshots, icons, privacy answers, permission justifications, and store listing details.
- Avoiding accidental exposure of personal browser data in screenshots and generated assets.

## Files

- `SKILL.md` contains the skill metadata and instructions.

## License

Add a license before publishing if you want to grant reuse rights explicitly.
