# tiny-chess-01 entry

A 0x88-board chess engine in Python 3.13 (stdlib only), packed as an
lzma payload so `main.py` stays under the 4,096-byte cap (3,997 bytes).

Engine: alpha-beta with iterative deepening (depth 1-5, 60,000 nodes per
depth), quiescence over captures and promotions, check extensions,
null-move pruning (R=2), late-move reductions, killer moves, and a
transposition table with score bounds. Evaluation is incremental
(material + piece-square tables + bishop pair + endgame king table).
Repetition in the search path scores as a draw. Fixed node budget, no
clock, no randomness beyond the fixed Zobrist seed, no model calls.

Local practice trials (6 games each, vs depth-2..nodes-500k gauntlet):
trial-0 3.0/6, trial-1 1.5/6, trial-2 1.5/6; mean practice Elo ~1,099.
