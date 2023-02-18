# Tic-Tac-Toe-Game-Python-:x::o:
A simple game of Tic Tac Toe in Python (User vs AI). Python libraries used: random

## Thoughts on starting this project
My second programming project, in Python. My approach to this traditional python project is through dictionaries (key, value relationships), 
and replacing the numbered values based on the key the user typed in to 'X' and 'O' to indicate that is the spot the player has chosen.

<br>

Computer program used for coding: VS Code

## Code description
Let's start with:
1. Imported Libraries
2. Defining the dictionary
3. Self-defined functions
4. Main code

<br>

<br>

**1. Imported Libraries**
```python
import random
```
Importing the 'random' library.

<br>

<br>

**2. Defining the dictionary**
```python
spots = {1: ' 1 ', 2: ' 2 ', 3: ' 3 ', 4: ' 4 ', 5: ' 5 ', 6: ' 6 ', 7: ' 7 ', 8: ' 8 ', 9: ' 9 '}
```
The 'spots' dictionary consists of 9 key value pair, representing a slot in the tic-tac-toe table, which the 'draw_board()' function uses to print out the table visually.

<br>

<br>

**3. Self-defined functions**
```python
def user_play():
    while True:
        try: 
            n = input("Choose position: ")
            if spots[int(n)] in [' 1 ', ' 2 ', ' 3 ', ' 4 ',' 5 ', ' 6 ',' 7 ', ' 8 ',' 9 ']:
                break
        except Exception:
            print("That position is not available!")
    return n
```
The 'user_play()' function is to get the user's input, as well as checking if that input is the desirable input of an int 1 to 9. That would be the slot the user chose to put in, and the loop will also check if that slot is already filled by either 
the user or the computer already. If that spot the computer chose already has an 'X' or 'O' as its value, the while loop will prompt the user for another input, until a
desired input is produced.


```python
def computer_play():
    while True:
        try: 
            n = random.randint(1, 9)
            if spots[int(n)] in [' 1 ', ' 2 ', ' 3 ', ' 4 ',' 5 ', ' 6 ',' 7 ', ' 8 ',' 9 ']:
                break
        except Exception:
            print("That position is not available!")
    return n
```
The 'computer_play()' function is to get a random, computer-generated input, from the number 1 to 9 that would be the slots the computer chose to put in, as well as checking if that slot is already filled by either 
the user or the computer already. If that spot the computer chose already has an 'X' or 'O' as its value, the while loop will prompt the computer for another random input, until a
desired input is produced.

<br>

The function then returns the generated input back to the main code.

<br>

```python
def user_winner(spots):
    if spots[1] == ' O ' and spots[2] == ' O ' and spots[3] == ' O ':
        print("You won!")
        return True 
    if spots[4] == ' O ' and spots[5] == ' O ' and spots[6] == ' O ':
        print("You won!")
        return True 
    if spots[7] == ' O ' and spots[8] == ' O ' and spots[9] == ' O ':
        print("You won!")
        return True 
    if spots[1] == ' O ' and spots[5] == ' O ' and spots[9] == ' O ':
        print("You won!")
        return True 
    if spots[3] == ' O ' and spots[5] == ' O ' and spots[7] == ' O ':
        print("You won!")
        return True  
    if spots[1] == ' O ' and spots[4] == ' O ' and spots[7] == ' O ':
        print("You won!")
        return True 
    if spots[2] == ' O ' and spots[5] == ' O ' and spots[8] == ' O ':
        print("You won!")
        return True 
    if spots[3] == ' O ' and spots[6] == ' O ' and spots[9] == ' O ':
        print("You won!")
        return True
    return False
```
The 'user_winner()' function is to check every round if the user has won after user has given an input. There is 8 possible combinations for the user to win. If these 3 keys in the dictionary are filled with an 'O',
then the user is declared a winner and returns True, else it returns False.

<br>

```python
def AI_winner(spots):
    if spots[1] == ' X ' and spots[2] == ' X ' and spots[3] == ' X ':
        print("You lost!")
        return True 
    if spots[4] == ' X ' and spots[5] == ' X ' and spots[6] == ' X ':
        print("You lost!")
        return True 
    if spots[7] == ' X ' and spots[8] == ' X ' and spots[9] == ' X ':
        print("You lost!")
        return True 
    if spots[1] == ' X ' and spots[5] == ' X ' and spots[9] == ' X ':
        print("You lost!")
        return True 
    if spots[3] == ' X ' and spots[5] == ' X ' and spots[7] == ' X ':
        print("You lost!")
        return True 
    if spots[1] == ' X ' and spots[4] == ' X ' and spots[7] == ' X ':
        print("You lost!")
        return True 
    if spots[2] == ' X ' and spots[5] == ' X ' and spots[8] == ' X ':
        print("You lost!")
        return True 
    if spots[3] == ' X ' and spots[6] == ' X ' and spots[9] == ' X ':
        print("You lost!")
        return True 
    return False
```

Similarly, the 'AI_winner()' function is to check every round if the AI has won after user has given an input. There is 8 possible combinations for the AI to win. If these 3 keys in the dictionary are filled with an 'X',
then the AI is declared a winner and returns True, else it returns False.

