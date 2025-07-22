import random

words = ['python', 'hangman', 'programming', 'developer', 'algorithm', 'function']

# Choose a random word
word = random.choice(words)
guessed_word = ['_'] * len(word)
attempts = 6
guessed_letters = []

print("🎮 WELCOM TO HANGMAN!")
print("Guess the word:")
print(' '.join(guessed_word))

while attempts > 0 and '_' in guessed_word:
    guess = input("\nEnter a letter: ").lower()

    if not guess.isalpha() or len(guess) != 1:
        print("⚠️ Please enter a single valid letter.")
        continue

    if guess in guessed_letters:
        print("🔁 You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    if guess in word:
        print("✅ Good guess!")
        for i in range(len(word)):
            if word[i] == guess:
                guessed_word[i] = guess
    else:
        attempts -= 1
        print(f"❌ Wrong guess! Attempts left: {attempts}")

    print(' '.join(guessed_word))

if '_' not in guessed_word:
    print("\n🎉 Congratulations! You guessed the word:", word)
else:
    print("\n💀 Game over! The word was:", word)


