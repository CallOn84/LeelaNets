# Leela Chess Zero & Derived Nets
This repository contains all the nets that I have trained. This included Leela Chess Zero nets and any Lc0-derived nets, like Maia. 

If you have any questions, please let me know. Otherwise, you can download any nets here and play or test yourself.

# Elite Leela
Elite Leela is a project derived from Leela Chess Zero, where Leela was trained using the 19.7 million games from the Lichess Elite Database created by nikonoel from Lichess.

There's a Lichess Bot for Elite Leela, which you can find here: [https://lichess.org/@/EliteLeela](https://lichess.org/@/EliteLeela). It hasn't been active for a while, but you can check the games it has played with other users, as well as the 1,000 game match between it and Jellyfish 1.1 through our eight studies.

![Screenshot 2024-03-02 153042](https://github.com/CallOn84/LeelaNets/assets/55154899/e1f121e5-11dc-4c58-8ceb-6a105e4fbad8)
Figure 1: A test match carried out by me between Jellyfish 1.1 and Elite Leela

![Test Match 1](https://github.com/CallOn84/LeelaNets/assets/55154899/0f37e8ce-7ee7-41e2-94e6-6f9d279fcd7c)
![Test Match 2](https://github.com/CallOn84/LeelaNets/assets/55154899/af5c81e5-2556-4602-994d-262932839256)

Figure 2: A test match by NickIsntHere on the Leela Chess Zero Discord server, where he put several engines and Leela nets against Elite Leela. Based on CCRL rating and performance, it's rated at least 3350 on a GTX 1660 Super.

# Maia 2200
Maia 2200 is based on the excellent work by Reid Mcllroy-Young and his team, which you can read more about in their paper `"Aligning Superhuman AI with Human Behavior: Chess as a Model System"`. Maia 2200 was trained using games from the Lichess Open Database between players rated within the 2200 to 2299 Glicko2 rating range, filtered down to get a total of ~29 million games, spanning from 2013 to 2023. The net is currently in the middle of its training run, but it will become available for download through this repository.

The plan is to have it go through the same move-matching test that Reid and his team have developed, as that's the only way for me to know whether or not the Maia 2200 net I'm producing is working as intended. I will do a more crude test through a test match between Maia 1900 and Maia 2200 until I can replicate the `replication-run_model_on_csv.py` on Windows. I will also set up a Lichess Bot for users to play against once everything is done.
