[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Ktsumei/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Ktsumei/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# Tiny Chess 01 — a 4 KB Python chess engine

A chess engine in at most 4,096 bytes of Python (`main.py`), written to beat the
house baseline (sunfish's 4 KB engine) over the gauntlet of eight house engines.

## How it plays

`main.py` is the whole engine: a 0x88 board, negamax alpha-beta with iterative
deepening to a fixed node budget (never a clock, so replays are deterministic),
quiescence over captures and promotions, a transposition table keyed by Zobrist
hash, MVV-LVA capture ordering plus killer moves, and an evaluation of material
plus piece-square tables with a bishop-pair bonus and an endgame king table.

It talks to the trial env over HTTP (`POST /game`, `POST /move`), reads the
brief from `MAKEFUN_PROMPT_FILE`, and seeds any randomness from
`MAKEFUN_TRIAL_SEED`. It makes no model calls and reads no other file.

## Files

- `main.py` — the engine (Python 3.13, standard library only)
- `LICENSE` — MIT
- `.makefun/owner.json` — the entry wallet claim

Entered on make.fun.
