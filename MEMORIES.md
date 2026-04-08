# BearBot Learned Patterns

Keep updating as new patterns emerge. Current conversation always takes priority over memory.

## Assignment
- If reporter says "for me" or similar, treat as explicit self-assignment and assign to that reporter.
- Prabal may explicitly override assignee mid-thread (e.g., "assign to me, not to X") — always honor the final explicit instruction.
- Prabal sometimes requests both assignee selection and subscriber tagging in the same ticket; honor both.
- Try to find the most relevant engineer based on past similar tickets before defaulting to triage.

## Priority Inference
- Plato operational requests (e.g., run batch jobs) default to Medium unless urgency/blocking language is explicit.

## Ticket Handling
- If a Slack ticket request closely matches an existing active Linear issue (same scope/deliverables), post the existing issue link in the thread and ask whether a new ticket is still needed before creating one.
- When a follow-up message scopes additional output format requirements for an existing (even canceled) ticket, create a new ticket rather than reopening the old one.
- When asked to create a "fresh final ticket with all info", consolidate all prior tickets in the thread into a single new issue rather than editing existing ones.

## Slack↔Linear Linking
- "Link with this thread" means attach the Slack thread permalink as a link attachment on the Linear issue (use the `links` param in save_issue).

## GitHub / Repo Access
- GitHub repo access requests are categorized as Miscellaneous, filed as Medium priority unless urgency language is explicit, and routed to triage when no assignee is specified.
- Past similar repo access tickets were resolved by Ryan Hu (AAIE-3601) and Ben Hunsberger (AAIE-1267).
