---
title: Strings
draft: true
---
Let us see the different operations that can be performed on the below string.
```python
>>> word = 'Sample'
>>> len(word)
6
```


```python
 +---+---+---+---+---+---+
 | S | a | m | p | l | e |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1
```

### 1 Concatenation
Join a string with another string
```python
>>> word = 'Sample'
>>> word + ' ' + 'trick'
'Sample trick'
```

### 2 Indexed Access of Strings
A string in a python can be indexed to perform operations on the string.

Positive single character
```python
word = 'Sample'
word[3]
Output
p
```

Negative single character
```python
word = 'Sample'
word[-2]
Output
l
```

String Reverse
```python
word = 'Sample'
word[::-1]
Output
'elpmaS'
```

Reverse string by iterating through string contents.
```python
word = 'Sample'
for char in reversed(word):    
    print(char)
Output
e
l
p
m
a
S
```

### 3 Slicing of Strings
Slicing allows us to access a substring of characters from a word.
```python
Example 1
word = 'Sample'
word[0:3] 
Output
Sam
```

```python
Example 2
word = 'Sample'
word[4:5] 
Output
le
```

```python
Example 3
word = 'Sample'
word[:5] 
Output
Sampl
```

### 4 Remove leading and trailing characters
To remove space before and after a string the strip() method can be used has shown below
```python
'   Sample   '.strip()
Output
Sample
'sample'.strip('ple')
Output
Sam
```

### 5 Left fill with ASCII ‘0’
To left fill with ASCII ‘0’’, we can use zfill() method to make a length of required string width.
```python
"10".zfill(6)
Output
000010
"-10".zfill(6)
Output
-00010
```
### 6 Find Substring
The find() method can be used to extract a substring from a string
```python
'sample'.find('am',0,5)
Output
1
'sam' in 'sample'
Output
True
```

### 7 Find if the string contains Numbers
The isalpha() method can be used to find if a string contains number
```python
'123'.isalpha()
Output
False
'abc'.isalpha()
Output
True
'1abc'.isalpha()
Output
False
```

### 8 Find if the string is alphanumeric
The isalnum() method can be used to find if the string contains alphanumeric and at least one character
```python
' '.isalnum()
Output
False
'abc'.isalnum()
Output
True
```

### 9 Find if the string is having only whitespace
The isspace() method can be used to determine if the string is only whitespace character
```python
' '.isspace()
Output
True
'Sample  '.isspace()
Output
False
```

### 10 Remove Spaces on the left side of the string
The lstrip() Strings
can be used to remove whitespace characters on the left.
```python
'   sample   '.lstrip()
Output
'spacious   '
'www.example.com'.lstrip('cmowz.')
Output
'example.com'
```

### 11 Remove Spaces on the right side of the string
The rstrip() can be used to remove whitespace characters on the left.
```python
'   sample   '.rstrip()
Output
'spacious   '
'mississippi'.rstrip('ipz')
Output
'mississ'
```

### 12 Formatted String Literals
The string literals which are prefixed with ‘f’ or ’F’ are called f-string.
```python
word = "Sample"
f"THis is a {word!r} string."
Output
"THis is a 'Sample' string."
```

#13 Joining multiple strings from a list
The join() method can be used to join the strings in a list
Test = ["This","is","Sample"]
print(" ".join(Test))
Output
This is Sample
#14 Repeat string multiple times
Same like nos the strings can be multiplied to generate multiple string
word = "Sample"
print(word*3)
Output
SampleSampleSample
#15 Search for multiple prefixes in a string
The startswith() and endswith() method can be passed with multiple patterns of substrings to check if it is present.
"sample".startswith(("sam","Sam"))
Output
True
"sample".endswith(("ple","ple."))
Output
True
#16 Splitting a sentence to word
The split() method can be used to split a sentence to multiple words to form a list
"This is a Sample".split()
Output
['This', 'is', 'a', 'Sample']
#17 Find the frequent word in a sentence
The word which occurs most times in a sentence can be found using the below trick
sentence = “She was young the way an actual young person is young”.split()
most_frequent_word = max(set(sentence),key=sentence.count)
Output
'young'
#18 Find how many occurences of words in a sentence
The below trick helps in finding, how many times the word is present in the sentence sorted by the increasing rate of word occurence.
from collections import Counter
sentence = “She was young the way an actual young person is young”.split()
Counter(sentence)
Output
Counter({'young': 3, 'She': 1, 'was': 1, 'the': 1, 'way': 1, 'an': 1, 'actual': 1, 'person': 1, 'is': 1})
#19 Convert all the words to capital in a sentence
The map() method can be used to make all words to capital letters.
sentence = "Quick brown fox".split()
list(map(str.capitalize,sentence))
Output
['Quick', 'Brown', 'Fox']
#20 Remove duplicate words in a sentence
Duplicate words in a sentence can be removed has shown below
sentence = "The sound sounds sound".split()
list(set(sentence))
Output
['sound', 'The', 'sounds']
#21 Remove duplicate words retain the sentence order
The below trick removes the duplicate word keeping the order of words in the sentence.
from collections import OrderedDict
sentence = "The sound sounds sound".split()
list(OrderedDict.fromkeys(sentence).keys())
Output
['The', 'sound', 'sounds']
#22 Reversing a sentence
The reverse() method can be used to reverse a sentence
sentence = "This is Sample".split()
sentence.reverse()
print(sentence)
Output
['Sample', 'is', 'This']
#23 Splitting words to multiple string
The below trick can be used to split a sentence into multiple words and storing in a string variable.
sentence = "This is Sample".split()
first_word, second_word, third_word = sentence
print(first_word)
print(second_word)
print(third_word)
#24 Combine list using zip() method
The zip() method can be used to combine two seperate list of strings.
Name = ['Tom', 'Marry', 'Jon']
Age = ['35', '30', '40']
for Name, Age in zip(Name,Age):
    print(Name,Age)
Output
Tom 35
Marry 30
Jon 40
#25 Sort words in a list using sorted() method
The sorted() method can be used to sort the list of strings.
sorted(['string1','string2','string3'],reverse=True)
Output
['string3', 'string2', 'string1']