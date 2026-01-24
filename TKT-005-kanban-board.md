---
status: resolved
priority: high
project: ticketing-plan
created: 2026-01-24
---

# Implement Kanban board view

## Overview
Add a Kanban-style board view for visualizing tickets. Each board is a separate `.board.yaml` file that defines columns and ticket placement. The renderer fetches ticket metadata (status, priority, assignee) from the actual ticket files.

## Requirements
- Multiple boards per team repo (one file per board)
- Drag-and-drop moves ticket ID between columns in the YAML
- Renderer shows ticket metadata from ticket files
- Optional WIP limits per column
- Sprint support with date ranges

## Board Schema

File: `*.board.yaml` (e.g., `main.board.yaml`, `sprint-12.board.yaml`)

```yaml
title: Engineering Board
description: Main development board
created: 2026-01-24
updated: 2026-01-24

columns:
  - name: Backlog
    tickets:
      - TKT-004
      - TKT-006
      - TKT-007

  - name: In Progress
    wip_limit: 5
    tickets:
      - TKT-002
      - TKT-005

  - name: Review
    wip_limit: 3
    tickets:
      - TKT-003

  - name: Done
    tickets:
      - TKT-000
      - TKT-001
```

### Sprint Board Example

File: `sprint-12.board.yaml`

```yaml
title: Sprint 12
created: 2026-01-20
updated: 2026-01-24

sprint:
  start: 2026-01-20
  end: 2026-02-03
  goal: Complete kanban board implementation

columns:
  - name: To Do
    tickets:
      - TKT-005
      - TKT-006

  - name: Doing
    wip_limit: 3
    tickets:
      - TKT-002

  - name: Done
    tickets: []
```

## Rendering

The UI reads the board YAML, then for each ticket ID:
1. Fetch ticket file (e.g., `TKT-002-flat-ticket-structure.md`)
2. Parse frontmatter for status, priority, assignee
3. Render card with title and metadata

This keeps the board simple (just structure + IDs) while tickets remain the source of truth for their own data.

## Implementation Notes
- Use @dnd-kit for drag-and-drop
- On drop, update the YAML and commit via MCP
- Glob `*.board.yaml` to discover boards
- Show WIP limit warnings when exceeded
- Sprint boards show burndown in header
- Consider: sync ticket status when moved to "Done" column?