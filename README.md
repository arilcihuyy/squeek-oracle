# Squeek Oracle

A single page that reads Squeekchain's public API and suggests a call for the next
[Squeek or Sleep](https://squeekorsleep.mfbrat.com/) round.

**Live:** https://arilcihuyy.github.io/squeek-oracle/

## What it shows

- **Suggested call** for the next 10-minute round, derived from the live wheel reading
  (`api.squeekchain.com/v1/status`): a turning wheel above 12 rpm implies a zoomies round,
  a slow wheel implies jog, a still wheel implies nap. Every round is still decided by the
  hamster — the suggestion is a reading, not a promise.
- **A seven-day strip** of the hamster's real work, one cell per six-hour block, built from
  `v1/settlements?range=7d`.
- **Round record by time of day**, so you can see which blocks actually carry work.
- **Today, hour by hour**, from `v1/settlements?range=24h`.
- **Chain facts** from `v1/core` and `v1/economy/state`: Squeek block height, difficulty,
  cumulative work and $SQK minted against the cap.

No wallet, no signature, no transaction, no tracking. Static file, no build step.

## Notes on the data

`v1/settlements` returns hourly buckets for `range=24h`, six-hour buckets for `range=7d`
and daily buckets for `range=30d`, so the seven-day view is aggregated per six-hour block
rather than per hour.

## Build

It is one file. Open `index.html`, or serve the folder:

```
python3 -m http.server 8080
```

Built by [@0xAril27](https://x.com/0xAril27). Unofficial, not affiliated with Squeekchain.
