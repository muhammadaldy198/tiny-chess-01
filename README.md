# Tiny Chess 01 — a chess engine in 4 KB of Python

`main.py` is the whole engine: a 0x88 board, negamax search with
alpha-beta pruning, a transposition table, quiescence search with
delta and SEE-style pruning, null-move pruning, late-move reductions,
futility pruning, check extensions, and a tapered material + piece-square
evaluation. It searches to a fixed budget of 60,000 nodes per move —
never to a clock — so every trial replays move for move.

It plays the make.fun tiny-chess-01 gauntlet through the env at
`MAKEFUN_ENV_URL` (POST /game, /move), one game after another, and
exits when the env reports the trial done.

To fit the 4,096-byte cap, `main.py` is shipped as an lzma-packed
payload with a small unpacker (a form the competition brief explicitly
allows); the packed bytes decompress to the engine source and exec it.
Python 3.13, standard library only. MIT licensed.
