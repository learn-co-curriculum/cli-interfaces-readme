# CLI Interfaces

## The CLI Interface

CLI Applications generally follow a similar interface or user experience pattern. Imagine a CLI version of Tic Tac Toe. From a player's perspective, they would start the game by executing the `bin` for the game.

```
$ bin/tictactoe
```

The program will execute and generally greet the user with some text output:

```
$ bin/tictactoe

Hi! Welcome to Command Line Tic Tac Toe! Would you like to play? (Y/n)

```

The CLI will prompt the user for input and will hang until the user types something and presses enter. The CLI generally gives instructions for the expected input at a given prompt. In the example above, the greeting ends by asking the user if they would like to play. 

### User Input

The `(Y/n)` at the end is a common convention for telling the user that the following prompt is looking for a "Yes" or "No" input as an answer. It is also saying it expects that input as a single character, either `y` or `n`. The capital `Y` is suggesting the default input if the user types nothing and simply presses enter. Generally CLIs will accept "Yes"/"No" in many forms (`yes`, `no`, `N`, `n`) and still use the `y/n` convention.

```
$ bin/tictactoe

Hi! Welcome to Command Line Tic Tac Toe! Would you like to play? (Y/n)
y ↵
Great! Starting a new game...

   |   |   
-----------
   |   |   
-----------
   |   |   

Please select a square by entering 1-9, 1 for the top left and 9 for the bottom right:

```
*↵ is a Carriage Return symbol and simply means the "Enter" key was pressed. It is not literal. In the line above it is used to mean that the user entered in the `y` character at an input prompt and then pressed enter.*

For more complex interactions, the CLI must inform the user about the custom input prompt, just like in the example above: `Please select a square by entering 1-9, 1 for the top left and 9 for the bottom right:`. We just tell the player to enter a number, 1 through 9, to represent the square.

```
$ bin/tictactoe

Hi! Welcome to Command Line Tic Tac Toe! Would you like to play? (Y/n)
y ↵
Great! Starting a new game...

   |   |   
-----------
   |   |   
-----------
   |   |   

Please select a square by entering 1-9, 1 for the top left and 9 for the bottom right:
5↵

 O |   |   
-----------
   | X |   
-----------
   |   |   

Please select a square by entering 1-9, 1 for the top left and 9 for the bottom right:
7↵

 O |   |   
-----------
   | X |   
-----------
 X |   |   
```
*Etc...*

That's a pretty common interface pattern.

### Program Loop

CLI programs have to continue running and accepting input from the user until they are explicitly exited through sending a termination signal to the program by pressing `CTRL+C` (on OS X, on Windows and other environments it might be `ALT+C` or `COMMAND+C`), or by telling the program to quit or exit through some sort of input.

Imagine a Command Line Jukebox application to browse and play music through the Command Line (like Spotify or iTunes). It might look like this when run:

```
$ bin/jukebox

Hi! Welcome to Command Line Music.

What would you like to do?
I accept: list, play, help, and quit.
help↵

Main Menu Commands:
  help - Brings up this dialog.
  list - Will list all the songs in my collection.
  play - Will prompt for a song to play and play that song.
  quit - Will exit this program

What would you like to do?
I accept: list, play, help, and quit.
list↵

My songs are:
1. Shake It Off, by Taylor Swift
2. In An Aeroplane Over the Sea, by Neautral Milk Hotel
3. Reality Check, by Binary Star
4. Hey boy, hey girl, by the Chemical Brothers

What would you like to do?
I accept: list, play, help, and quit.
play↵

Please enter the song number you would like to play:
3↵

Reality Check, by Binary Star is currently open in your browser.

What would you like to do?
I accept: list, play, help, and quit.
```

Within the transcript of this program you can see the structure of the main application loop.

After the initial greeting, the application begins its main loop, which consists of:

1. Prompting the user for input: `What would you like to do?`
2. Defining the input interface: `I accept: list, play, help, and quit.`
3. Accepting user input by yielding to a prompt and waiting patiently for the user to press enter. *If the user never enters anything, the program will wait at this state forever until the process is otherwise terminated.*
4. Taking the user input and executing the appropriate sub-routine or procedure that represents that feature. If a user enters 'help', the program should print the help instructions.
5. Once that feature terminates, the program is back at the start of the main loop.

Any CLI application you build that necessitates a non-binary interface ("Do you want to play Tic Tac Toe?" vs "What game would you like to play?") will have a main loop interface as described above. 
<p data-visibility='hidden'>View <a href='https://learn.co/lessons/cli-interfaces-readme' title='CLI Interfaces'>CLI Interfaces</a> on Learn.co and start learning to code for free.</p>
