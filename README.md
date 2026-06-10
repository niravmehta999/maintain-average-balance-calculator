# Average Balance Calculator

A simple browser-based tool to calculate the required daily bank balance for the remaining days of a quarter, so your quarterly average meets the minimum balance requirement.

## Live App

[https://niravmehta999.github.io/maintain-average-balance-calculator/](https://niravmehta999.github.io/maintain-average-balance-calculator/)

## What it does

Banks calculate your average balance over a quarter (or billing period). If the average falls below the minimum requirement, you get charged a penalty. This tool helps you stay on top of it.

Enter your quarter start/end dates and your current average balance — the app tells you exactly how much you need to keep in the account each day for the rest of the quarter to hit the target.

## Inputs

| Field | Description |
|---|---|
| Start Date | First day of the quarter |
| End Date | Last day of the quarter |
| Current Average Balance | Average of your daily closing balances from start date to today |
| Minimum Required Balance | Your bank's minimum average balance requirement (default: ₹50,000) |

## How the calculation works

```
total_days       = end_date − start_date + 1 (inclusive)
today            = current date in IST (UTC+5:30)
days_passed      = today − start_date + 1
remaining_days   = total_days − days_passed

sum_so_far       = current_avg × days_passed
total_needed     = min_balance × total_days
required_daily   = (total_needed − sum_so_far) / remaining_days
```

If `required_daily ≤ min_balance`, you're on track. The app also shows:
- **Excess kept so far** — how much above the minimum you've accumulated
- **Projected quarter average** — what your final average would be if you kept ₹0 for all remaining days (shows your true buffer)

## Usage

No installation needed. Open `index.html` directly in any browser, or use the hosted link above.

## Tech

Single HTML file — Tailwind CSS (CDN) + vanilla JavaScript. No build step, no backend.
