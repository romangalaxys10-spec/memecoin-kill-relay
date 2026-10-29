# Memecoin Kill Relay

<p align="center">
  <a href="https://z.ai/subscribe?ic=R0K78RJKNW"><img alt="z.ai coding plans - 10% OFF coupon" src="https://img.shields.io/badge/z.ai%20coding%20plans-10%25%20OFF%20coupon-blueviolet" /></a>
  <a href="https://zcode.z.ai/invite/ALWM9JUA"><img alt="Try ZCode free" src="https://img.shields.io/badge/Try%20ZCode-free%20invite-0969da" /></a>
</p>

Kill-first memecoin screening relay for [ZCode](https://zcode.z.ai) — five stages pass each
candidate down a chain and any single veto kills the coin.

> **Attribution & disclaimer**: this plugin was created based on an X.com post by
> [@0xNevsky](https://x.com/0xNevsky/status/2115535669082595790) (the "13-line prompt").
> It is **not verified and not personally tested by the author**. Memecoins can go to zero.
> Nothing here is financial advice; the relay screens, it does not predict returns.

## How it works

| Stage | Job |
|-------|-----|
| SCOUT | Surface fresh candidates (web: Dexscreener, Birdeye, X chatter) |
| FILTER | First veto gate: bundled wallets, dead/washed liquidity, fake volume, rugging deployers, unverified contracts |
| ANALYST | Thesis, holder distribution, smart-money presence, top risks |
| EXECUTOR | Paper trade plan only — physically cannot place a trade |
| RISK | Independent final veto on the whole file |

One KILL at any stage ends the coin. A survivor is not a guarantee; it is a coin that
did not die.

Install with the ZCode desktop app and run:

```
/kill-relay solana AI agent coins
```

## Install

**Option A — self-installable marketplace (recommended)**

1. Download or clone this repo to a folder.
2. In ZCode: **Plugin Marketplace → Add → Add Plugin Marketplace**, paste that folder path.
3. Open the market, then **Install** on *Memecoin Kill Relay*.

**Option B — manual**

Copy the folder into your ZCode workspace `plugins/` directory and add it to your local
`marketplace.json`.

## Safety rails built in

- Every non-obvious claim needs a source URL; unverifiable claims default to KILL.
- EXECUTOR never sends a transaction; there is no wallet integration at all.
- Each stage runs as a fresh subagent so no stage inherits the previous stage's bias.

## Try ZCode

- Coding plans, 10% off coupon: [z.ai/subscribe?ic=R0K78RJKNW](https://z.ai/subscribe?ic=R0K78RJKNW)
- Try ZCode free: [zcode.z.ai/invite/ALWM9JUA](https://zcode.z.ai/invite/ALWM9JUA)

## License

MIT.
