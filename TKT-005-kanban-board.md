---
status: open
priority: high
project: ticketing-plan
created: 2026-01-24
---

# Implement Kanban board view

## Overview
Add a Kanban-style board view for visualizing tickets by status. Each board is stored as a separate `.board.yaml` file in the repo, following the same pattern as timelines.

## Requirements
- Multiple boards per team repo (one file per board)
- Column per status (open, in_progress, resolved, closed) or custom columns
- Drag-and-drop to change status
- Optional swimlanes by priority, assignee, or project
- WIP limits per column (configurable)
- Sprint support with date ranges and velocity tracking
- Board filtering by labels, assignee, project

## Board Schema

File: `*.board.yaml` (e.g., `main.board.yaml`, `sprint-12.board.yaml`)

```yaml
title: Engineering Board
description: Main development board
created: 2026-01-24
updated: 2026-01-24

columns:
  - id: backlog
    name: Backlog
    statuses: [open]
  - id: in-progress
    name: In Progress
    statuses: [in_progress]
    wip_limit: 5
  - id: review
    name: Review
    statuses: [in_progress]
    labels: [needs-review]
    wip_limit: 3
  - id: done
    name: Done
    statuses: [resolved, closed]

swimlanes:
  enabled: true
  group_by: priority  # priority | assignee | project | label
  collapsed: [low]

filters:
  exclude_labels: [blocked]
```

### Sprint Board Example

File: `sprint-12.board.yaml`

```yaml
title: Sprint 12
description: Complete kanban board implementation
created: 2026-01-20
updated: 2026-01-24

sprint:
  start: 2026-01-20
  end: 2026-02-03
  goal: Complete kanban board implementation

columns:
  - id: todo
    name: To Do
    statuses: [open]
  - id: doing
    name: Doing
    statuses: [in_progress]
    wip_limit: 3
  - id: done
    name: Done
    statuses: [resolved]

filters:
  labels: [sprint-12]
```

## Implementation Notes
- Use @dnd-kit or similar for drag-and-drop
- Create `KanbanBoard` component with board selector dropdown
- Glob for `*.board.yaml` files to discover boards
- Parse and validate against schema on load
- Changes to board config require git commit (through MCP or UI)
- Add board management UI for creating/editing boards
- Sprint boards show burndown/velocity in header
- Consider adding `default: true` field or using alphabetical first as default