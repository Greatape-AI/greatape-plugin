# GreatApe plugin

Manage your GreatApe digital employees from the assistant you already use: Claude (chat, Cowork and
Claude Code), ChatGPT and Codex. Create an employee, hand it what your assistant already knows about
your work, give it tasks, answer its questions and get the results, without leaving the chat.

**Status: in development.** Nothing here is installable yet.

This repository will hold the plugin for both platforms and act as its marketplace:

- `skills/`: shared skills (`employee-pack`, and the GreatApe workflow skill)
- `.claude-plugin/`: the Claude plugin manifest and marketplace file
- `plugin.json`, `mcp.json`: the OpenAI plugin manifest (ChatGPT, Codex)

Both connect to the GreatApe MCP server, where you sign in with your GreatApe account.
