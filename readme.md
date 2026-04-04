# BearBot

Slack-triggered Cursor Cloud Agent that converts messages into structured Linear tickets for the Mercor AAIE team.

## How it works
1. Someone posts in a channel and mentions `bearbot`
2. Cursor Cloud Agent reads the thread, gathers context, checks for duplicates
3. Creates a Linear ticket under "Bear & Plato AAIE Tooling" / Applied AI Engineering
4. Replies in Slack with the ticket link

## Structure
- `.cursor/rules/bearbot.mdc` — Entry point
- `.cursor/rules/bearbot-context.mdc` — Identity, team members, config
- `.cursor/rules/ticket-conventions.mdc` — Ticket format and priority guide
- `.cursor/rules/file-ticket.mdc` — Step-by-step filing workflow
- `.cursor/mcp.json` — Slack + Linear MCP connections
- `MEMORIES.md` — Learned patterns, updated after each interaction
