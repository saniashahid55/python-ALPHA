[hangman.py](https://github.com/user-attachments/files/22176073/hangman.py)
import random 
words=["python","apple","laptop","chair","ocean"] ##LIST PREDEFINED OF WORDS 

#RANDOMLY SELECT WORD FROM LIST 
secret_word=random.choice(words)

#STEP 2 INITIALIZE GAME STATE 
guessed_letters=[] # To store all guessed letters
max_attempts = 6   # Limit to 6 incorrect guesses
attempts_left= max_attempts

## Step 3: Display Word Progress
#We show blanks (_) for unguessed letters.
def get_display_word(secret_word, guessed_letters):
  display = ""
  for letter in secret_word:
      if letter in guessed_letters:
        display += letter + " "
      else:
          display += "_ " 
  return display.strip() 

#STEP 4 MAIN GAME LOOPS 

while attempts_left > 0:
    print("\nWord:", get_display_word(secret_word, guessed_letters))
    print("Guessed letters:",guessed_letters)
    print("Attempts left:",attempts_left)

    guess = input("Guess a letter:").lower()

    # INPUT VALIDATION 
    if len(guess) != 1 or not guess.isalpha():
       print("Please enter a single valid letter.")
       continue
    if guess in guessed_letters:
       print("You already guessed that letter.")
       continue
    guessed_letters.append(guess)

    if guess in secret_word:
       print("Correct!")
    else:
       print("Wrong guess.")
       attempts_left -= 1 
    #check for win 
    if all(letter in guessed_letters for letter in secret_word):
        print ("Congratulations! You guessed the word:", secret_word)
        break 
else:
    print(" Game Over! The word was:",secret_word)
    






