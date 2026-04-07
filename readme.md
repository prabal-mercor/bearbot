# BearBot

Slack-triggered Cursor Cloud Agent that converts messages into structured Linear tickets for the Mercor AAIE team.

## How it works
1. Someone posts in a channel and mentions `bearbot`
2. Cursor Cloud Agent reads the full thread and gathers context
3. Checks Linear for duplicate issues before creating a new one
4. Asks who to assign if not mentioned (suggests based on past work)
5. Creates a Linear ticket under "Bear & Plato AAIE Tooling" / Applied AI Engineering
6. Replies in Slack with the ticket identifier, priority, assignee, and link

## Structure
- `.cursor/rules/bearbot.mdc` — Entry point
- `.cursor/rules/bearbot-context.mdc` — Identity, team members, config
- `.cursor/rules/ticket-conventions.mdc` — Ticket format and priority guide
- `.cursor/rules/file-ticket.mdc` — Step-by-step filing workflow
- `.cursor/mcp.json` — Slack + Linear MCP connections
- `MEMORIES.md` — Learned patterns, updated after each interaction
