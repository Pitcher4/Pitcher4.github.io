---
title: "Celsius / Fahrenheit Converter"
date: 2022-12-11T09:42:38Z
draft: false
---

# Write Up
Celsius / Fahrenheit converter will ask the user which equation they want to do and what temperatures they want to convert. 

I used Python for this project. I started by inputting information from the user whether they wanted to convert Celsius to Fahrenheit (by entering 1) or the other way round (by entering 2). If they wanted to exit the user could press 3. If the user enters 1, the computer will request an input from the user of the temperature and will then use the formula to calculate the value in Fahrenheit - **(*[celsius value]* \* 9/5) + 32** - and then output this value. If the user wanted to do the opposite, they would enter 2 and the computer would calculate the inverse operation - **(*[Fahrenheit value]* \* 5/9) - 32** - and then, as before, output the final answer in celsius. If an erroneous value, for example, 4 is entered (a number that isn’t accounted for in the program) the computer will print the following error message: **“ERROR! Make sure you only enter 1, 2, or 3.”**

During this project, I continued to develop my confidence using Python. I also furthered my knowledge of selection (**IF**, **ELIF** and **ELSE** statements) and how to use them.


# Code
```python
CorF = int(input("Enter 1 if you want to convert Celsius to Fahrenheit or enter 2 if you want to Convert Fahrenheit to Celsius or enter 3 if you want to end: "))

while True:

    if CorF == 1:
        c = float(input("Please enter a value in Celsius: "))
        f = (c * 9/5) + 32
        print(f"{c}ºC is {f}ºF")

    elif CorF == 2:
        f = float(input("Please enter a value in Fahrenheight: "))
        c = (f - 32) * 5/9
        print(f"{f}ºF is {c}ºC")

    elif CorF == 3:
        break

    else:
        print("ERROR! Make sure you only enter 1, 2, or 3.")
```