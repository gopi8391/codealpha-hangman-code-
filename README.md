# codealpha-hangman-code-
import random

# List of 5 words
words = ["python", "computer", "school", "keyboard", "program"]

# Select a random word
word = random.choice(words)

# Create a list to store guessed letters
guessed = []

# Maximum incorrect guesses
attempts = 6

print("----- HANGMAN GAME -----")
print("Guess the word one letter at a time.")
print("You have 6 incorrect guesses.")

while attempts > 0:

    # Display the word
    display = ""

    for letter in word:
        if letter in guessed:
            display = display + letter + " "
        else:
            display = display + "_ "

    print("\nWord:", display)

    # Check if the word is completely guessed
    if "_" not in display:
        print("Congratulations! You guessed the word!")
        break

    # Take a guess from the user
    guess = input("Enter a letter: ").lower()

    # Check if the input is valid
    if len(guess) != 1 or not guess.isalpha():
        print("Please enter only one letter.")
        continue

    # Check if letter was already guessed
    if guess in guessed:
        print("You already guessed that letter.")
        continue

    # Add the guess to the list
    guessed.append(guess)

    # Check the guess
    if guess in word:
        print("Correct guess!")
    else:
        attempts = attempts - 1
        print("Wrong guess!")
        print("Remaining attempts:", attempts)

else:
    print("\nGame Over!")
    print("The correct word was:", word)
