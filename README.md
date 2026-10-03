# Campus Library Management System

A small, demonstration-friendly Library Management System for an academic
Software Engineering project. It uses Flask, SQLite, server-rendered HTML,
and no database server or frontend build step.

## What it does

- Session-protected administrator login
- Dashboard with catalog, inventory, member, and loan counts
- Book CRUD with ISBN, title, author, category, and copy-count validation
- Search by title, author, ISBN, and category
- Member CRUD with enrollment number and active/inactive status
- Safe issuing: only an active member can borrow an available copy
- Safe returns: one loan is closed and one copy is restored atomically
- Complete current-loan and loan-history views
- First-run sample data: four books, two active members, and one inactive
  member

## Run it

Requirements: Python 3.10+ and internet access once to install Flask.

```powershell
cd library_management_system
py -m venv .venv
.\.venv\Scripts\Activate.ps1
py -m pip install -r requirements.txt
py app.py
```

If `py` is unavailable, replace it with `python`. Then open
<http://127.0.0.1:5000>.

Use the included demo administrator account:

```text
Username: admin
Password: admin123
```

The password is stored as a Werkzeug password hash, not as plain text. The
SQLite file (`library.db`) is created automatically beside the source files;
it keeps data between runs. To reset only the demo data, stop the server and
delete that file, then run the app again.

## Run the tests

```powershell
python -m unittest discover -s tests -v
```

The test suite uses a temporary SQLite database. It checks duplicate ISBN
protection, unavailable-book rejection, inactive-member rejection, and
issue/return inventory consistency.

## Project structure

```text
library_management_system/
├── app.py                 # Flask routes, login protection, application factory
├── database.py            # SQLite schema, first-run seed data, transactions
├── models.py              # Validation and book/member/circulation services
├── templates/             # Jinja HTML pages
├── static/css/style.css   # Responsive application styling
├── tests/test_lms.py      # unittest service-level tests
├── requirements.txt       # Flask only
└── SOURCE_ATTRIBUTION.md  # Starter-project credit and adaptation notes
```

## Demonstration flow

1. Sign in with the demo account.
2. Open **Books** and filter or add a catalog record.
3. Open **Members** and notice that inactive members are clearly marked.
4. Issue a book to an active member, then verify the dashboard count changes.
5. Return the book and view the completed record in **Loan history**.

## License and attribution

This academic adaptation is released under the [MIT License](LICENSE). The
starter project is credited in [SOURCE_ATTRIBUTION.md](SOURCE_ATTRIBUTION.md).
# LMS
