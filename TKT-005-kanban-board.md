---
status: open
priority: high
project: ticketing-plan
created: 2026-01-24
---

# Implement Kanban board view

## Overview
Add a Kanban-style board view for visualizing tickets by status. Board configuration is stored as a YAML file in the repo for version control and team sharing.

## Requirements
- Multiple boards per team repo
- Column per status (open, in_progress, resolved, closed) or custom columns
- Drag-and-drop to change status
- Optional swimlanes by priority, assignee, or project
- WIP limits per column (configurable)
- Sprint support with date ranges and velocity tracking
- Board filtering by labels, assignee, project

## Board Configuration Schema

Store in `.boards.yaml` at the repo root:

```yaml
boards:
  - id: main
    name: Engineering Board
    default: true
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
    filters:
      exclude_labels: [blocked]

  - id: sprint-current
    name: Sprint 12
    sprint:
      start: 2026-01-20
      end: 2026-02-03
      goal: "Complete kanban board implementation"
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

defaults:
  wip_limit: 10
  swimlanes:
    collapsed: [low]  # collapse low priority swimlane by default
```

## Implementation Notes
- Use @dnd-kit or similar for drag-and-drop
- Create `KanbanBoard` component with board selector
- Parse `.boards.yaml` on load, validate against schema
- Changes to board config require git commit (through MCP or direct)
- Add board management UI for creating/editing boards
- Sprint boards show burndown/velocity in header