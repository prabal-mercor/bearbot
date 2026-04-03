# Skill: File a Linear Ticket from Slack

## Trigger
User says "ticketBot file this", "ticketBot ticket", or similar
in a Slack thread or channel.

## Steps

### Step 1: Gather Context
- Read the target message and the full thread
- Note the channel name, channel ID, and who posted
- Get the Slack permalink for the message

### Step 2: Check Assignment
- If the reporter mentions a specific engineer, note them
- If NOT mentioned, reply in the thread asking:
  "Who should this be assigned to? (Or should I leave it for triage?)"
- Wait for response before proceeding

### Step 3: Search for Duplicates
- Use Linear MCP to search for existing issues matching key terms
- If a clear duplicate exists:
  - Reply: "This looks like a duplicate of [IDENTIFIER]: [title]
    [link]. Should I still create a new ticket?"
  - STOP and wait for response
- If related issues exist, note them for the description

### Step 4: Draft the Ticket
- Generate title: `[Tool Type] [Project Name] - Ask summary`
- Generate full description using the template from ticket-conventions.mdc
- Classify priority using the Priority Guide
- Set assignee based on Step 2

### Step 5: Create in Linear
- Use Linear MCP to create the issue with:
  - title, description, teamId, priority, assigneeId (if known)
- Capture the issue identifier and URL

### Step 6: Reply in Slack
- Use Slack MCP to reply in the same thread with the confirmation
  format from ticket-conventions.mdc

### Step 7: Update Memory
- If any new patterns were useful, note them in ticket-patterns.md
