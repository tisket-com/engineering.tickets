---
status: open
priority: medium
project: ticketing-plan
created: 2026-01-24
---

# Implement @mentions and notifications

## Overview
Allow users to mention others in comments and receive notifications.

## Requirements
- Parse @username mentions in comment content
- Send notifications to mentioned users
- Notification preferences per user
- Support email and/or in-app notifications

## Implementation Notes
- Add mention parsing to comment content
- Create notification system (needs backend support)
- Add notification bell/indicator to UI
- Consider webhook integration for external notifications