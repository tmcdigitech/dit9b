---
title: RELIEF LESSON
weight: -100
---
*Monday T2.9 (4 July)*

This morning you should work through the challenges 1-7 in Task 1, which are on Sequence.

Some of you did these last semester, but in Python. This time you'll need to do them in C#, and you will find it instructive to compare the code from the two languages.

You should write these programs using [.NET Fiddle](https://dotnetfiddle.net/). As you finish each one and have tested it successfully, copy the completed code into a new file in Visual Studio Code and save it into a folder named `task1` in your Digital Tech folder. Give each one a name according to the number of the exercise: number 1 will be `ex1.cs`, number 2 will be `ex2.cs`, and so on.

To help you with the structure and specifics of C#, here is the complete code for exercise 2:

```c#
using System;

public class Program
{
    public static void Main()
    {
        Console.WriteLine("What is your first name?");
        string firstname = Console.ReadLine();
        Console.WriteLine("What is your surname?");
        string surname = Console.ReadLine();
        Console.WriteLine(surname+" "+firstname);
    }
}
```

A couple of useful notes: 

- *.NET Fiddle* provides you with the necessary code to get started. You should leave the surrounding code in place, and only change the bits inside the Main() function, which initially is the line with "Hello World" in it.
- notice that statements must end with a semicolon (`;`), as in the example *.NET Fiddle* begins with
- you need to declare variables before you use them the first time (as in the example above, where we put "string" before the name of the variables firstname and surname in their first use). If you write to them a second time, you don't need to declare their type again.
- If you need to convert a string into an integer, which has the type `int`, you can use the function `int.Parse("32")`, where you replace the string `"32"` with the variable you want to interpret as a number. For example, this code will read in a number from the console and print out double that number:
```c#
using System;

public class Program
{
    public static void Main()
    {
        Console.WriteLine("What is your favourite whole number?");
        int number = int.Parse(Console.ReadLine());
        number = number*2;
        Console.WriteLine("Double that number is "+number+".");
    }
}
```
