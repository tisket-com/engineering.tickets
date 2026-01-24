---
status: open
priority: high
project: ticketing-plan
created: 2026-01-24
---

# Implement Kanban board view

## Overview
Add a Kanban-style board view for visualizing tickets by status.

## Requirements
- Column per status (open, in_progress, resolved, closed)
- Drag-and-drop to change status
- Optional swimlanes by priority, assignee, or project
- WIP limits per column (configurable)
- Persist view preferences

## Implementation Notes
- Use @dnd-kit or similar for drag-and-drop
- Create `KanbanBoard` component
- Add view toggle (list vs kanban) to `TicketsOverview`
- Store view preference in localStorage