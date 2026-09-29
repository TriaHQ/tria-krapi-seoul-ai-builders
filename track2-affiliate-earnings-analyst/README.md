# Track 2: Affiliate Earnings Analyst

**Build an AI analyst that a Tria affiliate can chat with about the affiliate program and their own earnings.**

## The problem

Tria affiliates earn commissions when people they refer buy Tria products. They also earn a smaller cut when the referrals of affiliates they recruited buy something. Rates depend on a monthly tier, and refunds reverse commissions.

That makes earnings hard to follow. Affiliates ask "how much did I make?", "why is this commission $49.80 and not $37.35?" and "what do I need to reach Gold?". Today, a support person has to dig through the numbers to answer.

Your bot answers these questions itself. It combines the program rules with the affiliate's own data, and explains how each number was calculated.

## What you get

- **A program guide:** how referrals, recruits, tiers, commission rates and refunds work. It is a simplified version made for this event.
- **A synthetic dataset:** 30 affiliates in a recruiting tree, 440 referred customers, about 800 purchases and 1,500 commissions, from April to September 2026.

Read [PROGRAM_GUIDE.md](PROGRAM_GUIDE.md) first, then [SCHEMA.md](SCHEMA.md) for the tables.

## What your bot should do

Answer questions like these for the logged-in affiliate:

- "How much did I earn in September?"
- "Who are my top referrals?"
- "What tier am I, and how close am I to the next one?"
- "How much of my earnings come from my own referrals vs my recruits?"
- "Why did I earn $49.80 on this sale?"

### Stretch goals

- **What-if questions:** "If I refer 5 more card buyers this month, how much would I earn?"
- **Answer in Korean** as well as English.

## Requirements

- The bot answers only about the **logged-in affiliate**. Make the affiliate ID a setting; judges will switch it.
- It must refuse to reveal another affiliate's earnings, including their upline's.
- Rates and tier rules are only in the guide, not in the tables, so the bot has to use both.
- Figures must match the data. Check against [SAMPLE_QUESTIONS.md](SAMPLE_QUESTIONS.md).

## Files

| File | What it is |
|---|---|
| [PROGRAM_GUIDE.md](PROGRAM_GUIDE.md) | How the affiliate program works |
| [SCHEMA.md](SCHEMA.md) | Tables, columns, and rules for reading them |
| [SAMPLE_QUESTIONS.md](SAMPLE_QUESTIONS.md) | Example questions with correct answers |
| `data.sqlite` | The whole dataset as one SQLite database |
| `csv/` | The same data, one CSV per table |
