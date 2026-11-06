# GreatApe plugin

Work with your GreatApe digital employees from the assistant you already use: Claude (chat, Cowork
and Claude Code), ChatGPT and Codex. Hire an employee from what your assistant knows about your
work, see your employees, give one a task and files, answer its questions, read its progress and
results, and cancel work you no longer need.

**Status: phase 4, staging only.** The plugin points at `https://staging.api.greatapeai.com/mcp`.
Hiring (`create_employee`) and text files (`upload_files`) need the GreatApe server from
coworker-agent PR #1156 and employees on the sandbox image with the `install-employee-pack-task`
skill. Setup links and `apps_to_fix` need phase 3 (#1159). The dashboard in the chat, approvals,
routines, check-ins, config and workflow runs need phase 4 (stacked on #1159) and the dashboard's
`mcp-app` screen.

## What's here

```
.claude-plugin/marketplace.json      Claude marketplace
.agents/plugins/marketplace.json     Codex / ChatGPT marketplace
plugins/greatape/
  .claude-plugin/plugin.json         Claude plugin manifest
  .mcp.json                          the GreatApe MCP server, for Claude
  plugin.json                        OpenAI plugin manifest
  mcp.json                           the GreatApe MCP server, for ChatGPT and Codex
  skills/greatape/SKILL.md           when to use which tool
  skills/employee-pack/SKILL.md      interview, build the pack, hire and send it (copied from
                                     Greatape-AI/greatapeai-skills, plus the connected step)
```

Both plugins connect to the GreatApe MCP server, where you sign in with your GreatApe account and
pick an organization. One connection acts in one organization; to switch, disconnect and connect
again.

## Install

**Claude Code**

```
/plugin marketplace add Greatape-AI/greatape-plugin
/plugin install greatape@greatape
```

Then run `/mcp`, choose GreatApe and sign in.

**Claude (chat, Cowork)**: add this repository as a plugin marketplace, install GreatApe, then
connect it under Settings → Connectors and sign in.

**Codex**

```
codex plugin marketplace add Greatape-AI/greatape-plugin
```

Install GreatApe from the plugin list and sign in when asked.

**ChatGPT**: until the plugin is listed, add the server as a custom MCP server in developer mode:
`https://staging.api.greatapeai.com/mcp`.

## Tools

| Tool | What it does |
|---|---|
| `get_account` | Who you're signed in as, and in which organization |
| `list_employees`, `get_employee` | Your organization's employees, and one in detail |
| `update_employee` | Change an employee's name, description or timezone |
| `create_task` | Give an employee a task with a brief |
| `list_tasks`, `get_task` | An employee's tasks, and one task's progress and results |
| `message_task` | Answer a task's question or add to it |
| `cancel_task` | Stop a task for good |
