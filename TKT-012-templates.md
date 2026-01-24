---
status: open
priority: low
project: ticketing-plan
created: 2026-01-24
---

# Add ticket templates per team

## Overview
Allow teams to define reusable ticket templates.

## Requirements
- Store templates in team repo (e.g., `.templates/` directory)
- Template types: bug report, feature request, task, etc.
- Pre-filled frontmatter and markdown structure
- Template selection when creating new ticket

## Implementation Notes
- Define template format (markdown with placeholder syntax)
- Add template picker to ticket creation flow
- MCP tool should support `--template` option