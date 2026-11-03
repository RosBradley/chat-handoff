# Changelog

## 2.0.0 — 2026-11-03

- Renamed the plugin and skill ID from `chat-handoff` to
  `chat-handoff-for-chatgpt`, and the download to `chat-handoff-for-chatgpt.zip`.
  Remove the old plugin before installing this one (see docs/setup.md,
  "Upgrading from 1.x").
- Moved into the `chatgpt/` folder of
  [RosBradley/chat-handoff](https://github.com/RosBradley/chat-handoff), which
  also holds the Claude and Microsoft Copilot versions. Releases are tagged
  `chatgpt-v<version>` there; the old repository is archived.
- A release is published when the version in plugin.json changes on main,
  instead of on a pushed tag.
- Removed NOTICE.md and the migration notes: the source they described is now
  in the same repository. The skill and docs no longer mention another app
  except where the work moves to one.

## 1.1.5 — 2026-11-02

- Name the plugin download chat-handoff-chatgpt.zip, with no version in the file
  name.

## 1.1.4 — 2026-11-01

- Use RosBradley as the author name in the manifests, license notice and commit
  history.
- Republish the repository history with that name. Earlier commit hashes and the
  v1.1.3 release download are no longer available; use this release instead.

## 1.1.3 — 2026-11-01

- Correct the author name and contact address in the manifests and license notices.
- Republish the repository with corrected history. Earlier commit hashes and the
  v1.1.2 release download are no longer available; use this release instead.
- Build and publish only the plugin ZIP and its single-entry checksum file.
- Use GitHub's automatic source downloads for development; the plugin already
  includes the skill, so separate source and skill release assets are unnecessary.

## 1.1.2 — 2026-10-25

- Validate ZIP entry paths consistently across Windows, macOS and Linux.
- Expand regression coverage for rooted paths, drive paths and traversal.
- Preserve both upstream and RosBradley MIT copyright notices.

## 1.1.1 — 2026-10-24

- Check which selected project chats can be read before preparing a full export.
- For unavailable or partial chats, provide named handoff requests and a checklist
  of handoffs and referenced files for the user to bring to the coordinator.
- Track partial project coverage and preserve source chats as active backups.
- Add the GitHub repository URL and a description explicitly covering moves
  to new conversations and other AI tools; refresh setup and release guidance.

## 1.1.0 — 2026-10-24

- Add .export/transfer to automatically package scoped context and accessible
  project files for another AI, with a manifest and continuation prompt.
- Make plain handoff/.push a lightweight Markdown path with focused reads and
  no automatic repository inventory, archive, checksums or project test run.
- Route explicit handoff/.push to another AI through the full-package path;
  keep export project as a snapshot that leaves the current chat active.
- Preserve partial-transfer reporting, safety exclusions and existing commands.

## 1.0.1 — 2026-10-22

- Package the ChatGPT/Codex adaptation as a complete maintainable repository.
- Review the supplied Claude repository; confirm its skill matches the original
  v0.3.5 attachment.
- Preserve the upstream MIT license and add source attribution.
- Replace Claude installation, UI and release guidance with host-aware setup.
- Add a Codex installer, deterministic source/plugin/skill builds, validation,
  automated tests, CI and version-tag release workflow.
- Add portable transfer documentation, examples and Codex continuation guidance.
- Correct skill provenance; core workflow behavior remains the 1.0.0 adaptation.

This source release does not automatically update an existing account plugin.

## 1.0.0 — 2026-10-22

Initial ChatGPT adaptation of the supplied Claude v0.3.5 skill: familiar commands,
portable transfer packages, file coverage reporting, review receipts and
capability-aware stale-state handling. Validated with two isolated assistant
exercises: incomplete legacy pickup and proposal review.

## Upstream history

The original Claude repository used versions through 0.3.5. Those releases are
not releases of this repository. See NOTICE.md for provenance.
