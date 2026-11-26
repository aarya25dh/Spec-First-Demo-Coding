# Tasks: Campus Event & Club Hub

**Input**: Design documents from `specs/001-campus-event-hub/`

**Prerequisites**: `plan.md`, `spec.md`, `research.md`, `data-model.md`, and `quickstart.md`

**Tests**: No automated test tasks are included because the specification does not request a test-first workflow. Validate the finished app manually using `specs/001-campus-event-hub/quickstart.md`.

**Organization**: Tasks are grouped by the prioritized user stories in `specs/001-campus-event-hub/spec.md`.

## Phase 1: Setup

**Purpose**: Create only the source files specified by the implementation plan.

- [ ] T001 Create the three root-level application files `index.html`, `styles.css`, and `app.js` as specified in `specs/001-campus-event-hub/plan.md`.

## Phase 2: Foundational

**Purpose**: Establish the shared page shell, visual base, and event data/storage used by all stories.

- [ ] T002 [P] Create the semantic HTML5 document shell, link `styles.css` and `app.js`, and add the shared main content container in `index.html`.
- [ ] T003 [P] Define base typography, color and spacing variables, reset, and responsive page layout with Flexbox and/or Grid in `styles.css`.
- [ ] T004 [P] Define future-dated mock events and initialize, load, and save the full event array under `campusEventHub.events.v1` in `app.js`; seed storage only when no saved list exists. Follow the canonical field definitions in `specs/001-campus-event-hub/data-model.md` for `Event.id`, `Event.title`, `Event.category`, `Event.date`, `Event.time`, `Event.location`, and `Event.description`; expose storage read/write errors for the UI.

**Checkpoint**: Shared structure, styling, and event state are ready for story implementation.

## Phase 3: User Story 1 - Discover upcoming events (Priority: P1) - MVP

**Goal**: Let students browse sample upcoming events and understand their essential details.

**Independent Test**: Run the app using `specs/001-campus-event-hub/quickstart.md`; without signing in, confirm sample event cards show title, category, date, time, and location in chronological order, and that an empty upcoming list has a clear empty state.

- [ ] T005 [P] [US1] Add the event-list section, accessible heading, empty-state element, and live storage-status region with stable selectors in `index.html`.
- [ ] T006 [P] [US1] Style the event list, event cards, empty state, and storage-status region for responsive layouts in `styles.css`.
- [ ] T007 [US1] Render upcoming events in chronological order, show title, category, date, time, and location on each card, and display empty/storage-error states in `app.js`; insert event content as text, not markup.

**Checkpoint**: User Story 1 works independently with the mock event list and no sign-in.

## Phase 4: User Story 2 - Filter events by category (Priority: P2)

**Goal**: Let students show all upcoming events or only Workshop, Social, or Sports events.

**Independent Test**: With mixed-category events present, select each category and confirm only matching upcoming cards remain; select All and confirm the full chronological list returns. Confirm the no-match empty state.

- [ ] T008 [P] [US2] Add accessible All, Workshop, Social, and Sports filter controls with stable selectors and a visible selected state hook in `index.html`.
- [ ] T009 [P] [US2] Style the category filter controls, selected state, hover/focus state, and narrow-screen layout in `styles.css`.
- [ ] T010 [US2] Connect the category controls to the event renderer in `app.js` so each selection shows only matching upcoming events, All restores the full list, and a category with no matches shows its empty state.

**Checkpoint**: User Stories 1 and 2 work together; filters do not alter saved events.

## Phase 5: User Story 3 - Submit a campus event (Priority: P3)

**Goal**: Let students submit valid events, retain them in the same browser, and see saved events in the list.

**Independent Test**: Submit an event with valid future details and confirm it appears as a card, survives a reload in the same browser, and clears the form. Confirm missing/invalid or past details and storage failures show clear errors without reporting an unsaved event as saved.

- [ ] T011 [P] [US3] Add the event submission form, required title/category/date/time/location controls, optional description, and field/status error regions in `index.html`.
- [ ] T012 [P] [US3] Style the submission form, validation feedback, and save/storage status for responsive layouts in `styles.css`.
- [ ] T013 [P] [US3] Implement form validation and event submission in `app.js`; follow `specs/001-campus-event-hub/data-model.md` for `Event.id`, `Event.title`, `Event.category`, `Event.date`, `Event.time`, `Event.location`, and `Event.description`. Save successfully before updating the displayed list, reset the active filter to All, clear fields only after success, and preserve the form with an error when saving fails.

**Checkpoint**: All three user stories work, including same-browser persistence and visible storage errors.

## Phase 6: Polish and Cross-Cutting Validation

**Purpose**: Verify the complete app against the documented acceptance scenarios and requested source layout.

- [ ] T014 Run every manual scenario in `specs/001-campus-event-hub/quickstart.md` against `index.html`, `styles.css`, and `app.js`; correct any failures while keeping application code in those three files only.

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: T001 creates the three application files.
- **Foundational (Phase 2)**: T002, T003, and T004 depend on T001 and can run in parallel because they edit different files.
- **User Story 1 (Phase 3)**: Depends on the foundation. T005 and T006 can run in parallel; T007 needs the shared event state and the list/status selectors from T005.
- **User Story 2 (Phase 4)**: Depends on User Story 1's event renderer. T008 and T009 can run in parallel; T010 needs the filter selectors from T008 and the renderer from T007.
- **User Story 3 (Phase 5)**: The complete story depends on User Stories 1 and 2 because successful submission must update the rendered list and reset the active filter. T011 and T012 can run in parallel; T013 also needs the form controls from T011.
- **Polish (Phase 6)**: T014 depends on the desired user stories being complete.

### User Story Dependencies

- **User Story 1 (P1)**: Depends only on Setup and Foundational phases; no dependency on another story.
- **User Story 2 (P2)**: Builds on User Story 1's event list and renderer.
- **User Story 3 (P3)**: Builds on the event list from User Story 1 and the active category filter from User Story 2.

### Parallel Opportunities

- After T001, run T002, T003, and T004 in parallel.
- After the foundation, run T005 and T006 in parallel.
- After User Story 1, run T008 and T009 in parallel.
- Within User Story 3, run T011 and T012 in parallel; after T011 is ready, T013 can proceed alongside T012.

## Parallel Examples

### User Story 1

```text
T005: Add event-list and status markup in index.html
T006: Style event list and cards in styles.css
```

### User Story 2

```text
T008: Add category filter controls in index.html
T009: Style category filter controls in styles.css
```

### User Story 3

```text
T011: Add event form and feedback regions in index.html
T012: Style the form and feedback in styles.css
```

## Implementation Strategy

### MVP First

Complete Setup and Foundational phases, then finish User Story 1 and validate its independent test. This delivers the smallest useful hub: students can see sample upcoming event cards without signing in.

### Incremental Delivery

1. Add User Story 1 for event discovery.
2. Add User Story 2 for category filtering.
3. Add User Story 3 for event submissions and same-browser persistence.
4. Run all scenarios in `specs/001-campus-event-hub/quickstart.md`.
