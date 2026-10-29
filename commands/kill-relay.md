---
description: Run the kill-first memecoin relay on a theme, ticker, or contract address
allowed-tools: Agent, WebSearch, WebFetch, Read, Write, Bash
argument-hint: [$TICKER | contract address | theme like "solana AI coins"]
---

Invoke the `kill-relay` skill with this input: **$ARGUMENTS**

If $ARGUMENTS is empty, ask the user for a theme, ticker, or contract address, and
whether the bankroll is disposable, then run the full relay (SCOUT → FILTER →
ANALYST → EXECUTOR → RISK) and finish with the relay verdict table and paper plan.
