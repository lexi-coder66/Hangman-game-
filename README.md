# Hangman-game-
In this game there will be predefined list of Country's names and it picks one randomly. The user guesses letter until it completes the word or run out of tries.

CODE:

import random

words = ['Finland', 'Sweden', 'Norway', 'Denmark', 'Iceland']

chosen_word = random.choice(words)
display_word = ['_' for _ in chosen_word]
guessed_letters = set()
tries = 7

print("Welcome to Hangman!")
print("Hint: The word is a country in Northern Europe.")
print("Guess the word: ", ' '.join(display_word))

while tries > 0 and '_' in display_word:
    print(f"Guessed letters: {', '.join(sorted(guessed_letters))}")
    guess = input("Guess a letter: ").lower()
    if len(guess) != 1 or not guess.isalpha():
        print("Please enter a single alphabetic character.")
        continue
    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue
    guessed_letters.add(guess)
    if guess in chosen_word.lower():
        found = False
        for idx, letter in enumerate(chosen_word):
            if letter.lower() == guess:
                display_word[idx] = letter
                found = True
        print("Correct! ", ' '.join(display_word))
    else:
        tries -= 1
        print(f"Wrong! Tries left: {tries}")
        print(' '.join(display_word))

if '_' not in display_word:
    print("Congratulations! You guessed the word:", chosen_word)
else:
    print("Game over! The word was:", chosen_word)
