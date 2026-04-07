# Contributing to BearBot

This document outlines guidelines for updating BearBot's rule files and configuration.

## Overview

BearBot is a Cursor Cloud Agent defined entirely through rule files (`.mdc`) and MCP configuration. There is no application code — all behavior is specified in markdown rules that the agent follows.

## Rule File Structure

All rule files live in `.cursor/rules/` and use the `.mdc` extension (Markdown with Cursor metadata).

### Frontmatter

Each rule file starts with YAML frontmatter:

```yaml
---
description: "Brief description of this rule file"
globs: ["**/*"]
alwaysApply: true
---
```

- `description`: Shown in Cursor's rule management UI
- `globs`: File patterns where this rule applies (`["**/*"]` for everywhere)
- `alwaysApply`: If `true`, rule is always active regardless of context

## Making Changes

### Updating Team Members

Team member mappings are in `bearbot-context.mdc` under "Team Members":

```markdown
| Slack ID | Name | Linear Email |
|----------|------|--------------|
| U0XXXXXXX | New Person | newperson@mercor.com |
```

To add a new team member:
1. Get their Slack user ID (format: `UXXXXXXXXXX`)
2. Get their Linear email address
3. Add a row to the table in alphabetical order by name

### Updating Priority Keywords

Priority inference keywords are in `bearbot-context.mdc` under "Priority Inference":

```markdown
- "keyword1", "keyword2" → Priority (level)
```

Add new keywords to the appropriate priority line, keeping the format consistent.

### Updating Type Classification

Type keywords are in both `bearbot-context.mdc` and `ticket-conventions.mdc`. Keep them in sync when making changes.

### Updating the Ticket Template

The description template is in `ticket-conventions.mdc`. Changes here affect all future tickets.

### Updating the Workflow

The step-by-step workflow is in `file-ticket.mdc`. Be careful when modifying — changes affect how BearBot processes every request.

## Testing Changes

Since BearBot is a Cursor Cloud Agent, testing happens by:

1. Making changes to rule files
2. Triggering BearBot in a test Slack channel
3. Verifying the behavior matches expectations

There are no automated tests — behavior is validated through manual interaction.

## Best Practices

### Do
- Keep changes atomic (one logical change per commit)
- Update all related files together (e.g., if adding a keyword, update both context and conventions)
- Test in a non-critical channel before deploying
- Document non-obvious decisions in commit messages

### Don't
- Change escalation contacts without team approval
- Modify MCP endpoints without infrastructure team involvement
- Remove team members without verifying they've left the team
- Add complex conditional logic — rules should be straightforward

## File Responsibilities

| File | Owner | Change Frequency |
|------|-------|------------------|
| `bearbot.mdc` | Core team | Rarely changes |
| `bearbot-context.mdc` | Team leads | When team changes |
| `ticket-conventions.mdc` | Process owners | When ticket format evolves |
| `file-ticket.mdc` | Core team | When workflow changes |
| `mcp.json` | Infrastructure | Rarely changes |
| `MEMORIES.md` | BearBot (automated) | After each interaction |

## Updating MEMORIES.md

`MEMORIES.md` is updated automatically by BearBot after each interaction. Humans should generally not edit this file directly, except to:

- Remove clearly incorrect entries
- Clean up duplicate or stale patterns
- Reorganize for clarity (without changing meaning)

## Questions?

Reach out in #applied-ai-engineering or contact the escalation contacts listed in `bearbot-context.mdc`.
