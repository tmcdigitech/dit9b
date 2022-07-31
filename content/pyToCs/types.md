---
title: Explicit typing
weight: 20
---

Computers store all information as sequences of numbers,
and different kinds of information are encoded using
different methods. These different kinds of information
are known as *types*, and they exist in all programming
languages.

The Python interpreter allows the programmer to ignore
many of the issues of typing much of the time, as it
can infer a lot from the code. But you would have had
to convert numbers into text using the `str()` function,
and this is an example of *type conversion*.

C# requires you to be a lot more explicit about the types
of variables and their conversion, so you'll get a lot
more exposure to the idea of types.

## Common types

### int
Integers are whole numbers, positive or negative.
They are a fixed number of digits long, so there
is a maximum and minimum value you can store in one.

### float/double
Floating point is the most common way to store decimals; it stores them in scientific notation. There are a certain number of digits for the exponent, and a certain number for the mantissa. The fixed number of digits means there are values that can't be stored, so the computer will round to the nearest valid value. *Floats* are usually 32-bits (32 binary digits long), and *doubles* are, as their name might suggest, 64-bits long. This gives doubles much more room for extra digits, meaning far less likelihood of drifting and errors due to rounding.

### char/strings
Any time input is read in from the keyboard, or text output to the screen, strings of characters are involved. A single entity, like '`a`', '`%`' or '`3`' are characters, and are indicated with single quotes. Multiple characters together are known as strings, and are represented with double quotes.

**Note that Python doesn't really distinguish between characters and strings, and uses single and double quotes interchangeably. This is not the case in C#.**

### bool
Booleans are `true`/`false` values. The conditions in `if` and `while` loops must have boolean values; that is, they evaluate either to true or false.

**In Python, the keywords are `True`/`False`, with a capital letter. In C#, they are `true`/`false`, without one.**