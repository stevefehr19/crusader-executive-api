# Crusader Trading — Live Performance Dashboard

Public read-only trading performance surface for Steve Fehr.

## UI

- `dashboard.html` — premium Crusader black/brass/ivory mobile-first dashboard.
- Calendar, Journal, and Bot Breakdown buttons are interactive.
- Previous/next month, Today, Refresh now, and Refresh feed controls are active.
- The browser polls `journal.json` every 15 seconds with cache disabled.

## Journal feed contract

`journal.json` is the single published read source for this dashboard. Every closed trade row may include:

- `trade_id`
- `date`
- `strategy`
- `sleeve`
- `side`
- `qty`
- `contract`
- `entry_price`
- `exit_price`
- `pnl_usd`
- `exit_reason`
- `status`
- `lane`
- `source`

The same row drives the calendar P&L, daily trade list, monthly metrics, and sleeve attribution.

## Safety and privacy

- This surface is read-only and contains no order-routing capability.
- Forward/simulated and real-money lanes must never be silently mixed.
- Broker credentials, account IDs, tokens, private strategy source, and client/private trading evidence must not be published here.
- Seed values for 2026-09-14 are marked `PROVISIONAL` because they were reconstructed from a TradingView screenshot rather than a verified closed-trade export.

## Automatic ingestion still required

The static public site can read `journal.json` but cannot itself receive TradingView webhooks. A verified ingestion publisher/backend must update this file or a future compatible endpoint after each closed trade before the dashboard can be described as automatic end-to-end trade ingestion.
