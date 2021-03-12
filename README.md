# Number_Guessing_Game
import random
import sys

random_number = random.randint(1, 20)
tries = 0
tries_remaining = 8
has_won = False
start_game = print("""---------------------------------------------------------------------------------------------------------------------------------------"""
"""                                                                         Welcome To Tony's Number Guessing Game!!                                                                              """ 
"""---------------------------------------------------------------------------------------------------------------------------------------""")
player_name = input("What's your name player?    ")
print('Okay! You have eight tries to guess. '+ player_name+ ' Are you ready?')


def test_number(guess_num, tries, tries_remaining, has_won):
    if not guess_num > 0 or not guess_num < 21:
        print("That number is not between 1 and 20.")
        tries -= 1
        tries_remaining += 1

    elif guess_num == random_number:
        print("""         Congratulations! You are correct!!""")
        print("                  It took you {} tries.".format(tries))
        print("Awesome you win a GOLD STAR!!! Thanks for playing!!! ")
        has_won = True

    elif guess_num < random_number:
        if tries_remaining > 0:
            print("I'm sorry, that number is too LOW. You have {} tries remaining.".format(int(tries_remaining)))
        else:
            print("Sorry, but my number was {}".format(random_number))
            print("You are out of tries. Better luck next time.")

    elif guess_num > random_number:
        if tries_remaining > 0:
            print("I'm sorry, that number is too HIGH. You have {} tries remaining.".format(int(tries_remaining)))
        else:
            print("Sorry, but my number was {}".format(random_number))
            print("You are out of tries! Better luck next time!")
            sys.exit()

    return (tries, tries_remaining, has_won)


def main(random_number, tries, tries_remaining, has_won):
    while tries < 8:
        guess = input("Guess a random number between 1 and 20.      ")
        tries += 1
        tries_remaining -= 1

        try:
            guess_num = int(guess)
            tries, tries_remaining, has_won = test_number(guess_num, tries, tries_remaining, has_won)

        except:
            print("That's not a number silly! ")
            tries -= 1
            tries_remaining += 1

        if has_won:
            break

main(random_number, tries, tries_remaining, has_won)
