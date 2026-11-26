
# SpecFirst Demo: Campus Event & Club Hub

A demo of **spec-driven development** using [GitHub Spec Kit](https://github.com/github/spec-kit) with GitHub Copilot. Instead of jumping straight into code, the project starts with a written spec, a plan, and a data model, and the implementation is meant to follow from them.

## The idea

A simple **Campus Event & Club Hub** web app where students can:

- 📅 **Browse** upcoming campus events as cards (title, category, date, time, location), sorted soonest-first
- 🏷️ **Filter** events by category: Workshop, Social, or Sports
- ➕ **Submit** a new event through a simple form, with validation for missing fields and past dates

**MVP constraints:** no login, no database, no framework, no build step. Just HTML5, CSS3 (Flexbox/Grid), and vanilla ES6+ JavaScript in three files (`index.html`, `styles.css`, `app.js`). Mock events seed the app, and everything is persisted in the browser's `localStorage`.

## What's in this repo

```
campus-event-hub/
├── specs/001-campus-event-hub/
│   ├── spec.md          # User stories (As a… I want… so that…) + Given/When/Then acceptance criteria
│   ├── plan.md          # Implementation plan & technical context
│   ├── research.md      # Decisions and alternatives
│   ├── data-model.md    # Event entity, fields, validation rules, localStorage schema
│   ├── quickstart.md    # Manual browser acceptance checks
│   └── checklists/      # Spec quality checklist
├── .specify/            # Spec Kit templates, scripts, workflow & constitution
└── .github/skills/      # Spec Kit Copilot skills (specify, clarify, plan, tasks, analyze, implement…)
```

## Workflow used

`constitution` → `specify` → `clarify` → `plan` → `tasks` → `analyze` → `implement`

Each step is driven by a Copilot skill, so the spec is the source of truth and the code is generated from it.

## Status

Spec, plan, and data model are complete. Implementation (`index.html`, `styles.css`, `app.js`) is the next step via `/speckit-tasks` and `/speckit-implement`.

## Tech

HTML5 · CSS3 · Vanilla JavaScript (ES6+) · `localStorage` · GitHub Spec Kit · GitHub Copilot