<br>

```python
def draw_board(spots):
    print(f"{spots[1]},{spots[2]},{spots[3]}\n{spots[4]},{spots[5]},{spots[6]}\n{spots[7]},{spots[8]},{spots[9]}")
```
The 'draw_board()' function basically prints out a visual look of the tic-tac-toe table using the dictionary key-value pairs. This makes it easy to switch the contents in each slot
based on the user/AI input and re-print it out visually when updating the board to the user.

<br>

<br>

```python
spots = {1: ' 1 ', 2: ' 2 ', 3: ' 3 ', 4: ' 4 ', 5: ' 5 ', 6: ' 6 ', 7: ' 7 ', 8: ' 8 ', 9: ' 9 '}
```
The 'spots' dictionary consists of 9 key value pair, representing a slot in the tic-tac-toe table, which the 'draw_board()' function uses to print out the table visually.

<br>

<br>

**4. Main code**
```python
def main(): 

    print('Welcome to a game of Tic Tac Toe! (User vs AI)\n')
    print('Select a position by typing the corresponding number!')
    draw_board(spots)

    playing = True

    while playing:
        x = user_play()
        spots[int(x)] = ' O '
        draw_board(spots)

        if user_winner(spots) is True:
            break
            
        if full_board() is True:
            print("Its a tie!")
            break

        y = computer_play()
        spots[int(y)] = ' X '
        print(f"Computer chose: {y}")
        draw_board(spots)

        if AI_winner(spots) is True:
            break

        if full_board() is True:
            print("Its a tie!")
            break
```
'while playing' sets a while loop of the game, where user input is taken (and checked at the same time in the 'user_play()' function), and replace the value of the key (user input) to 'O'
and then drawing the updated board with the 'O'.

Then the code will check the user win condition. If True, the code will exit the loop and print user win. If False, nothing happens and the code continues.

Then the code will also check if the board is full. If all the key-value pairs in the 'spots' dictionaries are filled with 'X' and 'O', then it is a full board and code will print 'Its a tie!'

The computer input is now taken (and checked at the same time in the 'computer_play()' function), and replace the value of the key (computer input) to 'X'
and then drawing the updated board as well as showing the user what number the computer has chosen.

Then the code will check the computer win condition. If True, the code will exit the loop and print user has lost. If False, nothing happens and the code continues.

Then the code will also check if the board is full. If all the key-value pairs in the 'spots' dictionaries are filled with 'X' and 'O', then it is a full board and code will print 'Its a tie!'

These lines of code will keep looping until the user/computer has won, or it is a full board.

## Output
```python
Welcome to a game of Tic Tac Toe! (User vs AI)

Select a position by typing the corresponding number!
 1 , 2 , 3
 4 , 5 , 6
 7 , 8 , 9
Choose position: 1
 O , 2 , 3 
 4 , 5 , 6
 7 , 8 , 9
Computer chose: 9
 O , 2 , 3
 4 , 5 , 6
 7 , 8 , X
Choose position: 5
 O , 2 , 3 
 4 , O , 6
 7 , 8 , X
Computer chose: 7
 O , 2 , 3
 4 , O , 6
 X , 8 , X
Choose position: 8
 O , 2 , 3 
 4 , O , 6
 X , O , X
Computer chose: 3
 O , 2 , X
 4 , O , 6
 X , O , X
Choose position: 6
 O , 2 , X 
 X , O , X
Computer chose: 2
 O , X , X
 4 , O , O
 X , O , X
Choose position: 4
 O , X , X
 O , O , O
 X , O , X
You won!
```

## Thoughts after the project
This project took me 3 days to complete as I struggled with the loops as I am still grasping the understanding of loops in programming, as well as creating conditions.

Furthermore, this expanded my knowledge on dictionaries, and the functionality of key-pair values.

This project also stretched the way on how I think as a programmer, such as being able to visualise the many scenarios that can occur in tic-tac-toe such as full board, and winning combinations, and
account for them in my code.

<br>

To be improved:
* Major flaw, the 'full_board()' function does not work, I have given up solving it at the time as I wanted to move on to new projects.
```python
def full_board():
    if spots[1] == (' X ' or ' O ') and spots[2] == (' X ' or ' O ') and spots[3] == (' X ' or ' O ') and spots[4] == (' X ' or ' O ') and spots[5] == (' X ' or ' O ') and spots[6] == (' X ' or ' O ') and spots[7] == (' X ' or ' O ') and spots[8] == (' X ' or ' O ') and spots[9] == (' X ' or ' O '):
        return True
    return False
```

* Too many if loops to check for User Win, Computer Win, should be possible to shorten them. I have learnt that in coding that you should always try not to
copy-paste your code and there is usually a way to shorten them e.g. into a loop, etc (based on what I know)
* Like all code, more features can definitely be added to make the game more interactive like making the AI smart, instead of making random choices on empty spaces on the board, making it easy for user to win.

## Special Thanks
Special thanks to harvestingmoon (https://github.com/harvestingmoon), for helping me check for the many bugs and solving them during this project :)

<br>

Have a gif:

![Semantic description of image](https://media.tenor.com/fWXyb86dSWMAAAAC/ok-cat.gif)
