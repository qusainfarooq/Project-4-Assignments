Problem: High Low
We want you to gain more experience working with control flow and Booleans in Python. To do this, we are going to have you develop a game! The game is called High-Low and the way it's played goes as follows:

Two numbers are generated from 1 to 100 (inclusive on both ends): one for you and one for a computer, who will be your opponent. You can see your number, but not the computer's!

You make a guess, saying your number is either higher than or lower than the computer's number

If your guess matches the truth (ex. you guess your number is higher, and then your number is actually higher than the computer's), you get a point!

These steps make up one round of the game. The game is over after all rounds have been played.


Solution


import random

NUM_ROUNDS = 5

def main():
    print("Welcome to the High-Low Game!")
    print("--------------------------------")
    score = 0

    for round_num in range(1, NUM_ROUNDS + 1):
        print(f"Round {round_num}")
        user_num = random.randint(1, 100)
        comp_num = random.randint(1, 100)

        print(f"Your number is {user_num}")
        guess = input("Do you think your number is higher or lower than the computer's?: ").lower()

        # Input validation
        while guess not in ['higher', 'lower']:
            guess = input("Please enter either higher or lower: ").lower()

        # Check if the guess is correct
        if (guess == "higher" and user_num > comp_num) or (guess == "lower" and user_num < comp_num):
            print(f"You were right! The computer's number was {comp_num}")
            score += 1
        else:
            print(f"Aww, that's incorrect. The computer's number was {comp_num}")

        print(f"Your score is now {score}\n")

    # Final message based on performance
    print("Thanks for playing!")
    if score == NUM_ROUNDS:
        print("Wow! You played perfectly!")
    elif score >= NUM_ROUNDS // 2:
        print("Good job, you played really well!")
    else:
        print("Better luck next time!")

if __name__ == '__main__':
    main()
