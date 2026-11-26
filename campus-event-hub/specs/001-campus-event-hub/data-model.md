# Data Model: Campus Event & Club Hub

## Event

Represents one campus event shown in the hub.

| Field | Type | Required | Rules |
|---|---|---:|---|
| `id` | String | Yes | Unique and stable for the event |
| `title` | String | Yes | Must contain non-whitespace text |
| `category` | String | Yes | Exactly `Workshop`, `Social`, or `Sports` |
| `date` | String | Yes | Local calendar date in `YYYY-MM-DD` form |
| `time` | String | Yes | Campus-local time in `HH:MM` form |
| `location` | String | Yes | Must contain non-whitespace text |
| `description` | String | No | Optional event details |

## Data Sources and Persistence

- `app.js` defines an array of mock `Event` records for first-run content. Their dates must be generated or maintained so the sample events are upcoming when the app is used.
- On first launch, the app initializes `localStorage` from the mock array. On later launches, it reads the stored event list instead of adding the mock records again.
- Use a namespaced key such as `campusEventHub.events.v1`. The stored value is a JSON-serialized array of `Event` records.
- A successful student submission is appended to the in-memory event array and saved to `localStorage`; the list is then rendered from the current array.
- Stored events are local to the browser and origin. They are not synchronized across devices or users.
- If storage cannot be read or written, show an explicit status message. Do not claim a failed write was saved; retain form input when a save fails.

## Validation and Display Rules

- Require title, supported category, date, time, and location.
- Reject malformed date/time values and event date-times that are not in the future, using campus-local time.
- Keep optional descriptions optional.
- Display only upcoming events in chronological order. Category filters select `All`, `Workshop`, `Social`, or `Sports`.
- An empty upcoming list and an empty category result each have a visible, explanatory empty state.

## Relationships and Lifecycle

Events have no relationships to accounts, clubs, registrations, or other server-side entities.

For student input, the lifecycle is: draft → validation feedback if invalid, or validated → stored → displayed. The app must not show a submission as successfully saved before the storage operation succeeds.
