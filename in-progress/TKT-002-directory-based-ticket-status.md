# TKT-002: Directory-Based Ticket Status

**Priority:** high
**Assignee:** @jim

## Description

Implement directory-based status for tickets where the folder name determines the ticket status (in-progress, backlog, closed).

## Implementation

- Directories within ticket repos act as status categories
- Status is derived from directory name, not frontmatter
- Sidebar groups tickets by directory like docs
- Default structure: in-progress, backlog, closed

## Progress

- [x] Updated tickets.ts to support tree structure
- [x] Updated sidebar to render directory hierarchy
- [ ] Reorganize tickets via MCP
- [ ] Test in browser
