# Inki plugin for AI agents

[日本語](README.ja.md)

[Inki](https://inki.so) is a writing app for pieces you want to get right: articles, reports, proposals, press releases. You keep each draft as a note. Inki's check reads a note paragraph by paragraph and marks typos, grammar mistakes, and sentences that are hard to read, and you can edit the note in Inki on the web, Mac, iPhone, or Android.

This plugin lets an AI agent such as Claude Code or Codex work on your Inki notes with you. It connects the agent to your Inki account and teaches it a way of working that keeps you in charge of the text:

1. The agent puts a draft from your conversation into an Inki note.
2. It runs Inki's check on the note.
3. It shows you the findings in three groups: what to fix, what to leave as it is (with a reason), and what only you can answer, such as a missing number or source. It does not fill those in with a guess.
4. It fixes only what you asked for.
5. When you have changed the note in Inki yourself, it reads your changes first and keeps them, then continues from your version.

You can start anywhere in that loop. For example:

- "Put this press release draft in Inki, check it, and fix the typos."
- "Check my note about the product launch."
- "I edited the draft in Inki. Keep going."

## Install

You need an Inki account. You can create one at [inki.so](https://inki.so).

### Claude Code

```
/plugin marketplace add n-inc/inki-plugin
/plugin install inki@inki
```

Then run `/mcp`, choose `inki`, and sign in to Inki in the browser window that opens.

### Codex

```
codex plugin marketplace add n-inc/inki-plugin
codex plugin add inki@inki
codex mcp login inki
```

Sign in to Inki in the browser window that opens, then start a new Codex session.

### Other agents

Steps for ChatGPT, Claude, and Cursor are in Inki's docs: [Use Inki from ChatGPT and Claude](https://docs.inki.so/en/features/connect-ai).


The plugin is two pieces that other agents can use too:

- The Inki MCP server at `https://inki.so/api/mcp`. Any agent that can add a remote MCP server with OAuth sign-in can connect to it.
- The skill at [`skills/inki-notes/SKILL.md`](skills/inki-notes/SKILL.md). Agents that read Agent Skills can load it as it is.

## What the agent can do in your account

Signing in lets the agent search and read your notes and folders, see your account's name and email address, create and edit notes, rename and move notes, create folders, move one note at a time to Inki's trash (restorable for 30 days), run Inki's check and reviews, and undo its own edits. Inki keeps the version before each edit in the note's history, so you can go back. Your agent may ask you before each change, depending on its permission settings.

Checks count toward your plan's hourly limit of checked paragraphs, and reviews use credits from your Inki account, the same as in the Inki app. Notes you send through the agent are processed under [Inki's privacy policy](https://inki.so/en/privacy) and [terms](https://inki.so/en/terms).

To disconnect, open Inki and go to Settings › Account › Use Inki from ChatGPT and Claude.

## What's in this repository

| Path | Purpose |
| --- | --- |
| `.mcp.json`, `mcp.json` | The Inki MCP server, `https://inki.so/api/mcp` (Claude Code reads `.mcp.json`, Codex reads `mcp.json`) |
| `skills/inki-notes/SKILL.md` | How the agent drafts, checks, fixes, and continues a note with you |
| `.claude-plugin/`, `.agents/plugins/`, `plugin.json` | Manifests for Claude Code and Codex |

The plugin contains no scripts and stores nothing on your computer beyond the sign-in token your agent keeps for the server.

## Support

Questions and problems: hello@inki.so or [Inki's FAQ](https://inki.so/en/faq).

## License

MIT
