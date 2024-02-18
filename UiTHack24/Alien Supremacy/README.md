The aliens have composed a challenge for the petty humans using their own game against them - CHESS. Play out the sequence using the best possible moves starting as white. A chess piece move is represented by first stating where the piece moved from to where it is going.

This CTF challenge from the crypto category included a zip file containing various files for a chess game in python, aswell as an encoded flag.

By running chess.py, we are faced with a chess puzzle, where we have to find the winning sequence of moves. Like most chess puzzles, we are playing as white



```
$ python3 chess.py 
*********************************
|   |   |   | B | B |   |   | K |
|   |   |   |   |   |   |   | P |
|   |   |   |   |   |   |   | K |
|   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |
|   |   |   |   |   | P |   | P |
|   |   |   |   |   |   |   | P |
|   |   |   |   |   |   |   |   |
*********************************
From:
```

To find the winning sequence of moves, we can use a chess engine to find the moves for us. 

I used the Board Editor on lichess.org to set up the situation and then the Analysis Board to view the reccomended (winning) moves.

The winning sequence is as follows:

```
From: e8
To: h5

From: h6
To: h5

From: h8
To: g7

From: h7
To: h6

From: g7
To: e6

From: h5
To: h4

From: f6
To: g6

Sequence: e8h5h6h5h8g7h7h6g7e6h5h4f6g6
```

Flagg: UiTHack24{YouAreNotGM}

