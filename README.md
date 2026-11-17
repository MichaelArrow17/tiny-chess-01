# tiny-chess-01 entry (PHANTOM / Deng Aji)

A compact alpha-beta chess engine in 4 KB of Python.
`main.py` is an lzma-packed payload (allowed by the rules); the
readable source is in the workspace dev folder, not in this repo.

- 0x88 board, alpha-beta + quiescence, transposition table,
  killer moves, MVV-LVA ordering, iterative deepening to a
  fixed 60,000-node budget, never a clock.
- Piece-square evaluation with endgame king centralisation,
  bishop-pair bonus, root repetition avoidance.
- Plays the env over HTTP (POST /game, /move) and is
  deterministic: same position, same move.

## Test (local, practice trials, kit env server)
- trial-0 (v1, 40k nodes): 1W 3D 2L, 2.5/6, Elo 1191
- trial-1 (v2, 60k nodes): 1W 2D 3L, 2.0/6, Elo 1099
- trial-2b (packed main.py, clean re-run): 4W 0D 2L, 4.0/6, Elo 1451
  (beat depth-2, depth-3, depth-4 and nodes-100k by mate; lost to
  nodes-250k and nodes-500k)
- Combined 8.5/18, Elo ~1250: above the 1154 floor, below the
  sunfish baseline (~1365) — not yet prize-eligible on current
  evidence. See BUILD_NOTES.md in the workspace.
