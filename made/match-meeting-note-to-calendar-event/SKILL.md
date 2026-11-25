---
name: match-meeting-note-to-calendar-event
description: Rename a Notion AI meeting-note page so its title exactly matches the calendar event it belongs to. Use when asked to fix, match or clean up meeting-note titles against the calendar.
---

> Rename an AI meeting-note page so its title exactly matches the linked calendar event.

## Required inputs

- The AI meeting-note page.
- Read access to the page’s database and linked calendar event.

## Workflow

1. Load the meeting-note page and its parent data source.
2. Confirm the page contains an AI meeting-notes block and belongs to the intended database.
3. Confirm the page’s `tag` property contains `Notes`.
4. Identify the calendar event linked to the meeting note. Prefer explicit event metadata from the meeting note. If it is not exposed, use the note date, creation time, meeting time, course relation, and nearby calendar events to find one unambiguous match.
5. If no linked event exists or more than one event remains plausible, do not rename the page. Report the ambiguity.
6. Set the database title property to the event summary exactly, preserving capitalization, punctuation, spacing, emoji, and symbols.
7. Do not alter the calendar event, meeting-note contents, date, tags, relations, or any other property.
8. Reload the page and verify the title is an exact match.

## Expected result

Return a short confirmation naming the page and calendar event. If skipped, state the reason without making changes.
