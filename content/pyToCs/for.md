---
title: for loops
weight: 50
---

## Python
In Python, the range() function is commonly used to make a loop that counts through some number:
- `range(4)` will give the numbers 0, 1, 2, 3 (i.e. 0 to not-quite 4);
- `range(1,4)` will give the numbers 1, 2, 3 (i.e. 1 to not-quite 4);
- `range(1,4,2)` will give the numbers 1, 3 (i.e. 1 to not-quite 4, increasing by 2).

## C#
C# inherits its truly disgusting for loop layout from C. It is basically a slight rejigging of what you'd write if you were going to write a for loop using a while loop.

Here is a basic for loop, written using a while loop:

```cs
int i=0;
while( i<4 ){
    Console.WriteLine(i);
    i++;
}
```
Note that `i++` is a shortcut for `i = i + 1`.

Here is the equivalent written as a 'proper' for loop:

```cs
for( int i=0; i<4; i++ ){
    Console.WriteLine(i);
}
```
The setup part of the for loop has three mini statements. The first sets up the counter. The second is the loop condition (it will loop while this statement is true). The third is the step to perform at the end of each loop to prepare for the next run of the loop.

Here are two examples of equivalent Python and C# loops, and their resulting output.

## Python 1
```python
for i in range(4):
    print(i)
```

## C# 1
```cs
for( int i=0; i<4; i++ ){
    Console.WriteLine(i);
}
```

## Output 1
```
0
1
2
3
```

## Python 2
```python
for i in range(3, 10, 2):
    print(i)
```

## C# 2
```cs
for( int i=3; i<10; i=i+2 ){
    Console.WriteLine(i);
}
```

## Output 2
```
3
5
7
9
```
