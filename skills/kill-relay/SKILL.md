---
name: kill-relay
description: Kill-first memecoin screening relay. Five stages (SCOUT, FILTER, ANALYST, EXECUTOR, RISK) pass each candidate down a chain; a single veto at any stage kills the coin. Use when the user wants to vet a memecoin before touching it, run the kill-first desk, or asks for the "relay" / "kill-first" screen on Solana tokens (or any chain). Analysis and vetting only — EXECUTOR never sends a transaction without explicit human approval.
---

# Kill-First Memecoin Relay

Source: 0xNevsky's 13-line prompt on X (status 2115535669082595790), adapted into a
ZCode skill. The philosophy is kill-first: every stage hunts for reasons to kill the
coin, not reasons to buy it. One veto anywhere and the coin is dead. A coin that
survives all five stages is still not a guarantee — it is a coin that did not die.

## Rules of the relay

1. Each stage runs as a fresh Agent (general-purpose) so it has no loyalty to the
   previous stage's opinion. Pass forward only structured findings, never enthusiasm.
2. Any stage that cannot verify a claim reports it as UNVERIFIED, never as PASS.
3. A single KILL verdict at any stage ends the relay for that coin. Record which
   stage killed it and why.
4. EXECUTOR produces a paper plan only. No real trade, no wallet signature, no
   transaction without the user typing explicit approval in the session.
5. Web data beats vibes: cite the URL for every non-obvious claim. Unverifiable
   claims default toward KILL, not toward pass.

## Stage 1 — SCOUT

Given a theme, ticker, or "find me candidates": surface 3-5 fresh tokens via web
search (Dexscreener, Birdeye, X/Twitter chatter, Telegram call groups). Deliverables
per coin: name, ticker, chain, contract address, age, market cap, liquidity, 24h
volume, one-line hype narrative. No judgment yet.

## Stage 2 — FILTER (first veto gate)

For each candidate check the hard kill list. Kill immediately on any hit:

- Bundled wallets: top-10 holders control over ~35% with fresh cluster wallets.
- Dead or locked-exit liquidity: under $50k, or LP tokens held by a wallet with
  no lock/burn proof.
- Fake volume: volume dominated by self-swaps, wash patterns, or bot-only traders.
- Deployer history: same deployer or wallet cluster linked to a previous rug.
- Unverifiable contract: not source-verified, or honeypot-detector flags it.

Output per coin: KILL (with which rule) or SURVIVES with evidence URLs.

## Stage 3 — ANALYST

For survivors: narrative strength (is there a real community or an anthem-posting
bot ring?), holder distribution curve, smart-money presence (known wallets in/out),
liquidity depth vs. target position size, and a plain thesis: why would a second
buyer appear after us? Deliver: thesis in 3 sentences, top 3 risks, a suggested
entry/exit structure (paper only).

## Stage 4 — EXECUTOR

Turns the surviving thesis into a paper trade plan: position size as % of the
hypothetical bankroll, tranches, stop-loss level, take-profit ladder, invalidation
condition ("kill the plan if X"). This stage NEVER executes. Its output is a plan
document the human reviews.

## Stage 5 — RISK (final veto)

An independent reviewer that reads the whole file and tries to kill the plan one
last time: is the thesis circular? is the stop-loss reachable through slippage?
is the community organic? If RISK says KILL, the coin is dead. If RISK passes,
the plan goes to the human with a full audit trail of every stage's verdicts.

## Output format

End every run with a relay table:

| Coin | SCOUT | FILTER | ANALYST | EXECUTOR | RISK | Final |
|------|-------|--------|---------|----------|------|-------|
| $XYZ | ok | KILL (bundled wallets) | - | - | - | DEAD |

Plus, for any coin that reaches RISK: the full paper plan and the audit trail.
State plainly that survivorship is not investment advice and memecoins can still
go to zero.

## Disposable-bankroll note

The original prompt assumes money you can lose entirely. If the user has not said
so, ask once whether the bankroll is disposable before Stage 4; if they decline to
answer, cap the paper plan at 1% and say so.
