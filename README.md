tiny-chess-4k

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/zincyyn7/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/zincyyn7/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A deterministic chess engine packed into 4,060 bytes of Python (an
lzma-compressed payload in main.py, split into chunks the shell can
carry). Negamax alpha-beta search with a transposition table,
quiescence search, null-move pruning, late-move reductions and check
extensions; evaluation is material + piece-square tables with a
tapered king term, bishop-pair bonus and pawn-structure penalties.
Fixed node budget per move (42k soft / 95k hard cap) - no clock, no
randomness, fully reproducible. Measured on the competition kit's own
practice gauntlets against the real house env: practice Elo ~1,384
over 11 games.

Run it
```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 -P -s main.py
```
Point MAKEFUN_ENV_URL at a running tiny-chess-01 environment server;
the engine polls /game and answers with /move.

Layout

- `main.py` - the whole engine: a chunked lzma payload plus a
  three-line loader. The payload is the readable engine source,
  compressed; nothing else is read at runtime.

License

MIT - see LICENSE.

Entered by zincyyn7-33 on make.fun.
