# CodeAlpha-Task-1
import random

# Predefined list of words
words = ["python", "apple", "computer", "school", "hangman"]

# Choose a random word
word = random.choice(words)

# Create hidden word display
guessed_word = ["_"] * len(word)

# Track guesses
incorrect_guesses = 0
max_guesses = 6
guessed_letters = []

print("Welcome to Hangman!")
print("Guess the word one letter at a time.")

while incorrect_guesses < max_guesses and "_" in guessed_word:
    print("\nWord:", " ".join(guessed_word))
    print("Guessed letters:", ", ".join(guessed_letters))
    print(f"Remaining chances: {max_guesses - incorrect_guesses}")

    guess = input("Enter a letter: ").lower()

    # Validate input
    if len(guess) != 1 or not guess.isalpha():
        print("Please enter a single letter.")
        continue

    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    if guess in word:
        print("Correct guess!")
        for i in range(len(word)):
            if word[i] == guess:
                guessed_word[i] = guess
    else:
        print("Wrong guess!")
        incorrect_guesses += 1

# Game result
if "_" not in guessed_word:
    print("\nCongratulations! You guessed the word:", word)
else:
    print("\nGame Over! The word was:", word)
