---
name: chrome-extension
description: Use when building, testing, packaging, debugging, renaming, or preparing a Chrome extension for the Chrome Web Store, including manifest permissions, extension reloads, Chrome for Testing automation, screenshots, icons, privacy fields, and publishing artifacts.
---

# Chrome Extension

## Core Workflow

- Read repo guidance first, especially `AGENTS.md`, `README.md`, `package.json`, and `manifest.json`.
- Treat `manifest.json` as the source of truth for extension name, description, permissions, popup, background service worker, and icons.
- Prefer existing repo scripts over ad hoc commands. Check `package.json` before testing, packaging, generating assets, or launching browsers.
- Use `rg` to find extension names, permission mentions, generated asset names, and Chrome Web Store wording.
- Keep Chrome product concepts distinct from the extension brand. Do not rename terms like Bookmarks Bar, Other Bookmarks, Mobile Bookmarks, Bookmarks Manager, Chrome for Testing, or Chrome Web Store unless the user explicitly asks.

## Browser And Reloading

- When managing or reloading an extension in a user's main Chrome profile, follow repo-local instructions. If `AGENTS.md` says how to handle `chrome://extensions/`, obey it.
- Avoid replacing the user's current Chrome tab. Prefer an existing relevant tab, or open a new tab when needed.
- Use the user's main Chrome only for manual inspection or explicitly requested real-profile checks.
- Use Chrome for Testing for automation and E2E tests. Do not run automated extension tests against the user's main Chrome profile.
- On macOS browser automation, prefer Chrome for Testing with `--use-mock-keychain`.

## Testing

- Run the repo's documented test command, usually `npm test`, before claiming behavior is verified.
- If browser automation fails because of sandboxed local port binding or browser launch restrictions, rerun with the required permission instead of rewriting the test approach.
- For popup/UI work, verify behavior with browser automation when practical, especially after drag/drop, sizing, context menu, popup navigation, or generated screenshot changes.
- For generated images, verify dimensions with a reliable local tool such as `sips` on macOS.

## Packaging

- Chrome Web Store uploads should be `.zip` packages, not CRX files.
- Generated zips usually belong outside Git. If the repo does not already define this, consider ignoring `dist/` or generated zip artifacts.
- Before upload, verify the package contents. `manifest.json` must be at the archive root.
- Regenerate the package after changes that affect source files, manifest, icons, popup assets, or store-facing metadata.

## Store Assets

- Use fake/demo bookmark data for README, website, and Chrome Web Store screenshots. Never expose the user's real bookmarks, tabs, email, account names, or personal browsing data.
- Chrome Web Store listing screenshots may have strict dimensions. Verify exact pixel size before handing them to the user.
- Keep screenshot generators deterministic where possible. Prefer repo scripts that generate preview/banner assets over manual screenshots.
- For extension icons, check the small sizes too: 16, 32, 48, and 128 px. A concept that works at 128 px may fail at toolbar size.

## Chrome Web Store Forms

- For current Web Store rules or policy text, check official Chrome documentation.
- Fill drafts when the user asks, but do not submit for review without explicit confirmation.
- Confirm at action time before uploads, save-draft actions, publishing, or any action that transmits repo files or user-entered form data to Google.
- Privacy and permission justifications should be narrow, accurate, and tied directly to the extension's single purpose.
- If an extension does not collect or transmit user data, say that plainly. Do not imply user data is collected merely because Chrome APIs can read local browser data.

## Common Checks

- Search for old extension names after renames.
- Check `manifest.json`, popup HTML titles/ARIA labels, README, privacy policy, package names, generated screenshot text, and package output names.
- If the repository was renamed, update Git remote URLs and public docs/form URLs. Do not edit `.git/FETCH_HEAD` manually.
- If local workspace folders are renamed, prefer starting new agent sessions from the new path or using a compatibility symlink for old chats.
