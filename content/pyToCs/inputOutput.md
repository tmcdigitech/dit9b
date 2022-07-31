---
title: Basic input and output
weight: 10
---

## Output
### Python
{{< highlight python >}}
print("Some text")
{{< /highlight >}}

### C#
{{< highlight cs >}}
Console.WriteLine("Some text")
{{< /highlight >}}

To print to the console in Python, we use the `print()` function.
In C#, console functions are part of the Console class, and the
equivalent to Python's print function is `Console.WriteLine()`.
If you don't want it to automatically add a line break, you can
use the `Console.Write()` function.

## Input

### Python
{{< highlight python >}}
response = input("What is your name? ")
{{< /highlight >}}

### C#
{{< highlight cs >}}
Console.WriteLine("What is your name? ")
response = Console.ReadLine();
{{< /highlight >}}

Python's `input()` function takes a parameter which is
printed, like a question, before reading in the response
from the user. C#'s equivalent, `Console.ReadLine()`, only
offers a generic prompt: `> `. So in order to ask a question or
provide information to the user about what they should be entering,
you will need to add one or more `Console.WriteLine()` commands before
you read in the user's response.