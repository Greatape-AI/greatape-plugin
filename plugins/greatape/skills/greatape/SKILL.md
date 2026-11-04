---
name: greatape
description: Work with the person's GreatApe digital employees - list them, hire one, give one a task or files, follow up, answer its questions, read its results, cancel. Use whenever the person names a GreatApe employee, asks one to do something, asks to hire one, or asks how their work is going.
---

# GreatApe employees

**IRON LAW: ONE PIECE OF WORK IS ONE TASK.** Answers, corrections and follow-ups go to that task
with `message_task`. NEVER open a second task for work an employee already has.

## Start

- Call `get_account` once per conversation and say which organization you are acting in.
- Find the employee with `list_employees` and use its `id`. NEVER guess an id.
- A tool says you aren't signed in, or have no organization: explain how to connect (below).

## Give work

- `create_task(employee_id, title, description)`. The employee saw none of this conversation, so
  write the brief for a colleague: the goal and why, everything already decided (names, numbers,
  links, quotes), who is involved, constraints, what done looks like, where the result goes.
- Short material goes in the brief itself. The employee can't open files on the person's computer.
- Files go with `upload_files` first, then `upload_id` on `create_task` or `message_task`. Text
  only (Markdown, CSV, JSON, code); the first call goes alone and returns the `upload_id`. For a
  PDF, image or spreadsheet, give the person the employee's link to upload it there.
- Work that needs a connected app: check `apps` in `get_employee` first. Missing, give the person
  the `connections` link instead of starting a task that will fail.
- Share the tracking link from `create_task`'s reply.

## Follow up

- Status questions: `get_task` or `list_tasks`. NEVER create a task to ask about a task.
- The employee asked a question, or the person adds something: `message_task` on the same task.
- Results arrive in the task's updates. Files come as links; pass them on.
- Check when the person asks. Don't poll in a loop.

## Stop

- CONFIRM WITH THE PERSON before `cancel_task`. It stops the run for good.

## Change an employee

- `update_employee` changes name, description or timezone only.
- Instructions, model, pause and resume live in the dashboard (`dashboard_url` from `get_account`).
- To create an employee, use the `employee-pack` skill: it interviews the person, builds the pack,
  hires the employee with `create_employee` and sends the pack. `create_employee` starts the
  organization's free trial if it hasn't started; tell the person its terms exactly as the tool says.

## Connect

- Claude (chat, Cowork): Settings → Connectors → GreatApe → Connect, sign in, pick the organization.
- Claude Code: run `/mcp`, choose GreatApe, authenticate.
- ChatGPT and Codex: sign in when the plugin asks, and pick the organization.
- Another organization: disconnect GreatApe, connect again and pick the other one.
