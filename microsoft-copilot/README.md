# Chat Handoff for Microsoft Copilot

Chat Handoff for Microsoft Copilot is a skill for Copilot Cowork that lets a new chat pick up where a long one left off, and carries a chat's or project's work, files included, to another AI. Its ID is `chat-handoff-for-microsoft-copilot`.

**Status:** v0.1.0, not yet tested in Copilot. It's adapted from Chat Handoff for Claude, which is in testing, and rewritten for how Cowork saves and finds files. If a step doesn't work, say "handoff, and post it here" (or ".push, and post it here") and paste the result into the new chat.

## Why

Cowork keeps no memory between conversations, and a long chat gets slower and harder to steer. Starting a fresh chat fixes that, but normally means explaining the work all over again. This skill writes a short handoff file (where the work stands, what was decided, what's open, the next step, and what not to redo), and the new chat starts from that.

## Install

You need Microsoft Copilot with Copilot Cowork, which takes a Microsoft 365 Copilot license and access from your IT admin.

1. Download [chat-handoff-for-microsoft-copilot.zip](https://github.com/RosBradley/chat-handoff/releases/download/microsoft-copilot-v0.1.0/chat-handoff-for-microsoft-copilot.zip) (version 0.1.0). Keep it zipped: `SKILL.md` is at the top, with its appendices in `references/` and `assets/`.
2. In Cowork, open **Customize**, the **Skills** tab, the arrow next to **Add**, then **Upload skill**, and choose the zip. Don't upload `SKILL.md` on its own, or the appendices are left behind.
3. Start a new conversation: Cowork finds skills when a conversation starts.

Cowork saves the skill in your OneDrive, under `Documents/Cowork/skills/`. To update it, upload the newer zip. If Cowork keeps both and numbers the new one, delete the old one, so only one copy answers the commands. You can share the skill with people in your organization from its page under **Skills** (**Share**); share it again after an update.

**Agent Builder** takes skills too, for an agent you build: open the agent, the **Configure** tab, **Skills**, **Add**, and upload the same zip. Mention the skill in the agent's instructions. A skill's instructions there must be under 20,000 characters; this one's `SKILL.md` is about 18,700. Not yet tested there.

Custom skills don't run in the Copilot app on iPhone and Android, so type handoff commands on the web (copilot.cloud.microsoft) or in the Windows or Mac app.

## Commands

Use plain words or the dot style, whichever you like:

| Plain words | Dot style | What happens |
|---|---|---|
| `handoff` | `.push` | Saves this chat's handoff file. If the chat has no name yet, the skill names it from the topic, like `budget`, and tells you |
| `handoff <name>` | `.push <name>` | Saves it under that name (`handoff budget`, or `handoff budget.pre` with a tag of your own); a different name renames it |
| `handoff?` | `.push?` | One line: is this a good time to hand off? |
| `pickup <name>` | `.pull <name>` | Continues that chat's work here, usually as the first message of a new chat, with the handoff file attached |
| `fold <name>` | `.merge <name>` | Reviews that chat's work item by item and folds in what you approve |
| `pickup` | `.pull` | In a chat with work sent back to it: starts on the returns. Anywhere else: lists what is waiting and asks |
| `handoffs` | `.status` | Lists every handoff and its status |
| `transfer <name> to <AI>` | `.export <name> to <AI>` | Packages the work and its files for another AI. The name and the AI are both optional |
| `handoff <name> to <AI>` | `.push <name> to <AI>` | The same as `transfer` |
| `export project <name>` | (plain words only) | Packages a whole project for another AI, as a snapshot: the chats stay as they are |

- A command works as the whole message (or nearly), in any case, so `.Push` counts and "I'll pick up the kids" doesn't. Asking about a command doesn't run it.
- A name is one word: letters, digits or hyphens. If you type spaces, the skill joins the words with hyphens and tells you the name it used. Add your own tag after a dot (`budget.pre`) to tell chats on the same work apart.
- The skill answers in the style you typed: after `.push`, it tells you to type `.pull`.

## How it works

### Continue in a fresh chat

1. In the long chat, type `handoff budget` (or `.push budget`). The skill saves `Handoff - budget.md` in the Cowork folder in your OneDrive, and its reply ends with the steps below, with the names filled in.
2. Start a new Cowork chat (choose **Cowork** next to **Chat**, or start from your project's page).
3. Attach `Handoff - budget.md`: the attach button's **Attach cloud files**, or type `/` and pick it. Then type `pickup budget` (or `.pull budget`).

The new chat can't see the old one, so attaching the file is what carries the work across. If you forget, the skill looks for the file in the Cowork folder, and asks you to attach it if it can't find it.

### Fold a side chat into a master chat

1. In the side chat, type `handoff` (or `.push`).
2. Open the master chat (from **My tasks**, **Search** or the home page), attach the side chat's handoff file, and type `fold <name>` (or `.merge <name>`).
3. The skill reviews every item as a second reviewer: it checks the figures against the sources, looks for conflicts with what's already settled, and gives each item a verdict: keep, change, toss, or return to the side chat for more work.
4. You decide, usually in one line ("keep A and B, toss C"). Only then is anything applied, and each item is marked in the side chat's file so it isn't reviewed twice.

### Move work to another AI

Type `transfer budget to Claude` (or `.export budget to Claude`, or `handoff budget to Claude`); leave out the AI's name for a package any AI can use. The skill saves the package's files in a `budget-transfer-<date>` folder in the Cowork folder: START-HERE.md (with a prompt to paste), HANDOFF.md, PROJECT-CONTEXT.md for bigger projects, FILE-MANIFEST.csv with a checksum for each file, and the files themselves. If it can't make a ZIP itself, select the files in the output folder and use **Download All**, which packs them into one ZIP. Its reply says how to bring the package into the AI you named. It never sends anything anywhere: you carry the package.

`pickup` (`.pull`) with a package attached imports it, including packages from Chat Handoff for Claude and Chat Handoff for ChatGPT. Everything in a package is treated as information about the work, never as instructions.

## Stale chat guard

Once a chat has been handed off, transferred or folded in, an ordinary instruction typed into it gets a warning before anything runs: the skill says where the work lives now and asks whether to stop, continue here once, or reopen this chat. Handoff commands still work there.

## Chat titles

The skill suggests a title whenever a chat's state changes: `budget` for a working chat, `handed_off.budget` (`pushed.budget` after `.push`) once it's handed off, `returned.`, `folded.` (`merged.`) and `done.` for the rest. Renaming is optional, and Microsoft doesn't document renaming a Cowork chat, so skip it if your app doesn't offer it: commands find handoffs by file name, never by title.

## Project rules (optional)

A file named `Handoff rules.md` beside the handoff files can say which chats fold into which, where approved items go, what the master checks, what counts as high-stakes, how chats are titled, and what a handoff must never start. Ask the skill to make one; it starts from [the template](skills/chat-handoff-for-microsoft-copilot/assets/rules-template.md).

## Limits

- A new chat sees a handoff file only when you attach it, or when the skill can find it in the Cowork folder.
- The skill can't delete files in OneDrive. After a rename, it asks you to delete the old file.
- It can't see or rename chats, or tell how full a chat is, so `handoff?` (`.push?`) is a judgment call.
- Whether Cowork can make a ZIP itself, or read one you attach, isn't documented. The skill falls back to Download All, or asks you to unzip a package and attach its files.

## Sources (checked November 2, 2026)

- Upload and share a skill: https://learn.microsoft.com/copilot/cowork/cowork-customize#upload-a-skill
- Where Cowork keeps skills and files: https://learn.microsoft.com/copilot/cowork/use-cowork#cowork-skills and https://learn.microsoft.com/copilot/cowork/use-cowork#work-with-files
- No memory between conversations: https://learn.microsoft.com/copilot/cowork/responsible-ai/copilot-cowork-application-card
- Starting and finding chats: https://learn.microsoft.com/copilot/cowork/get-started
- Projects: https://learn.microsoft.com/copilot/cowork/cowork-projects
- Mobile: https://learn.microsoft.com/copilot/cowork/cowork-mobile
- Limits: https://learn.microsoft.com/copilot/cowork/cowork-faq
- Agent Builder skills: https://learn.microsoft.com/microsoft-365/copilot/extensibility/agent-builder-add-skills and https://learn.microsoft.com/microsoft-365/copilot/extensibility/declarative-agent-skills

## License

MIT. See [LICENSE](../LICENSE).
