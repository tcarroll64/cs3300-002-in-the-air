# Python Technical Documentation

### Table of Contents

[Introduction](#introduction)

[Virtual Environment](#virtual-environment)

[Classes and Objects](#classes-and-objects)

[Dictionaries](#dictionaries)

[Regular Expressions](#regular-expressions)

### Introduction

This document serves the purpose of being a resource to keep all of the important Python information we will be needing for this semester. Use the table of contents to navigate to a particular section you would like to know more about. Anyone on the team is welcome to edit this document, if they spot errors or would like to add new information.

### Virtual Environment

In Python, a virtual environment is a **dependency management** tool that isolates dependencies that are required by different projects. Two different projects might use two different versions of the same dependency. If you only used that global dependency, there could be a conflict, where only one of the projects works. 

For example, if I have one project that only works on <u>Django 4.1</u> and another project that only works on <u>Django 4.2</u>, then only one of them can work at a time. If I set up a different virtual environment for each of them, then the individual projects will be using the right python version, so both can work at the same time.

[Python Docs for installing a virtual environment](https://docs.python.org/3/library/venv.html)

### Classes and Objects

In python, a class is like a **blueprint** for creating things (objects). An object is an **instance** of a class. So you can have one class, and multiple instances (objects) of that class. In python, the constructor is the __init__() method, where the attributes for the class can be passed as arguments.  

For example, let’s say I have a class called “Car”. The attributes for Car would be make, model, and year. Those attributes could be instance variables. The class might look like this:

```python
class Car:
    def __init__(self, make, model, year)
        self.make = make
        self.model = model
        self.year = year
```

Remember to have the **self** parameter at the start, which refers to the instance of the object. You don’t actually have to pass an argument for this. If I wanted to instantiate a new car, it would look like this:  

```python
car1 = Car("Chevy, "Impala", 2005)
```

```python
dict["apples"]Then I could have an instance method like this:  
```

```python
    def display(self):
        print("This car is a " + self.year + " " + self.make + " " + self.model)
```

[Classes and Objects Python 3.11 Docs](https://docs.python.org/3/tutorial/classes.html)

### Dictionaries

A dictionary in python is like a key -> value map. It's interesting, because the values of the entries don't have to be of all the same type. You can create a dictionary like this:  

```python
dict = {"apples": 30, "location": "France"}
```

To access the value of a key you can use dictionary[<key>] like this:  

```python
dict["apples"]
```

You can also add an entry like this:  

```python
dict["key": "value"]  
```

As was said before, the entries for a dictionary don’t have to be of the same datatype. This is only possible because Python is dynamically typed, meaning that a variable only has a type at runtime when it’s used, and not when it’s created.

It’s important to note that dictionaries are ordered (**SINCE 3.7**), and the keys are unique, meaning there can be only one entry with a specific key.

You can return the number of entries in a dictionary by doing this:

```python
len(dict)
```

Dictionaries are a very useful way of storing data in python.

[W3Schools Python Dictionaries Docs](https://www.w3schools.com/python/python_dictionaries.asp)

### Regular Expressions

In Python regular expressions (regex, or regexp) are a useful tool for pattern matching. Using regex, you can search, match, and manipulate strings based on specific patterns. You need to import the **re** library to use them:

```python
import re
```

Here are some of the most common methods that are provided by the **re** library:

| Function | Description                                                      |
| -------- | ---------------------------------------------------------------- |
| findall  | Returns a list containing all matches of pattern                 |
| search   | Returns a "match" object if there is a match                     |
| split    | Returns a list, where each element is where the string was split |
| sub      | Replaces matches with a string                                   |

In the parameters of these functions, you can define patterns. You can do this with **metacharacters**. Metacharacters are characters that have a specific meaning.

Here are some useful metacharacters:

| Character | Description                                          | Example   |
| --------- | ---------------------------------------------------- | --------- |
| []        | A set of characters                                  | `[a-e]`   |
| \         | A special sequence (for example, sequence of digits) | `\d`      |
| .         | Any character (except newline)                       | `he..o`   |
| ^         | Starts with                                          | `^hello`  |
| \$        | Ends with                                            | `planet$` |
| \*        | Zero or more occurances                              | `he.*o`   |
| +         | One or more occurances                               | `he.+o`   |
| ?         | Zero or one occurances                               | `he.?o`   |

There are also **special sequences** which can be used with a `\` and then a specific character. Here are some of the characters that are useful

| Character | Description                                                                                                                                         | Example                   |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| \A        | Finds characters at the beginning of the string                                                                                                     | `"\AWord"`                |
| \b        | Finds characters at the beginning or end of a word. (`r` is at the beginning to tell the regular expression that it’s searching for a “raw” string) | `r“\bing”` or `r”find\b”` |
| \d        | Finds digits 0-9                                                                                                                                    | `\d`                      |
| \s        | Finds whitespace characters                                                                                                                         | `\s`                      |
| \w        | finds "words" (characters a-Z, 0-9, underscore)                                                                                                     | `\w`                      |

There are many more examples, but these are some of the most used.  

Here is an example of using the `search` function to find a pattern in a string:

```python
import re

txt = "The mouse lives in Italy"
x = re.search(r"\bI\w+", txt)
print(x.group()) # prints: Italy
```

Let's break down `r"\bI\w+"`

- `r` specifies a "raw" string

- `\b` search the following characters in a string

- `I` is the literal character to search for

- `\w` means to find a word matching the pattern

- `+` means match the pattern with one or more occurances

Regular expressions are useful for searching/manipulating data based on patterns.

[W3Schools Python RegEx Docs](https://www.w3schools.com/python/python_regex.asp)
