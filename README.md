import random
import sys

# a random number should be chosen in the range 1-10
#as a player of th game, I should see some kind of header,welcome or game intro message in the console
random_number = random.randint(1, 10)
tries = 0
tries_remaining = 3
player_wins = False
start_game = print("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n Welcome To Tony's Number Guessing Game!!\n~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~")
player_name = input("\nWhat's your name player?    ")
print("\nOkay! You have three tries to guess. "+ player_name+ " Are you ready?")

# as a player of the game i should be continuously promted for a guess until i get it right
# need to check their guess to see if it matches the random number
# if player is not correct, need to ask them for a guess again

def test_number(guess_number, tries, tries_remaining, player_wins):
    if not guess_number > 0 or not guess_number < 11:
        print("That number is not between 1 and 10.")
        tries -= 1
        tries_remaining += 1
    elif guess_number == random_number:
        print("""\n         Congratulations! You are correct!!""")
        print("                  It took you {} tries.".format(tries))
        print("\n Awesome you win a GOLD STAR!!! Thanks for playing!!! ")
        player_wins = True
    elif guess_number < random_number:
        if tries_remaining > 0:
            print("I'm sorry, that number is too LOW. You have {} tries remaining.".format(int(tries_remaining)))
        else:
            print("Sorry, but my number was {}".format(random_number))
            print("You are out of tries. Better luck next time.")
    elif guess_number > random_number:
        if tries_remaining > 0:
            print("I'm sorry, that number is too HIGH. You have {} tries remaining.".format(int(tries_remaining)))
        else:
            print("\nSorry, but my number was {}".format(random_number))
            print("You are out of tries! Better luck next time!")
            sys.exit()
    return (tries, tries_remaining, player_wins)


def game(random_number, tries, tries_remaining, player_wins):
    while tries < 3:
        guess = input("\nGuess a number between 1 and 10.      ")
        tries += 1
        tries_remaining -= 1
        try:
            guess_number = int(guess)
            tries, tries_remaining, player_wins = test_number(guess_number, tries, tries_remaining, player_wins)
        except:
            print("\nThat's not a number silly! ")
            tries -= 1
            tries_remaining += 1
        if player_wins:
            break

            
game(random_number, tries, tries_remaining, player_wins)
