# BearBot Learned Patterns

## Assignment
- If reporter says "for me" or similar, assign to the reporter (confirm from thread context).
- Prabal sometimes overrides assignee mid-thread — always honor the final explicit instruction.
- When no assignee is mentioned, ask in the thread before creating the ticket (unless urgency suggests immediate filing).
- Try to find the most relevant prior owner based on similar past tickets before defaulting to triage.

## Priority Inference
- Plato operational requests (e.g., run batch jobs) default to Medium unless explicit urgency/blocking language.
- "urgent", "blocking", "broken", "can't do tasks" → Urgent (P0)
- "need ASAP", "blocking project" → High (P1)
- Default if unclear → Medium (P2)

## Ticket Filing
- If a request closely matches an existing active Linear issue (same scope), post the existing link and ask before creating a new one.
- When asked to create a "fresh final ticket with all info", consolidate all prior tickets from the thread into one new issue.
- When follow-up scopes additional requirements for an even canceled ticket, create a new ticket.
- Prabal may request both assignee and subscriber tagging; honor both.

## Slack↔Linear Linking
- "Link with this thread" = attach Slack thread permalink as a link on the Linear issue (use `links` param in save_issue).
- Only do Slack↔Linear sync when explicitly asked.

## GitHub / Repo Access
- GitHub repo access requests (e.g., org/repo) are Miscellaneous, Medium priority, routed to triage unless assignee specified.
- Past similar tickets resolved by Ryan Hu (AAIE-3601) and Ben Hunsberger (AAIE-1267).
- BearBot can only push PRs to `prabal-mercor/bearbot`; external repos require manual collaborator access.

## Misc
- "apex-swe" refers to `Mercor-Intelligence/apex-swe`, an SWE integration harness repo.
- When asked to "raise any PR", default to a small meaningful improvement in the bearbot repo.
