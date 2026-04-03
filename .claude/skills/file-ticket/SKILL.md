# Skill: File a Linear Ticket from Slack

## Trigger
User says "@bearbot file this", "@bearbot ticket", or similar
in a Slack thread or channel.

## Steps

### Step 1: Gather Context
- Read the target message and the full thread
- Note the channel name, channel ID, and who posted
- Get the Slack permalink
- Capture the ENTIRE conversation — this is the most important part

### Step 2: Check Assignment
- If the reporter mentions a specific engineer, note them
- If NOT mentioned, reply in the thread asking:
  "Who should this be assigned to? (Or should I leave it for triage?)"
- Wait for response before proceeding

### Step 3: Search for Duplicates
- Use Linear MCP to search for existing issues matching key terms
- If a clear duplicate exists:
  - Reply with the link and ask if a new ticket is still needed
  - STOP and wait for response

### Step 4: Draft the Ticket
- Title: `[Tool Type] [Project Name] - Ask summary`
- Fill description using the template from ticket-conventions.mdc
- Include the full thread conversation in the "Full Context" section
- Classify priority per the Priority Guide
- Set assignee based on Step 2
- Don't block on missing fields — file the ticket with what you have

### Step 5: Create in Linear
- Use Linear MCP to create the issue with:
  - title, description, teamId, priority, assigneeId (if known)
- Capture the issue identifier and URL

### Step 6: Reply in Slack
- Reply in the same thread:
  ```
  Created [IDENTIFIER]: [Title]
  Priority: [level] · Assignee: [assignee or "Unassigned - pending triage"]
  [linear URL]
  ```
