# Continue this repository in Codex

## Goal

Maintain Chat Handoff for ChatGPT and Codex in the `chatgpt/` folder of
https://github.com/RosBradley/chat-handoff. Preserve the command vocabulary
while making cross-chat and cross-AI transfers honest about accessible context.

## Baseline

Source version 2.0.0, which renamed the plugin and skill ID from chat-handoff
to chat-handoff-for-chatgpt and moved the source into this folder. Earlier
versions lived in RosBradley/chat-handoff-for-chatgpt, since deleted.

One maintained skill: skills/chat-handoff-for-chatgpt. Both plugin manifests
package it. The hosted CI and release workflows are in the repository's
.github/workflows/ (chatgpt-ci.yml and release.yml). One release per version
carries all three skills' downloads; for ChatGPT, only the plugin ZIP.

The agreed public description is: A ChatGPT plugin for moving chat and project
work to new conversations or other AI tools, preserving context, decisions,
files, and next steps. Keep the README and both plugin manifests consistent.

Version 1.1.0 separates lightweight .push from full-package .export/transfer.
An explicit handoff/.push to another AI also selects the full package. Keep
this behavior in both the installed skill and its canonical source.

Version 1.1.1 adds explicit project-chat coverage checks and a collection
checklist for unavailable chats. Source chats remain active as backups.

The README and setup guide now lead with ordinary ChatGPT installation using
the ready-made plugin ZIP and Plugin Creator where available. Keep local Codex
and maintainer build instructions separate. There is no published public listing
or universal ChatGPT skill-ZIP upload menu verified by this repository.

## Read first

1. ../AGENTS.md
2. ../README.md
3. ../skills/chat-handoff-for-chatgpt/SKILL.md and its two references
4. validation.md

## What is implemented

README/setup/design documentation, examples, MIT attribution, portable
and Codex manifests, safe copy installation, package validation, reproducible
ZIP building, unit tests and GitHub CI/release definitions.

## Preserve

- Familiar commands and stable item letters.
- User-approved decisions, exact baselines and Don't redo notes.
- Clear partial-transfer reporting.
- Review before adopting unsupported side-chat claims.
- No invented chat/project access or always-on background behavior.
- A single maintained skill rather than divergent platform copies.

## Next action

Run validation, tests and build locally, then follow the user's next requested
change. Test real usage in Codex using disposable example files. For authorized
GitHub work, use https://github.com/RosBradley/chat-handoff and
inspect its current state before pushing. Do not create a separate repository.

## What not to redo

Do not copy the other Chat Handoff skills in this repository wholesale: their
UI instructions, marketplace commands and per-message cost claims are for other
apps. Do not publish or update the account plugin just to open the repo.

## Validation limits

Read validation.md. Local tests do not establish native ChatGPT/Codex plugin
installation, hosted CI success, or cross-provider automatic migration.
