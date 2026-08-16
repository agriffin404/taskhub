# TaskHub

A fast, self-contained task manager that lives in a single HTML file. No build step, no framework, no backend — just open it and go. Hosted as a static page on GitHub Pages.

**Live:** https://agriffin404.github.io/taskhub/

## Privacy

This repository contains **only the app** (`index.html`) — no personal data of any kind.

- All tasks, notes, and calendar events stay **on your own machine**: in the browser's local storage and in local JSON files you link via the browser's File System Access API.
- GitHub Pages is a one-way static host — it serves the app *to* your browser and never receives anything back. Nothing you do in the app is uploaded here.
- The data files (`taskhub-data.json`, `taskhub-events.json`, `taskhub-inbox.json`) are **intentionally never committed** to this repo.

## Features

- **Lists & views** — Personal / Work / combined / Today, with date buckets (No Due Date, Earlier, Today, Tomorrow, Later).
- **Inline editing** — click any chip to change due date, reminder, priority, list, or recurrence; quick one-line notes without expanding.
- **Recurrence** — daily, weekdays, weekly, monthly, annually; completing a task rolls the next due date forward.
- **Reminders & calendar** — set a reminder time; export any task to `.ics`, Google Calendar, or Outlook.
- **Notes with formatting** — bold/italic/underline, bulleted & numbered lists, hyperlinks, and **checklists** (`- [ ]` items you can tick right from the preview); everything carries through to synced apps.
- **Undo everywhere** — a bottom toast with Undo on completes, edits, moves, and deletes (plus multi-level Ctrl+Z).
- **Search, filters, sort & grouping**, bulk select, drag-to-reschedule, and a Recently Deleted bin (30-day retention).
- **Completed archive** — completed tasks older than 90 days are tucked into an archive section of your data file.
- **One-click triage** — "Move all to Today" on the overdue section; snooze chips (+1 day / +1 week / next Monday) on any task.
- **Compact density toggle**, light/dark themes, keyboard shortcuts, a weekly completions counter, and a sticky "Today's Calendar" rail with Teams join links on wide screens.
- **Installable** — a web manifest lets you install it as a standalone app (Edge/Chrome "Install app", iOS "Add to Home Screen").

## Microsoft 365 sync (optional)

The app produces a ready-made feed for two optional [Power Automate](https://make.powerautomate.com) flows:

- **Outbound** — pushes tasks to **Microsoft To Do** (matched by a hidden `[taskhub:id]` tag, so re-runs update instead of duplicate).
- **Calendar in** — pulls your Outlook calendar into the app's Upcoming Events panel.

Both are driven entirely by local JSON files; the flows run in your own tenant.

## Usage

1. Open the live URL above.
2. Click **Link all** and pick your `taskhub-*.json` files (the app reads and auto-saves to them locally; on `https` the permission persists).
3. Add and manage tasks. Everything saves locally and, if configured, syncs through your own Power Automate flows.

## Tech

Plain HTML/CSS/vanilla JavaScript in one file — no dependencies. State is kept in `localStorage` and mirrored to a local JSON file via the File System Access API.
