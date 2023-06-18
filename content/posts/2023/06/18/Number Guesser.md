---
title: "Number Guesser"
date: 2023-06-18T17:08:05+01:00
draft: false
---

# Write Up
This project creates a random number between 1 and 100. The user has 10 guesses to figure out the number. 

If the user is incorrect, the computer will print the messsage either "Your guess was too high." or "Your guess was too low.".

However, if the user is correct, the computer will print "Correct!"

When the user is out of guesses, the following is outputted: "You have ran out of guesses! The number was [...]"

# Code
```python
import random

# Choosing a pseudorandom number using the random library
number = random.randint(1, 100)
# Defining the constant number of guesses
NUMBER_OF_GUESSES = 10

won = False

# Iterating the number of guesses using a for loop
for i in range(NUMBER_OF_GUESSES):
	# Ask the user to guess
	guess = int(input("What is your guess? Pick between 1 and 100: "))

	# Check for win
	if number == guess:
		print("Correct!")
		won = True
		break
	# Check if number too high
	elif guess > number:
		print("Your guess was too high.")
	# Check if number too low
	elif guess < number:
		print("Your guess was too low.")

# Ternary operator to print message if the player does not win
print(f"You have run out of guesses! The answer was {number}." if not won else "")
```

# Reflection

From this project, I futher developed an understanding of Python - more specificly IF, ELIF and ELSE statements. I learnt more about variables as in this projects I created a "won" boolean and a constant: "NUMBER_OF_GUESSES". Additionally, I gained experiance creating psuedorandom numbers.