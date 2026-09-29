# Track 1 data and schema

Tables and rules for the Personal Finance Analyst. The problem statement is in [README.md](README.md).

## Files

- `data.sqlite`: all four tables in one SQLite database.
- `csv/`: the same tables as CSV files, one per table.
- `SAMPLE_QUESTIONS.md`: questions with correct answers, for checking your bot.

All data is synthetic. Amounts are in USD. It covers **2026-04-01 to 2026-09-30**; treat **2026-09-30 as today**, so "last month" means August 2026.

## Who is logged in

Build the bot for **Minji Park (`user_id` 1)**, and make the user ID a setting: judges may switch it to another user. The bot must only answer about the logged-in user.

## Tables

### `users`

| Column | Type | Meaning |
|---|---|---|
| user_id | integer | Primary key |
| name | text | Display name |

### `mcc_codes`

Merchant Category Codes: the standard 4-digit code that card networks assign to every merchant.

| Column | Type | Meaning |
|---|---|---|
| mcc | integer | Primary key, e.g. `5812` |
| description | text | e.g. `Eating Places, Restaurants` |
| category | text | Spending category, e.g. `Dining` |

### `card_transactions`

One row per card payment.

| Column | Type | Meaning |
|---|---|---|
| txn_id | integer | Primary key |
| user_id | integer | → `users.user_id` |
| ts | text | Local time, `YYYY-MM-DD HH:MM:SS` |
| merchant | text | Merchant name |
| mcc | integer | → `mcc_codes.mcc` |
| category | text | Same as `mcc_codes.category` for this MCC, copied here so no join is needed |
| amount_usd | real | Payment amount in USD, always positive |
| status | text | `completed`, `declined` or `refunded` (see below) |

### `trades`

One row per closed trade (a position opened and closed).

| Column | Type | Meaning |
|---|---|---|
| trade_id | integer | Primary key |
| user_id | integer | → `users.user_id` |
| ts | text | Time the position was closed |
| symbol | text | `BTC`, `ETH`, `SOL` or `HYPE` |
| side | text | `long` or `short` |
| notional_usd | real | Position size in USD |
| fee_usd | real | Trading fee paid |
| pnl_usd | real | Profit or loss **before** fees (negative = loss) |

## Rules your bot needs to know

- **Spend counts `completed` transactions only.**
  - `declined`: the payment was rejected and never charged.
  - `refunded`: the payment was charged and later fully refunded.
- **Net trading result** = `pnl_usd − fee_usd`.
- Some users have no trades.
- A few things in the data are worth noticing. Finding them is part of the challenge.
