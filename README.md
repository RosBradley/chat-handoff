# Chat Handoff

Chat Handoff lets a new chat pick up where a long one left off, folds a side chat's work into a main one after a review you approve, and carries a chat's or project's work, files included, to another AI. Type `handoff` (or `.push`) in the long chat, and `pickup <name>` (or `.pull <name>`) in the new one.

There's one version for each app. They share the same commands and the same package format, so work moves between them.

| For | Version | Download | Setup |
|---|---|---|---|
| **Claude** (claude.ai, Claude Code) | 0.5.0, in testing | [chat-handoff-for-claude.zip](https://github.com/RosBradley/chat-handoff/releases/download/claude-v0.5.0/chat-handoff-for-claude.zip), or the Claude Code plugin | [claude/](claude/) |
| **ChatGPT** (and Codex) | 2.0.0 | [chat-handoff-for-chatgpt.zip](https://github.com/RosBradley/chat-handoff/releases/download/chatgpt-v2.0.0/chat-handoff-for-chatgpt.zip) | [chatgpt/](chatgpt/) |
| **Microsoft Copilot** (Cowork, Agent Builder) | 0.1.0, not yet tested | [chat-handoff-for-microsoft-copilot.zip](https://github.com/RosBradley/chat-handoff/releases/download/microsoft-copilot-v0.1.0/chat-handoff-for-microsoft-copilot.zip) | [microsoft-copilot/](microsoft-copilot/) |

Each folder has its own README with the commands, setup steps and limits for that app, and its own changelog. Releases are tagged by app: `claude-v…`, `chatgpt-v…` and `microsoft-copilot-v…`.

**Claude Code plugin:**

```
/plugin install chat-handoff-for-claude --marketplace RosBradley/chat-handoff
```

## License

MIT. See [LICENSE](LICENSE).
