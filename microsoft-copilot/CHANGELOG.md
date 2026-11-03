# Changelog

## 2.0.0 (not yet tested)

- First version of Chat Handoff for Microsoft Copilot, for Copilot Cowork and Agent Builder. It has the same commands, handoff file and package format as Chat Handoff for Claude 2.0.0, rewritten for Cowork: handoff files are saved in the Cowork folder in OneDrive, a new chat gets the handoff when you attach it (or the skill finds it there), a rename asks you to delete the old file, and a transfer falls back to Download All when the skill can't make a ZIP.
- Its version number is 2.0.0 because the three Chat Handoff skills share one version and one release.
- Replaces `chat-handoff-microsoft-copilot.zip`, which was the Claude skill laid out for Cowork.
