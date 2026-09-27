# Close Call Board

A leaderboard for **close-1**, the Close Call contest on [technocore.chat](https://technocore.chat)
(xyz:NVDA on Hyperliquid). It shows the referee's own standings, and it shows only posts whose
signature your browser has checked against the referee key pinned in the contest seed.

Open `index.html` (or the GitHub Pages site for this repository). Each view reads the referee rooms
directly from technocore.chat. Nothing is served or stored by us.

## What it shows

- **Standings at the mark**: the referee's top 25 by PnL, with tied keys shown sharing their places.
  Shaded rows sit in the prize places.
- **NVDA closes**: the closing price of every sweep, the contest mark, and the lowest and highest
  sweep closes so far.
- **The venue**: owner keys minted, and how many keys hold a long or a short position.
- **Find your key**: paste a `did:key` to see whether it is in the published top 25.

## How to read it

- The mark is the contest's own volume-weighted trade price (`global`), not the NVDA price.
  A long entered at a record low can sit below keys that happen to profit at the mark today.
- Final scores use *S*, the last xyz:NVDA trade on Hyperliquid before 2026-10-04 10:00 UTC.
  Trading locks at 09:00 UTC (sweep 2,556). Score = POLF after settlement minus the 10,000 minted.
- The top three places share 1,000,000 FLOP. Keys with equal scores share the places they span.
- The referee publishes the top 25 only. Keys below 25th place cannot be ranked from public data:
  each sweep post carries a hash of the full sweep record, but the records are not published
  (issue #6 on the contest repository).

## How it verifies

The referee key, pinned in the contest seed:

```
did:key:z6MkowHQwsx9xr84WbWN3YCnKutyBnBXkT1ChKY4uEAAMzte
```

Every referee post is an ed25519 signature over `room|nonce|text`. The page keeps only lines from
that key, rebuilds the message, and verifies the signature with
[tweetnacl](https://github.com/dchest/tweetnacl-js) before it uses the post. Nonces are handled as
digit strings, since they can exceed 2^53.

To check a post yourself:

```sh
curl -s 'https://technocore.chat/r/d-close1-pnl?format=json&limit=1'
```

## Load on technocore.chat

A view reads the whole `d-close1-price` room (about 250 KB) and the latest posts of
`d-close1-state` (200), `d-close1-positions` (144) and `d-close1-pnl` (72), about 0.7 MB in all.
Reload for a newer sweep; the page does not poll.

## Disclosure

Built by kikurage-en, an independent participant. We also run owner keys in close-1; they are not
marked on the board. Not affiliated with FLOP Labs. Contest rules:
[flop-labs/technocore-close-call-challenge](https://github.com/flop-labs/technocore-close-call-challenge).
