# Vault22 — Investments tab (alternative)

A clickable prototype of an alternative Investments tab for Vault22. Not the IM Portal, and not a
built feature — this is a design proposal put up so colleagues can assess it live.

**Live:** https://gflash-vault22.github.io/vault22-invest-tab/

## What it proposes

- **One Total value** as the parent number, with *Invested* and *Available to invest* as its components.
- **One advice boundary.** Managed portfolios and direct securities sit in separate accounts, because
  one is advised and the other is not. Execution-only rows carry a "bought without advice" notice.
- **Everything expands in place** — no tabs. A portfolio opens to its read-only look-through; a security
  opens to its full detail.
- **Three kinds of cash, named apart.** Only wallet cash is available to invest; portfolio cash sleeves
  count in a portfolio's value and return but are not available.
- **Statements are self-service** — concise or detailed, month-end or to-date, download or email.

## Reading it

The page opens with a dark band explaining the frame, then the app itself. Below the app are three
working sections worth reading: **Goals**, **Conventions** (rounding and currency rules) and
**Decisions**, which lists what is settled and what is still open. Items marked *Confirm* or *Open*
are the ones that need a view.

## About the numbers

Prototype only. The view is live, the numbers behind it are static:

- Managed portfolio values and performance are the specimen values from the Vault22 Concise and
  Detailed Statements for the quarter to 30 June 2026, and reconcile to the cent before rounding.
- Securities carry Uday's prototype figures.
- Fund names, tickers, ISINs and TERs are read from the Investment Management database.
- Goals, both price series, and income lines are illustrative.
- USDZAR 18.42 is a placeholder pending a rate-source decision.

No real client data appears anywhere in this repo.

## Statements

The **Generate statement** button resolves the Concise/Detailed and period selection to a file in
`statements/`:

| Selection | File |
| --- | --- |
| Concise · to 31 August 2026 | `statements/Vault22-Concise-2026-08-31.pdf` |
| Detailed · to 31 August 2026 | `statements/Vault22-Detailed-2026-08-31.pdf` |
| Concise · to today | `statements/Vault22-Concise-2026-09-06.pdf` |
| Detailed · to today | `statements/Vault22-Detailed-2026-09-06.pdf` |

Wiring is switched on by `window.STATEMENTS_BASE` in `index.html`, which is set to `statements/`
in this build, so the button serves the real PDFs. If it is ever unset the button falls back to an
explanatory message rather than opening a dead link.

The PDFs are specimens, marked `SPECIMEN · REAL MARKET PRICES, INVENTED HOLDINGS` on every page.

## Layout

```
index.html      the whole prototype — no build step, no dependencies
statements/     generated statement PDFs served by the Generate button
.nojekyll       serve files as-is, no Jekyll processing
```

Only external request is Google Fonts (Manrope, IBM Plex Mono). Everything else is inline.
