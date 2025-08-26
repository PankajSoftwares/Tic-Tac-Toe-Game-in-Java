# Tic-Tac-Toe-Game-in-Java
This is a console based Tik-Tac-Toe-Game-in-java which is very interesting game and similar to the dashboard we refer to play.


Tic-Tac-Toe Game in Java

comments
Tic-Tac-Toe is a classic game that two people can enjoy together. It is played on a 3x3 grid where players take turns placing their marks, X or O, in empty spots. The main goal is to get three of the same marks in a row-horizontally, vertically, or diagonally.

We are going to build a Java program that lets two players play the Tic-Tac-Toe game right from the console. There will be a board with numbers from 1 to 9, and we have to select a spot. And when it's our turn, we have to choose a number to put the mark there, and the board will update after every move, and the game continues until someone wins or it ends in a tie.

Game Board Layout
The game board layout will look something like this:

      |---|---|---|        
      | 1 | 2 | 3 |
      |-----------|
      | 4 | 5 | 6 |
      |-----------|
      | 7 | 8 | 9 |
      |---|---|---|  
How to Play the Game
The steps to play the game are listed below:

Both players choose either X or O to mark their cells.
There will be a 3x3 grid with numbers assigned to each of the 9 cells.
The player who chooses X begins to play first.
He enters the cell number where he wishes to place X.
Now, both O and X play alternatively until one of the two wins.
Winning criteria: Whenever any of the two players has fully filled one row/ column/ diagonal with their symbol (X/ O), they win and the game ends.
If neither of the two players wins, the game is said to have ended in a draw.
Sample Input: Enter a slot number to place X in: 3

Sample Output:

      |---|---|---|        
      | 1 | 2 | X |
      |-----------|
      | 4 | 5 | 6 |
      |-----------|
      | 7 | 8 | 9 |
      |---|---|---|  
Sample Input:

Now, O's turn, Enter a slot number to place O in: 5

Sample Output:

      |---|---|---|        
      | 1 | 2 | X |
      |-----------|
      | 4 | O | 6 |
      |-----------|
      | 7 | 8 | 9 |
      |---|---|---|  
So, like this game will be continued.

Before you begin coding the project, it’s important to understand two key concepts used throughout:

Arrays: Arrays are used to store multiple values in a single variable. In this Tic-Tac-Toe game, we use a 1D array of size 9 to represent the 3x3 board, with each slot initialized to numbers 1–9.

Example:

// Creating a board with 9 positions

String[] board = new String[9];



// Filling the board with slot numbers (1 to 9)

for (int a = 0; a < 9; a++) {

    board[a] = String.valueOf(a + 1);

}

Conditionals (if, switch): Conditional statements help the program decide what to do next.

For Example:

if is used to validate input, check for a winner, or alternate turns.
switch is used in the checkWinner() method to determine all possible winning combinations.
Examples:

if statement:

// Example of an if condition to validate move

if (board[numInput - 1].equals(String.valueOf(numInput))) {

    board[numInput - 1] = turn;

} else {

    System.out.println("Slot already taken; re-enter slot number:");

}

switch case:

// Example of a switch statement used to check winning lines

switch (a) {

    case 0:

        line = board[0] + board[1] + board[2];

        break;

    case 1:

        line = board[3] + board[4] + board[5];

        break;

    // ... other cases to check rows, columns, and diagonals

}


Project Implementation



// A simple Java program to demonstrate

// Tic-Tac-Toe Game

