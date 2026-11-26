# Research: Campus Event & Club Hub

**Date**: 2026-11-26

No unresolved technology choices remain: the user specified the stack, source files, and browser storage. The decisions below resolve the remaining design details for planning.

## Decision 1: Use a static browser-only application

- **Decision**: Implement with HTML5, CSS3, and vanilla ES6+ JavaScript; use no frameworks, packages, server, or build step.
- **Rationale**: This directly satisfies the requested stack and keeps the MVP easy to run and inspect.
- **Alternatives considered**: A framework, package-based build, or server-backed app. These add dependencies and/or architecture the user explicitly excluded.

## Decision 2: Keep application code in exactly three files

- **Decision**: Put page structure and accessible controls in `index.html`, responsive Flexbox/Grid presentation in `styles.css`, and mock data plus application behavior in `app.js`.
- **Rationale**: This follows the requested file layout and keeps the application understandable without extra source modules.
- **Alternatives considered**: Component directories, separate data modules, and test/build configuration. These are unnecessary for the specified small MVP and would expand the source layout.

## Decision 3: Seed and persist the full event list in browser storage

- **Decision**: Define the initial mock events in a JavaScript array. On first launch, initialize the namespaced `localStorage` event key from that array. Load the event list from storage on later launches and save valid submissions back to it.
- **Rationale**: The seed array provides demonstration content; browser storage keeps student submissions available after reload without an account or database.
- **Alternatives considered**: Keeping submissions in memory only, which loses them on reload and conflicts with the user's `localStorage` requirement; a server/database, which is outside MVP scope.

## Decision 4: Make storage failures visible

- **Decision**: If stored events cannot be read or saved, show a clear message. Do not report a submission as saved unless the storage write succeeds; preserve the form contents so the student can retry.
- **Rationale**: This avoids silently losing user input or presenting an unsaved event as durable.
- **Alternatives considered**: Silently falling back to memory-only behavior, which would make persistence unreliable and mislead students.

## Decision 5: Use local campus date and time values

- **Decision**: Represent event dates as calendar dates and times as local clock values, and compare them using campus-local time for upcoming-event sorting and validation.
- **Rationale**: The spec assumes campus-local time and does not require time-zone conversion or an external service.
- **Alternatives considered**: UTC timestamps and time-zone configuration, which add complexity not needed for this single-campus MVP.
