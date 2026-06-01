# Productivity Category Schema

The `productivity` category handles signals from apps that understand work and task preferences, such as task managers, calendars, and time-tracking tools.

## Useful Context Fields

- **Task Organization Style:** How the user prefers to break down or organize tasks (e.g., `tagging`, `time-blocking`, `kanban`).
- **Recurring Project Areas:** High-level themes or project areas the user frequently engages with (e.g., `frontend_development`, `marketing_planning`).
- **Calendar or Planning Habits:** Preferences for scheduling (e.g., `morning_meetings`, `no_meetings_after_3pm`).
- **Preferred Notification Style:** How the user likes to be reminded (e.g., `batch_notifications`, `strict_deadlines`).
- **Focus-Time Preferences:** When and how the user achieves deep work (e.g., `pomodoro`, `uninterrupted_mornings`).
- **Collaboration Preferences:** How the user works with others (e.g., `async_first`, `pair_programming`).

## Fields Requiring Extra Care ⚠️

Productivity apps often have access to highly sensitive or private information. 
- **Do not send raw task lists or full task names.** Instead, summarize the pattern. For example, instead of sending "Buy anniversary gift for Sarah", send "Personal task management".
- **Do not expose private documents or calendar event details.** Filter out attendee names, locations, and meeting titles. Focus on the *habit* or *preference* (e.g., "Back-to-back meetings").

## Example Raw App Context Dumps

Here is an example of what an app might send to Memact. Notice how the app sends a summary of patterns rather than the raw task list.

```json
{
  "category": "productivity",
  "source_label": "Task Manager App",
  "evidence": {
    "title": "Weekly Planning Session",
    "project_area": "frontend_development",
    "organization_style": "time-blocking",
    "focus_preference": "pomodoro"
  },
  "canonical_themes": ["productivity", "planning", "time-blocking"],
  "meaningful_score": 0.8
}
```

## Normalized Context Examples

The Memact engine normalizes this into a schema packet, filtering out any overbroad data (like raw task names) and summarizing the preferences:

```json
{
  "schema_version": "memact.schema_packet.v0",
  "packet_id": "schema_productivity_productivity_1",
  "category": "productivity",
  "schema_type": "productivity",
  "sub_schema": "general",
  "confidence": 0.8,
  "attributes": {
    "record_count": 1,
    "themes": ["productivity", "planning", "time-blocking"],
    "preferred_organization_styles": ["time-blocking"],
    "recurring_project_areas": ["frontend_development"],
    "focus_time_preferences": ["pomodoro"],
    "calendar_habits": []
  },
  "created_at": "2026-06-01T12:00:00Z"
}
```

## User-Facing Wiki Entry Templates

Users will see these insights translated into plain language in their Wiki:

- "You prefer to organize tasks using **time-blocking**."
- "You frequently work on projects related to **frontend development**."
- "You tend to use **pomodoro** techniques for focus time."

## Category-Level Permissions

Apps proposing productivity context should request:
- `productivity.read_preferences` - To read the user's high-level work preferences.
- `productivity.write_summary` - To propose summarized insights about how the user works.
