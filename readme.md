# BearBot

Slack-triggered Cursor Cloud Agent that converts messages into structured Linear tickets for the Mercor AAIE team.

## How it works

1. Someone posts in a channel and mentions `@bearbot`
2. BearBot reads the thread and gathers full context
3. Checks for duplicate tickets in Linear
4. Asks for assignment clarification if needed (or infers from past patterns)
5. Creates a Linear ticket under "Bear & Plato AAIE Tooling" / Applied AI Engineering
6. Replies in Slack with the ticket link and details
7. Updates `MEMORIES.md` with any new patterns learned

## Quick Start

BearBot is a Cursor Cloud Agent — there's no separate deployment or server to run. It operates through Cursor's agent infrastructure with MCP (Model Context Protocol) connections to Slack and Linear.

### Prerequisites

- Access to a Cursor workspace with Cloud Agents enabled
- Slack workspace with BearBot added to relevant channels
- Linear workspace (mercor) with appropriate permissions
- MCP connections configured for both Slack and Linear

### Triggering BearBot

In any Slack channel where BearBot is added:

```
@bearbot file a ticket for this
@bearbot can you create a ticket?
@bearbot please log this as a bug
```

BearBot will:
- Read the thread context
- Check for existing similar tickets
- Ask clarifying questions if needed
- Create the ticket and reply with details

## Project Structure

```
.
├── .cursor/
│   ├── rules/
│   │   ├── bearbot.mdc          # Entry point — links to other rule files
│   │   ├── bearbot-context.mdc  # Identity, team members, priority/type inference
│   │   ├── ticket-conventions.mdc # Ticket format, templates, priority guide
│   │   └── file-ticket.mdc      # Step-by-step filing workflow
│   └── mcp.json                 # Slack + Linear MCP connections
├── MEMORIES.md                  # Learned patterns from past interactions
├── CONTRIBUTING.md              # Guidelines for updating rules
└── readme.md                    # This file
```

### Rule Files

| File | Purpose |
|------|---------|
| `bearbot.mdc` | Root entry point, always applied. Links to other rules. |
| `bearbot-context.mdc` | BearBot's identity, team member mappings (Slack ID → Linear email), priority inference keywords, type classification. |
| `ticket-conventions.mdc` | Ticket title format, description template, priority guide with SLAs, type classification reference. |
| `file-ticket.mdc` | Complete workflow: gather context → check duplicates → check assignment → draft → create in Linear → reply in Slack → update memory. Includes error handling. |

### MCP Configuration

BearBot connects to external services via MCP:

- **Slack MCP** (`https://mcp.slack.com/mcp`) — Read channels, threads; send messages
- **Linear MCP** (`https://mcp.linear.app/mcp`) — Search issues, create tickets, manage assignments

## Ticket Format

### Title
```
[Tool Type] [Project Name] - Ask summary
```

Tool types: `RLS`, `HEX`, `Airtable`, `AT Tooling`, `Miscellaneous`

### Description Template
```markdown
## Summary
1-2 sentences describing what is needed.

## Ask Spec
The ideal end state as described by the reporter.

## What is Being Blocked?
Current impact on work.

## Timeline
Deadline and reasoning.

## Slack Context
Link to original thread, reporter, channel.
```

## Priority Levels

| Priority | Level | SLA | When to use |
|----------|-------|-----|-------------|
| Urgent (P0) | 1 | < 4 hours | Production down, can't do tasks |
| High (P1) | 2 | < 24 hours | Blocking project, tight deadline |
| Medium (P2) | 3 | < 3 days | Important but not critical |
| Low (P3) | 4 | Best effort | Wishlist items |

## Team

BearBot is configured for the Applied AI Engineering team. See `bearbot-context.mdc` for the full team member mapping.

### Escalation Contacts (for <24hr SLA)
- Arunavha Chanda
- Dylan Pourkay
- Current oncall engineer
- Jordan Winawer

## Memory System

BearBot learns from interactions and stores patterns in `MEMORIES.md`:
- User preferences (assignment, priority tendencies)
- Project context (tool types, common requests)
- Assignment patterns (who owns what)
- Recurring request types

Memory provides background context but current conversation always takes priority.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on updating rule files and team member mappings.

## Troubleshooting

### BearBot doesn't respond
- Check that BearBot is added to the channel
- Ensure the message includes `@bearbot`
- Verify MCP connections are active

### Ticket not created
- Check Linear MCP connection
- Look for error messages in BearBot's reply
- Manually create ticket using the drafted content if MCP is down

### Wrong priority/type assigned
- BearBot infers from keywords; be explicit if needed
- Reply with corrections and BearBot can update
