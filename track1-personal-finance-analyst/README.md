# Track 1: Personal Finance Analyst

**Build an AI analyst that a Tria user can chat with about their own money: what they spend on their card, and how their trading is going.**

## The problem

Tria users pay with a Tria card and trade crypto in the same app. Their transaction history holds the answers to questions like "where is my money going?" or "is my trading actually working?". But few people read through thousands of rows to find out.

Your bot is the analyst they don't have. It answers questions in plain language, backs them up with numbers and charts, and points out what the user should pay attention to.

## What you get

A synthetic dataset of 12 users over six months (April to September 2026):

- **Card transactions:** about 5,300, with merchant, category (MCC), amount and status.
- **Trades:** about 600 closed crypto trades, with symbol, long/short, size, PnL and fees.

Tables, columns and the rules for reading them are in [SCHEMA.md](SCHEMA.md).

## What your bot should do

Answer questions like these for the logged-in user:

- "How much did I spend on dining in August?"
- "Show my spending by category from July to September as a chart."
- "Which subscriptions am I paying for?"
- "Am I making or losing money on trading? How much am I paying in fees?"
- "Who are my top 5 merchants?"

### Stretch goals

- **Notice things without being asked:** "Anything unusual in my spending?" There are real patterns in the data worth finding.
- **Answer in Korean** as well as English.

## Requirements

- The bot answers only about the **logged-in user**. Make the user ID a setting; judges will switch it.
- It must refuse to reveal another user's data.
- Figures must match the data. Check against [SAMPLE_QUESTIONS.md](SAMPLE_QUESTIONS.md).

## Files

| File | What it is |
|---|---|
| [SCHEMA.md](SCHEMA.md) | Tables, columns, and rules for reading them |
| [SAMPLE_QUESTIONS.md](SAMPLE_QUESTIONS.md) | Example questions with correct answers |
| `data.sqlite` | The whole dataset as one SQLite database |
| `csv/` | The same data, one CSV per table |
