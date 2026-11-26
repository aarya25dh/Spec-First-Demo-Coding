# Quickstart: Campus Event & Club Hub

## Prerequisites

- A current desktop or mobile web browser with JavaScript and `localStorage` enabled.
- Python 3 for the optional local static server command below, or another static file server.

## Run Locally

From the project root, start a static server:

```sh
python3 -m http.server 8000
```

Open `http://localhost:8000/` in the browser. The app uses no installation, build, or package commands. Keep `index.html`, `styles.css`, and `app.js` together in the project root.

## Manual Acceptance Checks

1. **Browse events**: Open the hub without signing in. Confirm sample event cards show title, category, date, time, and location in chronological order.
2. **Filter categories**: Select Workshop, Social, and Sports in turn. Confirm each view contains only that category; select All and confirm the complete upcoming list returns.
3. **Submit an event**: Enter a title, supported category, future local date and time, and location. Submit and confirm the new card appears, the form clears, and the filter resets to All.
4. **Verify persistence**: Reload the same page in the same browser. Confirm the submitted event remains visible.
5. **Reject invalid input**: Submit with a required field missing, then with a past date and time. Confirm each attempt is rejected, the relevant input is identified, and no rejected event appears.
6. **Check empty states**: Choose a category with no upcoming events and confirm the matching empty state is shown. Confirm the general empty state appears when there are no upcoming events.
7. **Check responsive layout**: Narrow and widen the browser viewport. Confirm cards, filters, and the form remain usable and legible.
8. **Check storage feedback**: If browser storage is blocked or unavailable, confirm the app clearly reports that events cannot be loaded or saved and does not report a failed submission as successful.

## Expected Outcome

The app runs as a static page, requires no account or database, and keeps submitted events in the same browser's local storage across reloads.
