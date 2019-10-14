# Project 1f: Stupid Checkers

Let's play a simple game of checkers. Well, stupid checkers. No jumping. Just moving and squishing your opponent.

First and formost, your script, `stupid-chekers.py`, is "started" for you. The game "state" (i.e., the positions of each piece on the playing board) is represented by a dictionary. Both books give some examples of using dictionaries for managing board state, so might serve as good reference.

The game itself starts with the board in the following state:
```
     A   B   C   D   E   F   G
   +---+---+---+---+---+---+---+
1  | r |   | r |   | r |   | r |
   +---+---+---+---+---+---+---+
2  |   | r |   | r |   | r |   |
   +---+---+---+---+---+---+---+
3  |   |   |   |   |   |   |   |
   +---+---+---+---+---+---+---+
4  |   |   |   |   |   |   |   |
   +---+---+---+---+---+---+---+
5  |   |   |   |   |   |   |   |
   +---+---+---+---+---+---+---+
6  |   | b |   | b |   | b |   |
   +---+---+---+---+---+---+---+
7  | b |   | b |   | b |   | b |
   +---+---+---+---+---+---+---+
```
Note that the above is ALSO an example of how you should display the game board whenever you want to show the board.

The only rules are as follows:

1. Play starts with "r" and then alternates one move at a time between "r" and "b".

2. Each move can go from an existing square to ANY other square.

3. The only exception is that it cannot go to a square occupied by a piece of the same type (i.e., "r" can't move to a place with an "r" already in it).

4. If one moves to a space occupied by another players piece, that piece is "removed" (i.e., in the above, if "r" moves from B2 to B6 then B2 will be empty, B6 will contain an "r", and there will simply be one fewer "b" pieces on the board.

5. Game is over when one player has no remaining game pieces. The player with remaining pieces is the winner.

And believe it or not, that's truly the only rules. Yes, it is in fact "stupid" checkers. If "r" doesn't win every time, then "r" has a serious problem.

Gameplay is very basic. Here's a partial example. `[SHOWBOARD]` is shown for brevity, but will display the current gameboard in a form similar to 7x7 grid shown above.
```
[SHOWBOARD]
r move from: B2
r move to: B6
[SHOWBOARD]
b move from: A7
b move to: B6
[SHOWBOARD]

... clipped for brevity ...

[SHOWBOARD]
r move from: G1
r move to: F6
[SHOWBOARD]
r wins!!
GAME OVER
```

## REQUIRED IMPLEMENTATION NOTES 

0. First and foremost, don't panic. Start small and build up. Initialize your `board`. Then implement and "play with" (i.e., test and retest and retest) `showboard()`, just to get it showing the current board state. Then implement the `countpieces()` function and play with it. ONLY THEN move on to writing any of the game play logic. Slow, steady and step-by-step is the way to conquer any "medium-sized" program. And there's plenty of partial credit to be had.

1. As noted, you MUST create a single `board` variable to represent your game board as a dictionary.

2. You MUST define and use a function called `showboard()` that iterates over the `board` variable and displays the game board as shown in the example above.

3. You MUST define and use a function called `countpieces(color)` that iterates over the `board` variable and RETURNS the count of pieces on the board that match the `color` parameter. In other words,at the beginning, calling `countpieces('r')` should return `7` since there are 7 r's on the board.

4. When the player enters the from and to locations, you MUST implement basic error checking logic and enforce game rule #3. If the starting or ending square doesn't exist OR if the starting square is empty OR if the starting square is occupied by the other players piece OR if the ending square is occupied by a piece of the same type, print `INVALID MOVE` to the screen and `continue` to let the next player go (yep, you are to be MEAN to players who can't type or follow rules very well).

And a few hints:

5. Your main game play might work best as a `while True:` loop that will `break` only when somebody wins (i.e., one of the calls to `countpieces()` returns `0`)

6. The logic for `showboard()` may not be obvious because your "keys" will include letters and numbers, not just sequential numbers. Just to get your brain in the right general location, you might want to create a nested for loop to iterate over each of the board squares (row by row) in the right order:
```
        for row in range(1,8):    # 1..7
            # Print row "header" (+---+---, etc.)
            rowstr = ''  # will be used to construct the string for the actual row
            for col in ('A','B','C','D','E','F','G'):
                # Draw and check each square.
                # '', 'r' or 'b' should be in board[col + row].
                # Concatenate the value to the rowstr, including
                # the spaces and "|" required for formatting.
            # Print rowstr
```

7. You MIGHT also want to define and use a `move(from,to)` function that you can call that better encapsulates the logic of moving a piece. If I were to do this, I would have this `move()` function return True or False depending on whether the move was allowed.

## LOGISTICS 

Same basic deal as with the homeworks. 

1. From your AIST2120 folder, run `git clone [URL]` to make a local copy of this assignment. 
2. DO THE WORK 
3. TEST YOUR WORK A WHOLE LOT 
4. TEST IT SOME MORE LIKE YOU MEAN IT THIS TIME 
5. When done, run `git add .` 
6. Then run `git commit –m "type a clever message here"` 
7. Finally run `git push` to push your changes back up to GitHub 
8. Breathe a sigh of relief 

## OPTIONAL CHALLENGES 

1. Show the current "score" in your `showboard` function centered above the board in the form `r: 7  b: 7`.

2. In addition to 1, show a move counter above the board. For example `Move #7 -- r: 4  b:3`.

3. Be "nicer". Instead of skipping to the next player if there is an invalid move as described in implementation note #4 above, allow the player to keep trying to enter a valid move.
