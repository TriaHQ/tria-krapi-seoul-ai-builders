# Tria × Krapi Seoul AI Builders

Ideathon problem statements and datasets. **Oct 2, 2026 · 14:00–17:00 KST · Seoul**

Build an AI chatbot on top of real-looking Tria data in about 2 hours, then demo it.

## Tracks

Each team picks **one** track.

| | Track | Build |
|---|---|---|
| 1 | [**Personal Finance Analyst**](track1-personal-finance-analyst/) | An AI analyst a Tria user chats with about their card spending and trading |
| 2 | [**Affiliate Earnings Analyst**](track2-affiliate-earnings-analyst/) | An AI analyst that explains the affiliate program and an affiliate's earnings |

Each track folder contains:

- `README.md`: the problem statement. Start here.
- `SCHEMA.md`: the tables, what each column means, and the rules your bot needs.
- `data.sqlite`: the whole dataset in one SQLite file.
- `csv/`: the same data as one CSV per table.
- `SAMPLE_QUESTIONS.md`: example questions with correct answers, for checking your bot.
- `PROGRAM_GUIDE.md` (Track 2 only): how the affiliate program works.

## Getting started

Get the files by cloning this repo, or with **Code → Download ZIP** at the top of this page.

Pick whichever format suits your tools:

- **SQLite** (`data.sqlite`): a real SQL database with no setup. Works with Python's built-in `sqlite3`, Node's `better-sqlite3`, or any SQL client.
- **CSV** (`csv/`): import into Supabase (the database Lovable uses), Google Sheets or pandas, or upload straight to ChatGPT or Claude.

**Using Lovable?** It can't read `data.sqlite`. In your project's Supabase, open **Table Editor → New table → Import data from CSV** and import each CSV from `csv/` as its own table.

Use any tools you like: Lovable, Cursor, Claude Code, Replit, v0, or your own code.

## Rules

- **The bot answers for one logged-in user.** Each `SCHEMA.md` names a default user. Make the user ID a setting: judges will switch it.
- **The bot must not reveal another user's data,** even if asked.
- **Check your answers** against `SAMPLE_QUESTIONS.md`.

## Judging

At demo time, judges ask your bot a set of questions that are **not** in this repo, sometimes as a different user. A working demo beats slides.

We look for:

- **Correct answers.** Figures match the data.
- **Useful insights.** The bot notices things, not just totals.
- **Good UX.** Charts where they help, clear explanations.
- **Bonus:** answers in Korean.

## About the data

All data is **synthetic**. The people, transactions and earnings are made up for this event (merchant names are real brands, used only for realism), and the Track 2 program is a simplified, fictional version of Tria's affiliate program. Amounts are in USD, and the data covers April to September 2026.
