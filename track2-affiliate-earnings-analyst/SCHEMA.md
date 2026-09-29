# Track 2 data and schema

Tables and rules for the Affiliate Earnings Analyst. The problem statement is in [README.md](README.md).

## Files

- `PROGRAM_GUIDE.md`: how the affiliate program works. **Read this first.** Your bot needs these rules too.
- `data.sqlite`: all four tables in one SQLite database.
- `csv/`: the same tables as CSV files, one per table.
- `SAMPLE_QUESTIONS.md`: questions with correct answers, for checking your bot.

All data is synthetic, and the program is simplified for this event. Amounts are in USD. It covers **2026-04-01 to 2026-09-30**; treat **2026-09-30 as today**, so "this month" means September 2026.

## Who is logged in

Build the bot for **Jiwoo Han (`affiliate_id` 7)**, and make the affiliate ID a setting: judges may switch it to another affiliate. The bot must only answer about the logged-in affiliate.

## Tables

### `affiliates`

| Column | Type | Meaning |
|---|---|---|
| affiliate_id | integer | Primary key |
| name | text | Display name |
| parent_affiliate_id | integer | The affiliate who recruited this one. Empty for top-level affiliates |

### `referred_users`

Customers who signed up through an affiliate.

| Column | Type | Meaning |
|---|---|---|
| user_id | integer | Primary key |
| name | text | Display name |
| affiliate_id | integer | → `affiliates.affiliate_id`, the affiliate who referred this user |

### `sales`

Purchases made by referred users.

| Column | Type | Meaning |
|---|---|---|
| sale_id | integer | Primary key |
| user_id | integer | → `referred_users.user_id` |
| product | text | `premium_card`, `signature_card` or `membership` |
| amount_usd | real | Price paid |
| ts | text | Purchase time, `YYYY-MM-DD HH:MM:SS` |
| status | text | `paid` or `refunded` |

### `commissions`

Money earned by affiliates from sales. One sale creates up to two rows (see the guide).

| Column | Type | Meaning |
|---|---|---|
| commission_id | integer | Primary key |
| affiliate_id | integer | → `affiliates.affiliate_id`, who earns this commission |
| sale_id | integer | → `sales.sale_id` |
| level | integer | `1` or `2` (see the guide) |
| tier_at_time | text | The earning affiliate's tier in the month of the sale. Only matters for Level 1: Level 2 always pays 5% |
| amount_usd | real | Commission amount |
| status | text | `earned` or `reversed` (the sale was refunded) |

## Rules your bot needs to know

- **Earnings count `earned` commissions only.**
- A commission's month is the month of its sale (`sales.ts`).
- **Rates and tier rules are in `PROGRAM_GUIDE.md`, not in the tables.** To explain *why* an amount was earned, the bot has to combine the guide with the data.
