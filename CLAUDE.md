# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Spendly** — a personal expense tracker web app built with Flask and SQLite. This is a step-by-step student project; many routes and the database layer are intentionally left as stubs to be implemented incrementally.

## Commands

```bash
# Activate virtual environment (required before running anything)
source venv/Scripts/activate        # Windows Git Bash
# source venv/bin/activate          # macOS/Linux

# Run development server (port 5001)
python app.py

# Run all tests
pytest

# Run a single test file
pytest tests/test_auth.py

# Run a single test by name
pytest -k "test_login"
```

## Architecture

```
app.py              — Flask app + all route definitions (single file for now)
database/
  db.py             — SQLite helpers: get_db(), init_db(), seed_db() (stub — students implement)
  __init__.py
templates/
  base.html         — Shared layout: navbar, footer, Google Fonts, global CSS/JS links
  landing.html      — Marketing page (hero, modal, footer links)
  register.html / login.html / terms.html / privacy.html
static/
  css/style.css     — Global styles
  css/landing.css   — Landing-page-specific overrides
  js/main.js        — Vanilla JS only — no frameworks
```

**Database**: SQLite via `expense_tracker.db` (gitignored). The `database/db.py` module must expose:
- `get_db()` — SQLite connection with `row_factory = sqlite3.Row` and `PRAGMA foreign_keys = ON`
- `init_db()` — creates tables with `CREATE TABLE IF NOT EXISTS`
- `seed_db()` — inserts sample data for development

**Templates**: All pages extend `base.html` via Jinja2 `{% extends %}`. The base template wires in `style.css` and `main.js` globally.

**JS rule**: Vanilla JS only — no libraries or frameworks. This is enforced throughout the project.

## Pending / Stub Routes

These routes in `app.py` return placeholder strings and are meant to be filled in during later steps:
- `GET /logout` — Step 3
- `GET /profile` — Step 4
- `GET /expenses/add` — Step 7
- `GET /expenses/<id>/edit` — Step 8
- `GET /expenses/<id>/delete` — Step 9
