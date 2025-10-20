# Library (Django)

Small Django project for managing books.

## Quick summary
- Django project located at the repository root.
- Main app: `books` (home view: `books.views.BookListView` mapped to `/`).
- Intended for local development and experimenting with CLI agents (see "Agent" below).

## Requirements
- Python 3.8+
- Django (project requirements in `requirements.txt` if present)
- Windows (development commands below assume PowerShell/CMD)

## Setup (Windows)
1. Open terminal in project root:
   c:\Users\j\Desktop\SoftwareEngineering\django\library

2. Create and activate a virtual environment:
   - PowerShell:
     python -m venv .venv
     .\.venv\Scripts\Activate.ps1
   - CMD:
     python -m venv .venv
     .\.venv\Scripts\activate

3. Install dependencies:
   python -m pip install -r requirements.txt
   (or install Django manually: python -m pip install django)

4. Set environment variable for settings (optional for some workflows):
   - PowerShell:
     $env:DJANGO_SETTINGS_MODULE="library.settings"
   - CMD:
     set DJANGO_SETTINGS_MODULE=library.settings

5. Apply migrations and create a superuser:
   python manage.py migrate
   python manage.py createsuperuser

## Run the development server
python manage.py runserver
Open http://127.0.0.1:8000/ — the `books` app home view is mapped to the root URL.

## Tests
Run Django tests:
python manage.py test

(If you use pytest: python -m pytest)

## Agent (CLI usage)
Two common ways to run an "agent" from CLI:

1. Management command
- Create a management command at `books/management/commands/run_agent.py`.
- Run:
  python manage.py run_agent

2. Standalone script
- Create a script, e.g. `scripts/run_agent.py`, that sets `DJANGO_SETTINGS_MODULE` and calls `django.setup()`, then imports and runs the agent.
- Run:
  python scripts\run_agent.py

Add imports and logic to those files to call your agent implementation (e.g. `from books.agent import Agent; Agent().run()`).

## Project layout (top-level)
- library/           (Django project package)
- books/             (Django app with views, urls, models)
- manage.py
- requirements.txt
- scripts/            (optional: helper scripts)
- README.md

## Contributing
- Fork, create a feature branch, and submit a pull request.
- Keep changes focused and add tests for new behavior.

## License
Add a LICENSE file or specify a license here.