import java.util.*;
public class Game {

static String[] board;

static String turn;

// CheckWinner method will decide the winner

static String checkWinner() {

for (int a = 0; a < 8; a++) {

String line = null;

switch (a) {

case 0:

line = board[0] + board[1] + board[2];

break;

case 1:

line = board[3] + board[4] + board[5];

break;

case 2:

line = board[6] + board[7] + board[8];

break;

case 3:

line = board[0] + board[3] + board[6];

break;

case 4:

line = board[1] + board[4] + board[7];

break;

case 5:

line = board[2] + board[5] + board[8];

break;

case 6:

line = board[0] + board[4] + board[8];

break;

case 7:

line = board[2] + board[4] + board[6];

break;

}


// For X winner

if (line.equals("XXX")) {

return "X";

}

// For O winner

else if (line.equals("OOO")) {

return "O";
}

}

for (int a = 0; a < 9; a++) {

if (Arrays.asList(board).contains(String.valueOf(a + 1))) {

break;

} else if (a == 8) {

return "draw";

}

}

System.out.println(turn + "'s turn; 
enter a slot number to place " + turn + " in:");

return null;

}


// To print the board

static void printBoard() {

System.out.println("|---|---|---|");

System.out.println("| " + board[0] + " | " + board[1] + " | " + board[2] + " |");

System.out.println("|-----------|");

System.out.println("| " + board[3] + " | " + board[4] + " | " + board[5] + " |");

System.out.println("|-----------|");

System.out.println("| " + board[6] + " | " + board[7] + " | " + board[8] + " |");

System.out.println("|---|---|---|");

}
public static void main(String[] args) {

Scanner in = new Scanner(System.in);

board = new String[9];

turn = "X";

String winner = null;

for (int a = 0; a < 9; a++) {

board[a] = String.valueOf(a + 1);

}


System.out.println("Welcome to 3x3 Tic Tac Toe.");

printBoard();

System.out.println("X will play first. Enter a slot number to place X in:");

while (winner == null) {

int numInput;

try {

numInput = in.nextInt();

// Check range

if (!(numInput > 0 && numInput <= 9)) {

System.out.println("Invalid input; re-enter slot number:");

continue;

}

// Check if slot is available

if (board[numInput - 1].equals(String.valueOf(numInput))) {

board[numInput - 1] = turn;

// Toggle turn

turn = turn.equals("X") ? "O" : "X";

printBoard();

winner = checkWinner();

} else {

System.out.println("Slot already taken; re-enter slot number:");

}


} catch (InputMismatchException e) {

System.out.println("Invalid input; re-enter slot number:");

in.nextLine(); // Consume invalid input to prevent infinite loop

}

}



// Final result

if (winner.equalsIgnoreCase("draw")) {

System.out.println("It's a draw! Thanks for playing.");

} else {

System.out.println("Congratulations! " + winner + "'s have won! Thanks for playing.");

}

​

in.close();

}

}

Output:

Below is the output of the above program :

Welcome to 3x3 Tic Tac Toe.

|---|---|---|

| 1 | 2 | 3 |

|-----------|

| 4 | 5 | 6 |

|-----------|

| 7 | 8 | 9 |

|---|---|---|

X will play first. Enter a slot number to place X in:

3

|---|---|---|

| 1 | 2 | X |

|-----------|

| 4 | 5 | 6 |

|-----------|

| 7 | 8 | 9 |

|---|---|---|
O's turn; enter a slot number to place O in:
5
|---|---|---|

| 1 | 2 | X |

|-----------|

| 4 | O | 6 |

|-----------|

| 7 | 8 | 9 |

|---|---|---|
X's turn; enter a slot number to place X in:
6
|---|---|---|

| 1 | 2 | X |

|-----------|

| 4 | O | X |

|-----------|

| 7 | 8 | 9 |

|---|---|---|

O's turn; enter a slot number to place O in:
1
|---|---|---|

| O | 2 | X |

|-----------|

| 4 | O | X |

|-----------|

| 7 | 8 | 9 |

|---|---|---|
X's turn; enter a slot number to place X in:
9
|---|---|---|

| O | 2 | X |

|-----------|

| 4 | O | X |

|-----------|

| 7 | 8 | X |

|---|---|---|

Congratulations! X's have won! Thanks for playing.

Steps to Run on IntelliJ IDE

Open IntelliJ IDE.

Create a New Java project.

Right-click on the src folder and create a new class like a class named Game.

Now, write your source code and ctrl+s to save it.

Now, to execute the program right-click the src folder and click on run as Java application.

You can check below screenshot for your reference.

output

Running the code
