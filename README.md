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
Maia 2200 is based on the excellent work by Reid Mcllroy-Young and his team, which you can read more about in their paper `"Aligning Superhuman AI with Human Behavior: Chess as a Model System"`. Maia 2200 was trained using games from the Lichess Open Database between players rated within the 2200 to 2299 Glicko2 rating range, filtered down to get a total of ~29 million games, spanning from 2013 to 2023. The games were split into training and testing datasets using a training ratio of 95% (A typical training ratio used in Leela Chess Zero training), resulting in having a training dataset of ~27.55 million and a testing dataset of ~1.45 million games. The training was conducted on Tensorflow 2.10 and Python 3.7.

Two tests were conducted on Maia 2200. The first test was through a policy tournament match between Maia 2200 and Maia 1900 to determine how much strong Maia 2200 is over Maia 1900 in Elo (Ordo). Below is the command line used to initiate the policy tournament:
`lc0.exe selfplay --player1.weights=maia-1900.pb.gz --player2.weights=maia-2200-20k.pb.gz --openings-pgn=openings-dd-12ply-10000.pgn --policy-mode-size=12 --mirror-openings=true --tournament-results-file=test.pgn --games=20000 --parallelism=12 --backend=multiplexing --backend-opts=backend=cuda-fp16 --syzygy-paths=D:/Tablebases/3-4-5;D:/Tablebases/6-dtz;D:/Tablebases/6-wdl --logfile=log.txt`

The version of Leela Chess Zero used for the policy tournament was "0.31.0-dev+git.7532768 built Mar 6 2024", running on a Ryzen 5 5600X and an RTX 3070. Both models were given a 12-ply opening book made by Chad in the Leela Chess Zero's Discord server, which has 10,000 of the most frequently played opening lines with an 86.76% coverage of total games played by humans over-the-board and in correspondence chess, and both models played the same opening line using `--mirror-openings=true`. `--policy-mode-size=12` is the number of games per thread, -`-parallelism=12` is the number of threads available for the tournament, and `--backend=multiplexing` allows to construct larger batches from multiple games, among other things. Both models were given 3-4-5, 6-dtz, and 6-wdl syzygy tablebases for the endgame.

![Elo Rating of Maia 2200 Against Maia 1900 Over Time (10k to 400k)](https://github.com/CallOn84/LeelaNets/assets/55154899/1eb455b0-c6e5-4356-842b-7c5179b8a210)
Figure 1: A line chart showing the Elo (Ordo) rating of Maia 2200 over time, from 10k to the 400k model.

The second test was through the testing data set that the Maia Chess developers put together to calculate the move-matching accuracy of their models. The dataset can be found in their GitHub repository, but it essentially contains 10,000 per rating division of 100, totalling to 150,000 games. Using 8 threads and a move time of 10, the model ran through all the move within the dataset, outputting a move for each row, and is recorded in a new csv.bz2 file. The testing dataset and the results dataset were read and compared, and a accuracy percentage was calculated for each rating division of how many moves did the model get correct out of all the moves it ran through.

![image](https://github.com/CallOn84/LeelaNets/assets/55154899/41c240b2-9cfe-4f9f-b47e-e5580b5bbb8f)
Figure 2: The percentage of correct moves in every rating divison.
