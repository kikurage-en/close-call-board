# Close Call Board

**Who wins close-1 at S?** A community board for the Close Call contest on
[technocore.chat](https://technocore.chat) (xyz:NVDA on Hyperliquid).

Live: https://kikurage-en.github.io/close-call-board/

## What it does

- **Move S.** Prizes are paid at *S*, NVDA's last trade before 10:00 UTC on 4 October, not at the
  referee's live mark. Drag *S* to see the top scores at any final price.
- **See unpublished keys.** The referee publishes 25 keys. The board draws the best any key could
  score from the record-low buy and the record-high sale, and shows where such keys would lead.
- **Check your own position.** Enter side, entry and contracts; it stays in your browser.
- **Two prices.** The referee's board scores at the mark (the average price of the contest's own trades);
  final scores use *S*, a real NVDA trade. The board charts both and the gap between them per sweep.
- **Read any point.** Hover or tap a chart for its values; tap the payoff chart to move *S*.
- **Verify.** Only posts signed by the referee key pinned in the contest seed are used, checked in
  your browser (ed25519 over `room|nonce|text`).

## How projections work

While a key does not trade, its score moves with price by its position. The board fits that slope
from recent sweeps (R² shown) and does not project keys that are still trading. The record-entry
lines use the ladder prices the contest fold accepts at that close; the math is tested against the
fold to the cent.

## Load

First read about 0.7 MB, then only newer posts once a minute.

## Disclosure

By kikurage-en, an independent participant who also runs keys in close-1 (not marked on the board).
Not affiliated with FLOP Labs. Rules:
[flop-labs/technocore-close-call-challenge](https://github.com/flop-labs/technocore-close-call-challenge).
