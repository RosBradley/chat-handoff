# Chat Handoff

Chat Handoff lets a new chat pick up where a long one left off, folds a side chat's work into a main one after a review you approve, and carries a chat's or project's work, files included, to another AI. Type `handoff` (or `.push`) in the long chat, and `pickup <name>` (or `.pull <name>`) in the new one.

There's one version for each app. They share the same commands and the same package format, so work moves between them. The current release is **2.0.0**, with a download for each app; download only the one for your app.

| For | Download | Setup |
|---|---|---|
| **Claude** (claude.ai, Claude Code), in testing | [chat-handoff-for-claude.zip](https://github.com/RosBradley/chat-handoff/releases/download/v2.0.0/chat-handoff-for-claude.zip), or the Claude Code plugin | [claude/](claude/) |
| **ChatGPT** (and Codex) | [chat-handoff-for-chatgpt.zip](https://github.com/RosBradley/chat-handoff/releases/download/v2.0.0/chat-handoff-for-chatgpt.zip) | [chatgpt/](chatgpt/) |
| **Microsoft Copilot** (Cowork, Agent Builder), not yet tested | [chat-handoff-for-microsoft-copilot.zip](https://github.com/RosBradley/chat-handoff/releases/download/v2.0.0/chat-handoff-for-microsoft-copilot.zip) | [microsoft-copilot/](microsoft-copilot/) |

Each folder has its own README with the commands, setup steps and limits for that app, and its own changelog.

**About Microsoft Copilot:** Chat Handoff for Microsoft Copilot is new and hasn't been tried in Copilot yet. It's adapted from the Claude version and rewritten for how Cowork saves and finds files. If a step doesn't work, say "handoff, and post it here" (or ".push, and post it here") and paste the result into the new chat. Reports of what works and what doesn't are welcome as [issues](https://github.com/RosBradley/chat-handoff/issues).

**Claude Code plugin:**

```
/plugin install chat-handoff-for-claude --marketplace RosBradley/chat-handoff
```

## License

MIT. See [LICENSE](LICENSE).
