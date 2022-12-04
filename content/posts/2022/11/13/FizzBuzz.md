---
title: "FizzBuzz"
date: 2022-12-04T15:07:14Z
draft: false
---

# Write Up
FizzBuzz is a mathematical game where a the computer counts from 1 to 100. If there is a multiple of 3 it will output Fizz, if there is a multiple of 5 it will output Buzz, and if it is a multiple of both 3 and 5, it will output FizzBuzz.

I decided to use Python for this project. I began this project by using a FOR loop to iterate through all of the numbers from 1 to 100. I then used an IF statment to evaluate each number; this checked whether the number was a multiple of 3 or 5 or both by calculating their modulus respectively. Modulus calculates the remainder of a division, so if the result of the calculation was 0, I knew the number was a multiple. The IF statment was ordered in the way that can be seen below because otherwise there could have been an unexpected result such as FizzFizzBuzz or BuzzFizzBuzz, which I will discuss in more detail below.

During this project, I improved my confidence using Python independently. I also learnt how to use modulus in order to calculate whether a number is a multiple of another. Furthermore, I strengthened my skills using Git and GitHub for version control.

When I first attempted this project, I was reciving an unexpected output where the program would print, for example: FizzBuzz, Fizz, Buzz, 15. I solved this by replacing the IF command after the first statment with either ELIF or ELSE, which prevented the subsequent statments from running if the prior one did.


# Code
```python
for num in range(1, 101):
    if num % 3 == 0 and num % 5 == 0:
        print("FizzBuzz")
    elif num % 3 == 0:
        print("Fizz")
    elif num % 5 == 0:
        print("Buzz")
    else:
        print(num)
```