## expenseTracker

A simple **command-line expense tracker** written in Python. It lets you add, update, delete, list, and summarize expenses, and it **persists data to a local `tracker.json`** file on quit (and loads it automatically on startup if it exists).

---

## Features

- Add expenses with a description and amount
- Update an existing expense by ID
- Delete an expense by ID
- List all recorded expenses in a table
- Show a summary (total of all expenses)
- Save/load expenses to/from `tracker.json`

---

## Project structure

- `main.py` — app entry point (interactive CLI loop)
- `tracker.py` — `Tracker` class with commands + JSON persistence
- `expense.py` — `Expense` model (IDs, formatting, serialization)
- `README.md` — documentation

---

## Requirements

- Python **3.x**
- No third-party dependencies (standard library only)

---

## Installation

Clone the repository:

```bash
git clone https://github.com/felipeUrra/expenseTracker.git
cd expenseTracker
```

---

## Run

Start the interactive CLI:

```bash
python main.py
```

On startup, if `tracker.json` exists in the same directory, it will be loaded automatically.

---

## Usage (commands)

After running `python main.py`, you’ll be prompted for a command:

### `help`
Prints available commands.

### `add`
Adds a new expense.

You will be prompted for:
- `description`
- `amount` (must be a decimal number)

### `update`
Updates an existing expense **by ID**.

You will be prompted for:
- `id`
- `description`
- `amount`

### `delete`
Deletes an expense **by ID**.

You will be prompted for:
- `id`

### `list`
Prints all expenses in a table format:

- ID
- Date (`YYYY-MM-DD`)
- Description
- Amount

### `summary`
Prints the total of all expense amounts.

### `quit`
Saves expenses to `tracker.json` and exits.

---

## Data persistence (`tracker.json`)

Expenses are stored locally in `tracker.json` (created/overwritten on `quit`).  
Example structure:

```json
{
  "expenses": [
    { "date": "2026-03-26", "description": "Coffee", "amount": 3.5, "id": 1 }
  ]
}
```

---

## Notes / Known issues

- Descriptions are intended to disallow `-`, but the current validation function always returns `False`, so `-` is not actually blocked.
- The `update` command is intended to request an ID, but the current `tracker.py` implementation calls `updateExpense(...)` with the wrong parameters. If you want, I can propose a fixed version.
