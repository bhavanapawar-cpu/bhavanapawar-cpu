import os
import time

# Initialize board
board = [' '] * 10  # Index 0 is unused for convenience
player = 1

# Game status flags
Win = 1
Draw = -1
Running = 0
Game = Running

# Function to draw the Tic-Tac-Toe board
def DrawBoard():
    print(" %c | %c | %c " % (board[1], board[2], board[3]))
    print("___|___|___")
    print(" %c | %c | %c " % (board[4], board[5], board[6]))
    print("___|___|___")
    print(" %c | %c | %c " % (board[7], board[8], board[9]))
    print("   |   |   ")

# Function to check if a position is empty
def CheckPosition(x):
    return board[x] == ' '

# Function to check if a player has won
def CheckWin():
    global Game

    # Winning conditions
    winning_combinations = [
        [1, 2, 3], [4, 5, 6], [7, 8, 9],  # Rows
        [1, 4, 7], [2, 5, 8], [3, 6, 9],  # Columns
        [1, 5, 9], [3, 5, 7]             # Diagonals
    ]

    for combo in winning_combinations:
        if board[combo[0]] == board[combo[1]] == board[combo[2]] and board[combo[0]] != ' ':
            Game = Win
            return

    # Draw condition
    if ' ' not in board[1:]:
        Game = Draw
    else:
        Game = Running

# Clear screen function for cross-platform support
def clear_screen():
    os.system('cls' if os.name == 'nt' else 'clear')

# Game Introduction
print("Tic-Tac-Toe Game")
print("Player 1 [X] --- Player 2 [O]\n")
print("Please Wait...")
time.sleep(1)

while Game == Running:
    clear_screen()
    DrawBoard()
    
    if player % 2 != 0:
        print("Player 1's turn (X)")
        Mark = 'X'
    else:
        print("Player 2's turn (O)")
        Mark = 'O'

    try:
        choice = int(input("Enter the position [1-9]: "))
        if choice < 1 or choice > 9:
            print("Invalid position! Choose between 1-9.")
            time.sleep(1)
            continue
    except ValueError:
        print("Invalid input! Enter a number between 1-9.")
        time.sleep(1)
        continue

    if CheckPosition(choice):
        board[choice] = Mark
        player += 1
        CheckWin()
    else:
        print("Position already taken! Try again.")
        time.sleep(1)

clear_screen()
DrawBoard()

if Game == Draw:
    print("Game Drawn!")
elif Game == Win:
    winner = "Player 1" if (player - 1) % 2 != 0 else "Player 2"
    print(f"{winner} Won!")
Practical 5 A) simulation of ... game using Min-Max Search.py
Displaying Practical 5 A) simulation of tic – tac – toe game using Min-Max Search.py.
Practical 5 : Write the program to compute the MMm
