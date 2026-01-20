# engineering.tickets

Engineering team tickets.

## Ticket Format

Tickets are markdown files with YAML frontmatter:

```markdown
---
status: open          # open, in_progress, resolved, closed
priority: high        # urgent, high, medium, low
assignee: username    # optional
project: api          # optional project tag
created: 2024-01-20   # optional
resolved: 2024-01-25  # optional, for resolved/closed tickets
---

# Ticket Title

Description and details...
```

## File Naming

Use the format: `TKT-XXX-short-description.md`

Example: `TKT-001-setup-ci-pipeline.md`

## Status Values

- `open` - New or backlog tickets
- `in_progress` - Currently being worked on
- `resolved` - Completed
- `closed` - Closed without resolution

Status is determined by frontmatter, not file location. All tickets live in the root directory.
