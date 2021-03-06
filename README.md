#Welcome to T3!

##Installing Lua
This game was programmed in Lua 5.2.2.  To run the game you'll need to have Lua installed.


###The Easy Way to Install Lua
* Download Lua [here](http://www.lua.org/download.html).
* Double click the file to "unzip".

Then open Terminal and run the following commands:

    cd lua-5.2.3/src
    make macosx
    sudo cp lua /usr/bin/lua
    lua

You'll know you have Lua correctly installed if, when you type the last command above, you get this:

    Lua 5.2.2  Copyright (C) 1994-2013 Lua.org, PUC-Rio
    >

###The Easier Way to Install Lua
Open Terminal and run the following commands:

    wget http://www.lua.org/download.html/ftp/lua-5.2.3.tar.gz
    tar xvzf lua-5.2.3.tar.gz
    cd lua-5.2.3/src
    make macosx
    sudo cp lua /usr/bin/lua
    lua

You'll know you have Lua correctly installed if, when you type the last command above, you get this:

    Lua 5.2.2  Copyright (C) 1994-2013 Lua.org, PUC-Rio
    >

##Running the Game
To run the game, 'cd' into the T3 directory and type:

    make play

##Running the Specs
To run the specs, you'll need to 'install' the telescope test library.  To do this, 'cd' into the T3 directory and type

    make install

Then to run the specs, type:

    make test

##Input/Output to File

I've designed the game's input/output ('in_out') functionality, so that a user can include two filenames for writing to a file and reading from a file, respectively.  The reading and writing functionality can be used together or separately (inputs could be read and output could be written to the console or outputs could be written to a file and inputs entered through the console.  In the case of reading inputs from a file and writing to the console, simply enter only a input filename.  In the case of reading inputs from the console and writing to a file, enter "none" for the input file argument and the output filename.

The sample file 't3_with_file_input_and_output.lua' to illustrate the game's configuration settings.
The sample file 'inputs.txt' illustrates how to configure input values.
The functionality requires that the input file specificed exists, however, the output file need not exist.

##Continuous Play Functionality

To run the game in 'continous mode', start the game and enter your desired configurations.  The game will loop one time. At the end of the loop's cycle, type 'yes' to play again, then 'yes' to keep the same configurations, and then enter a value to run the game loop multiple times.

The reasoning for this functionality is a common question I have heard often at 8th Light:

"But how do you REALLY know your Tic Tac Toe game is unbeatable??" - Doug Bradbury (with raised eyebrows)

 So, besides all of the TDD and unit testing, this was a way to be absolutely sure.

 The game is designed so that various player types can play the game as either player 1 or player 2.  Using the 'Input/Output to File' functionality, I set up a game between an 'Easy AI' player (gamepiece 'e') and a 'Hard AI' player (gamepiece 'h') with 'Easy AI' making the first move for each game.  I then ran the game 2,000 times and checked the output for an 'h wins' game decision.  The test was successful.  The 'Hard AI' player won 1,675 times.  The other 325 games were a tie. (Output can be found here: [Github Gist](https://gist.github.com/kellystee/4294eaa3f96e8ff4a217))

 The reasoning for using the 'Easy AI' player is because 'Easy AI' was designed to input random moves.  So using the 'Easy AI' player resulted in game cycles that were more varied.  Pitting two 'Hard AI' players against each other resulted in the same pattern of play for each game.