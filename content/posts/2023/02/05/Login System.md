---
title: "Login System"
date: 2023-02-05T13:43:03Z
draft: false
---

# Write Up
This program is my implementation of a secure login system. This system is designed to use hashing and salting to maximise security. Hashing is a one-way cipher that prevents a hacker from seeing the passwords that are stored. Hashes are not reversable but the same input will always provide the same output. This is preferable to encription because the reversal process is mathematically impossible. The salting makes it impossible to perform a rainbow table attack meaning the hacker's only option is to use brute-force methods such as a dictionary attack. During this project, I have learnt how to use hashing and salting, and I have also learnt why they are useful in computing.

# Code
```python
import json
import hashlib
import secrets


# Static Values
SALT_SIZE = 4096

# This function produces a hash and a salt for the user's password
def hash_password(password, salt):
	p = f"{password}{salt}"
	h = hashlib.sha3_512(p.encode("UTF-8")).hexdigest()
	return h

# Function to save live credentials to persistent disk storage.
def save_credentials():
    with open("creds.json", "w+") as f:
	    f.write(json.dumps(credentials))

credentials = {}

# This opens creds.json and reads it
try:
    with open("creds.json", "r") as f:
        credentials = json.loads(f.read())
except FileNotFoundError:
    print("New Datafile Created!")

# This infinate loop asks the user what they want to do until they enter 3 (break)
while True:
    menu = int(input("1) Login\n2) Sign Up\n3) Exit\n: "))

    # Login option
    if menu == 1:

        # Asks the user for their username and then password. Then the password is hashed and salted.
        UserReq = input("What is your username: ")
        PassReq = hash_password(input("What is your password: "), credentials[UserReq]["salt"])

        try:
            # Comparing the hashed password to the password they entered after hashing
            if credentials[UserReq]["hash"] == PassReq:
                print("Logged in!")
            # If they don't match, the program prints, "Login failed!"
            else:
                print("Login failed!")
        # If there is a username that doesn't exist, we would get a key error. Instead we print "Login failed!"
        except KeyError:
            print("Login failed!")

    elif menu == 2:
        NewUser = input("Please select a username: ")
        NewSalt = secrets.randbits(SALT_SIZE)
        NewPass = hash_password(input("Please select your password: "), NewSalt)

        # Checks username is available before proceeding with sign up process.
        try:
            credentials[NewUser]
            print("Username unavailable! Please select another.")
        except KeyError:
            credentials[NewUser] = {"hash": NewPass, "salt": NewSalt}
            print("Sign up succesful.")
            save_credentials()

    # If the user enters 3, the program will exit.
    elif menu == 3:
        print("\nGoodbye!")
        save_credentials()
        break

# On exit, saves the live credentials to persistent storage.
save_credentials()
```