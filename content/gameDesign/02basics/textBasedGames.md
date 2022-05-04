---
title: Text-based quiz games
weight: 20
---

*from [Coding Games with Pygame Zero & Python, by Richard Smith](https://electronstudio.github.io/pygame-zero-book/chapters/text_quizes.html)*

These programs can be entered using any text editor, but I suggest using the Mu editor because it comes with Python, Pygame Zero and other libraries all pre-installed in one easy download.

## 3.1. Hello, world
The traditional first program used to make sure Python is working and that we can run programs.

If using the Mu editor:

1. Click the mode button and make sure the mode is set to `Python3`.
2. Type in the program.
3. Click `Save` and enter a name for the program.
4. Click `Run`.

*Program 3.1 Hello, world*
```python {linenos=table}
print("Hello world")

# This line is a comment. The computer will ignore these.
```

## 3.2. Getting input from the keyboard
This program will pause and wait for you to enter some text with the keyboard, followed by the return/enter key. The text you enter is stored in a variable, `x`.

*Program 3.2 Getting input from the keyboard*
```python {linenos=table}
print("Enter your name:")
x = input()
print("Hello", x)
if x == "richard":
    print("That is a very cool name")
```

#### Exercise
Add some names of your friends and display a different message for each friend.

## 3.3. Making decisions: if, elif, else
This is how to add another name to Program 3.2.

*Program 3.3 Decisions: if, elif, else*
{{< highlight python "linenos=table,hl_lines=6-9" >}}
print("Enter your name:")
x = input()
print("Hello", x)
if x == "richard":
    print("That is a very cool name")
elif x == "nick":
    print("That is a rubbish name")
else:
    print("I do not know your name", x)
{{< /highlight >}}

Program 3.3 is very similar to Program 3.2. The new lines have been highlighted. You can either modify Program 3.2, or else create a new file and use copy and paste to copy the code from the old program into the new.

## 3.4. A random maths question
*Program 3.4 A random maths question*
{{< highlight python "linenos=table" >}}
import random

n = random.randint(0, 10)

print("What is", n, "plus 7?")
g = int(input())  # Why do we use int() here?
if g == n + 7:
    print("Correct")
else:
    print("Wrong")
{{< /highlight >}}

#### Exercise
Add some more questions, e.g.

- Instead of 7, use another random number.
- Use a bigger random number.
- Multiply (use `*`), divide (use `/`) or subtract (use `-`) numbers.

#### Exercise
Print how many questions the player got correct at the end.

## 3.5. Keeping score
We create a `score` variable to record how many questions the player answered correctly.

*Program 3.5 Keeping score*
{{< highlight python "linenos=table" >}}
score = 0

print("What is 1+1 ?")
g = int(input())
if g == 2:
    print("Correct")
    score = score + 1

print("What is 35-25 ?")
g = int(input())
if g == 10:
    print("Correct")
    score = score + 1

print("Your score:", score)
{{< /highlight >}}

## 3.6. Guessing game with a loop
This `while` loop goes round and round forever … or until the player gets a correct answer, and then it `break`s out of the loop. Note that everything in the loop is indented.

*Program 3.6 Guessing game with a loop*
{{< highlight python "linenos=table" >}}
import random

n = random.randint(0, 10)

while True:
    print("I am thinking of a number, can you guess what it is?")
    g = int(input())
    if g == n:
        break
    else:
        print("Wrong")
print("Correct!")
{{< /highlight >}}

#### Exercise
Give a hint to the player when they are wrong. Was their guess too high or too low?

#### Exercise
Print how many guesses they took to get it right at the end.

## 3.7. Improved guessing game
Program 3.6 with a hint whether the guess is greater or lesser than the answer.

*Program 3.7 Improved guessing game*
{{< highlight python "linenos=table" >}}
import random

n = random.randint(0, 100)
guesses = 0

while True:
    guesses = guesses + 1
    print("I am thinking of a number, can you guess what it is?")
    g = int(input())
    if g == n:
        break
    elif g < n:
        print("Too low")
    elif g > n:
        print("Too high")
print("Correct! You took", guesses, "guesses.")
{{< /highlight >}}