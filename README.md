# Checkers
Class Project - create checkers frmom scratch
TUI: Ben
3 GUI: Olivia
4 Game Logic: Margaux
5 Bot: BJ

Changes in Our Design:
Our feedback comments were:
1) "The board class uses the "n" in "C_n", which constrains the type of board we 
would create. For example, there is a variant of Chess that is played on a 16x12 
board. We may want to be able to support boards of that size in the future. 
It would be better to be able to specify an arbitrary number of rows and columns"
2) "The piece class contains methods that would require consulting the state of 
the board, but there is no attribute that allows a Piece object to access the board"
3) AND we were also using a graph structure to represent our board and were 
told that an array would be better suited for this assignment

We responded to these comments by creating a board class that takes in row
and column, so that a board with varying sizes could be supported. Only in 
the checkers class, do we create specific board based on n. We also removed 
all methods from the Piece class as they were no longer necessary to our new
design. Finaly, we stopped using a graph structure and implemented a numpy 
array to display and organize the board and the game checkers. We then edited 
all of our oringal methods so that they aligned with our new numpy structure

Running our code:

Game Logic:
I didn't recieve any feedback in milestone 2 so I just continued following the 
same logic I had been using then. I have now fully completed the Game Logic, and
all the checkers logic works. I have included tests in test_checkers.py to 
demonstare that my code works! To test the checkers code, run the following 
command within the src/checkers.py file: $ pytest -s "test_checkers.py" -v


TUI:
I had just figured out how to use a stub to print a standard board using my TUI
code for milestone 2, so I've come a long way. For milestone 3 I have a fully
working TUI, which is implemented with both game logic and bot code. 

In order to run the TUI code from our git repository, write the following 
command:

$ ipython3 src/tui.py

This will automatically start the game. Choosing 1 player will test the bot 
implementation.

GUI:
GUI is now fully integrated with game logic and does not reference a mockup. 
It currently calls on the start() class at the end of the file - when run, 
game appears.  

The main structural difference I made between milestone 2 and 3 is the 
separation of a drawBoard class and a click class. This made it much easier 
to update the screen after each user interaction. 
This additionally made it much easier to integrate with game logic (which it 
was not in milestone 2).
I also added some graphic features: each piece captured appears on the opponents
side | each player's turn is specified | squares that are passed in a jump appear
in a differnt color than the destination squares of a jump | there is a resign 
button that, when pressed during one player's turn, announces the other player's
win | the start screen no longer takes in row, col specifications, only n.

Bot:

Didn't receive feedback in milestone 2. However, I updated the indexing of the
bot to make it easier to read and improved the preciseness of the center_squares
move classification and danger_moves classification. I also added the find_future_captures
and check_for_jumps methods to reduce code redundancy.

I also ranamed bot_mockup.py to test_bot.py. In this file you can test the smart
bot against the random bot in multiple games,multiple board sizes, and 
different colorsituations. The bot usually wins over 90% of matches.
This demonstrates the bot's functionality as best as possible without
GUI or TUI implementation. However, the bot can also run in the TUI against a
human player. The README's previous section describes the steps to run this.

I would like the bot to be run 100 times against the random bot. This is the 
default set in my bot_mockup file. 

Running the bot:

The bot.py file includes two classes:

    RandomBot: A bot that will just choose a move at random
    SmartBot: A bot that makes the best possible move based off a 
    classification system (more info in the bot.py docstrings). You can use
    test_bot.py to test the smart bot against the random bot. This can be done
    via running the following from the root of the repository:
    
    pytest src/test_bot.py

    This will enable one to test the smart bot's win % against a random opponent
    in the test_bot.py file. The test passes if the bots wins > 50% of games 
    for 100 games run against random.
