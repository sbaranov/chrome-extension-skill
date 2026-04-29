# Chrome Extension Skill

A Codex skill for building, testing, packaging, debugging, renaming, and preparing Chrome extensions for the Chrome Web Store.

## Install

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
