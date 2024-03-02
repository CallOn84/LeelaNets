# Leela Chess Zero & Derived Nets
This repository contains all the nets that I have trained. This included Leela Chess Zero nets and any Lc0-derived nets, like Maia. 

If you have any questions, please let me know. Otherwise, you can download any nets here and play or test yourself.

# Elite Leela
Elite Leela is a project derived from Leela Chess Zero, where Leela was trained using the 19.7 million games from the Lichess Elite Database created by nikonoel from Lichess.

# Maia 2200
Maia 2200 is based on the excellent work by Reid Mcllroy-Young and his team, which you can read more about in their paper `"Aligning Superhuman AI with Human Behavior: Chess as a Model System"`. Maia 2200 was trained using games from the Lichess Open Database between players rated within the 2200 to 2299 Glicko2 rating range, filtered down to get a total of ~29 million games, spanning from 2013 to 2023. The net is currently in the middle of its training run but will become available for download through this repository when it becomes available.

The plan is to have it go through the same move-matching test that Reid and his team have developed, as that's the only way for me to know whether or not the Maia 2200 net I'm producing is working as intended. I will do a more crude test through a test match between Maia 1900 and Maia 2200 until I can replicate the `replication-run_model_on_csv.py` on Windows. I will also set up a Lichess Bot for users to play against once everything is done.
