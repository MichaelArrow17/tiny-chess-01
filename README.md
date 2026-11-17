# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/MichaelArrow17/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/MichaelArrow17/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A compact alpha-beta chess engine in 4 KB of Python.
`main.py` is an lzma-packed payload (allowed by the rules); the
readable source is in the workspace dev folder, not in this repo.

- 0x88 board, alpha-beta + quiescence, transposition table,
  killer moves, MVV-LVA ordering, iterative deepening to a
  fixed 90,000-node budget, never a clock.
- Piece-square evaluation with endgame king centralisation,
  bishop-pair bonus, root repetition avoidance.
- Plays the env over HTTP (POST /game, /move) and is
  deterministic: same position, same move.

## Run it

```sh
python3 main.py
```

(The entry is the kit env driver: it plays games served at
MAKEFUN_ENV_URL.)

## Test (local, practice trials, kit env server)
- trial-3 (90k nodes): 4W 1D 1L, 4.5/6, Elo 1545
- trial-4 (90k nodes, fresh instance): 2W 2D 2L, 3.0/6, Elo 1279
- trial-5 (90k nodes, third instance): 1W 4D 1L, 3.0/6, Elo 1279
- Combined mean Elo ~1368, essentially the sunfish baseline
  (~1365); all three trials clear the 1154 practice floor.
  See BUILD_NOTES.md in the workspace.

---

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
