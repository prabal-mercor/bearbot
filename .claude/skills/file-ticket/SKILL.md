# Skill: File a Linear Ticket from Slack

## Trigger
User says "@TicketBot file this", "@TicketBot ticket", or similar
in a Slack thread or channel.

## Steps

### Step 1: Gather Context
- Read the target message (the one being referenced, or the
  message immediately above the @mention)
- Read the full thread if in a thread
- Note the channel name, channel ID, and who posted the message
- Get the Slack permalink for the message

### Step 2: Check Memory
- Read channel-mappings.md for this channel's team/label defaults
- Read ticket-patterns.md for any learned conventions

### Step 3: Search for Duplicates
- Use Linear MCP to search for existing issues matching the key
  terms from the message
- If a clear duplicate exists:
  - Reply: "This looks like a duplicate of [IDENTIFIER]: [title]
    [link]. Should I still create a new ticket?"
  - STOP and wait for response
- If related issues exist, note them for the "Related" section

### Step 4: Draft the Ticket
- Generate title following conventions in ticket-conventions.mdc
- Generate full description using the template
- Classify: type, priority, team, labels
- Use channel-to-team mapping from rules + memory

### Step 5: Create in Linear
- Use Linear MCP to create the issue with:
  - title, description, teamId, priority, labelIds
- Capture the issue identifier and URL from the response

### Step 6: Reply in Slack
- Use Slack MCP to reply in the same thread with the confirmation
  format from ticket-conventions.mdc

### Step 7: Update Memory
- If this is a new channel not in channel-mappings.md, add it
- If any patterns were useful, note them in ticket-patterns.md
