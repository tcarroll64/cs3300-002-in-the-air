# Python Technical Documentation

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



### Regular Expressions

In Python regular expressions (regex, or regexp) 


