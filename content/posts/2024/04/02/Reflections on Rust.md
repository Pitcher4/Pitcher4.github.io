---
title: "Reflections on Rust"
date: 2024-04-02T12:30:43+01:00
draft: false
---

# Introduction
I recently learnt Rust - a compiled language - and this was my first time using one. I had a positive experience using it, however, there are a lot of differences between this and interpreted languages (such as Python). 

# Compiled Languages

## How They Work
Compiled languages work differently to interpreted languages. Firstly, the computer will translate the program into machine code all at once, which is the binary instructions the CPU can run. Compilation can take longer than interpretation, however, compiled programs are usually faster at run time. After it is translated, the program is stored as an executable file meaning it can be run many times without compilation again; it can also be run on computers which do not have the language the program was written in installed.

## Advantages
Compiling programs is useful because running the executable is usually quicker than interpreting programs written in languages such as Python. For production software, this is useful because there are no requirements on the end user (such having an interpreter installed). Furthermore, for closed-source software, the source code is protected because the end user is only provided with the executable.

## Disadvantages
In general, compiled languages will give less detailed error messages, but interpreted languages can give you what type of error it is and what line it is on. This is because with interpreted languages, execution will stop on the line of the error, meaning the computer knows the exact location of the error. Additionally, debugging may be harder with compiled languages because you have to compile every time you change something in your code.


# Rust

## About the Language
Rust is a modern, compiled language released in 2015. It was made by an employee at Mozilla as a personal project but has grown to be a widespread, popular language. Rust was built from scratch, not from another language. This is unlike other languages such as C++ which is built onto of C and Python which also runs on C. Rust prioritises efficiency, security and privacy, which are widely built into the structure of the language.

## Reflection on My First Project
Rust is a strongly typed language, meaning more information about the type is needed when declaring variables. Furthermore, once a variable is declared a specific type, we can’t use the variable for a different type, so we have to make a new one. Additionally, another feature of Rust is that its variables are immutable by default, meaning that the value can’t be changed after declaration. If we want to change the value of a variable, we have to use the keyword `mut` which allows the contents of the variable to be altered. This makes user error less likely was the developer has to be intentional about changing values.

### Mutability Example
```rust
let x: u8 = 5; // x is immutable and cannot be changed
let mut y: u8 = 5; // y is mutable and can be changed
```

# Conclusion
I enjoyed this project because it introduced me to Rust which is a modern language. Because of this, I am keen to use it again. I found writing a simple program will take longer as the language is strongly typed but Rust is very practical for bigger, formal projects.