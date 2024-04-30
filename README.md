# Functions
Functions in Python are blocks of code that perform a specific task. They are defined using the 'def' keyword followed by the function name and parentheses. 

Example:
```python
def greet():
    print("Hello!")


# Calling the function
greet()  # Output: Hello!
```
## Functions with Parameters
Functions can accept *parameters*, which are values that are passed to the function when it is called. Parameters are specified within the parentheses in the function definition. *Arguments* are the actual values passed to the function when it is called. 

Example:
```python
def greet(name):
    print("Hello,", name)


# Calling the function, passing "Alice" as an argument
greet("Alice")  # Output: Hello, Alice
```

## Functions with Return Values
Functions can also return values using the `return` keyword. This allows the function to send data back to the caller. 

Example:

```python
def add(a, b):
    return a + b


result = add(3, 5)

print(result)  # Output: 8
```

## Variable Namespace and Scope
Variables defined within a function have *local scope*, meaning they can only be accessed within that function. Variables defined outside of any function have *global scope*, meaning they can be accessed from anywhere in the code. 

Example:

```python
def my_function():
    x = 10  # Local variable
    print(x)


print(x)  # Will result in an error because x is not defined globally
```

<br><br><br>

# Strings
Strings are sequences of characters. They can be indexed, sliced, and manipulated in various ways.

## String Indexing
Strings can be indexed using positive and negative indices. Positive indices start from 0 at the beginning of the string, while negative indices start from -1 at the end of the string. 

Example:

```python
s = "Python"
print(s[0])   # Output: 'P'
print(s[-1])  # Output: 'n'
```

## String Slicing
String slicing is used to extract a substring from a string. It involves specifying a *starting* and *ending index*. In the absence of a start index, the beginning of the string is used. In the absence of an ending index, the end of the string is used.

Note that the ending index is *not inclusive*.

Example:

```python
word = "Python"
print(word[0:3])  # Output: 'Pyt'
print(word[1:5])  # Output: 'ytho'
print(word[:3])   # Output: 'Pyt'
print(word[3:])   # Output: 'hon'
print(word[:])    # Output: 'Python'
```

### More Indexing & Slicing Examples
This code snippet shows several examples of string slicing and indexing. 

```python
# Define a string
my_string = "Hello, World!"

# CHARACTER        H  e  l  l  o  ,     W  o  r  l  d  !
# INDEX            0  1  2  3  4  5  6  7  8  9  10 11 12
# INDEX FROM END              -9 -8 -7 -6 -5 -4 -3 -2 -1

# Indexing: Accessing individual characters
print("First character:", my_string[0])     # H
print("Last character:", my_string[-1])     # !
print("Third character:", my_string[2])     # l

# Slicing: Extracting substrings
print("First five characters:", my_string[:5])      # Hello
print("Characters from index 7 to the end:", my_string[7:])  # World!
print("Characters from index 7 to 11:", my_string[7:12])  # World
```

## Immutability
Strings in Python are *immutable*, meaning individual characters within a string cannot be changed. While you can reassign a string variable to a new value, changing characters or subsets of the string using a string index will result in an error.

This example will result in an error:

```python
my_string = "Hello"
my_string[0] = 'J'  # This will raise an error because strings are immutable
```

However, you can reassign a string variable to a new value without modifying the original string:

```python
my_string = "Hello"
my_string = "J" + my_string[1:]  # Reassign variable with a modified string
print(my_string)                 # Output: 'Jello'
```

## Using Strings with "for" Loops
Strings can be iterated over using a `for` loop. You can iterate over the characters of the string using `len()` or directly. 

Example, using `for` and `len()`:
```python
my_string = "Python"

for i in range(len(my_string)):
    print(my_string[i])
```

Example, iterating over a string directly:
```python
my_string = "Python"

for char in my_string:
    print(char)
```

Both versions will result in the same output:

```
P
y
t
h
o
n
```


## String Methods
Python provides various built-in methods for manipulating strings:

- `.upper()` Converts a string to uppercase.
- `.lower()` Converts a string to lowercase.
- `.swapcase()` Swaps the case of each character in a string.
- `.strip()` Removes leading and trailing whitespace from a string.
- `.find()` Searches for a substring within a string and returns the index of its first occurrence. Returns `-1` if not found. 

Examples:
```python
my_string = "   Python   "

print(my_string.strip())         # Output: 'Python'
print(my_string.upper())         # Output: '   PYTHON   '
print(my_string.find('th'))      # Output: 2
```

<br><br><br>

# Exceptions
We can use `try` and `except` blocks are used for error handling. Here's a summary of how to use them:

### `Try` Block
The code that you think might raise an exception is placed inside the `try` block.
```python
try:
    # Code that might raise an exception
    # ...
```

### `Except` Block
If an exception occurs in the `try` block, the control immediately passes to the `except` block. Here, you can handle the exception or take appropriate action.
```python
except ExceptionType:
    # Code to handle the exception
    # ...
```

`ExceptionType` specifies the type of exception you want to catch. You can be specific (e.g., `ValueError`, `TypeError`) or use a more general `Exception` to catch any type of exception.

### Optional `Else` Block
You can include an else block after the except block, which will only execute if no exception occurs in the try block.
```python
else:
    # Code to execute if no exception occurs
    # ...
```

### Optional `Finally` Block
This block is always executed whether an exception occurred or not. It's useful for releasing external resources (like files or network connections) regardless of whether the code in the try block succeeded or not.
```python
finally:
    # Code to execute whether there is an exception or not
    # ...
```

### Examples
Here are simple examples of how an exception might be handled. 

This example catches all errors with `try` and `except`:

```python
try:
    number = int(input("Enter an integer: "))  # int() only works with integers
except:
    print("Error. Enter a valid integer.")  # Error for all non-integers
```

This example displays different errors depending on the exception (`ValueError` and `ZeroDivisionError`):

```python
try:
    x = int(input("Enter a number: "))  # This might generate an error for int()
    result = 10 / x  # This line might generate an error for 0
    print("Result: ", result)
except ValueError:  # Exception when user enters a non-integer
    print("Please enter a valid number.")
except ZeroDivisionError:  # Exception when user enters a zero
    print("Cannot divide by zero.")
```

This is a complete example showing the usage of optional `else` and `finally` structures:

```python
try:
    x = int(input("Enter a number: "))
    result = 10 / x
    print("Result:", result)
except ValueError:
    print("Please enter a valid number.")
except ZeroDivisionError:
    print("Cannot divide by zero.")
else:
    print("No exceptions occurred.")
finally:
    print("This will always execute.")
```

In above example:

- If the user enters a non-integer value, a `ValueError` will occur, and the corresponding message will be printed.
- If the user enters `0`, a `ZeroDivisionError` will occur, and the corresponding message will be printed.
- If the user enters any other number, the result will be printed along with the message saying no exceptions occurred.
- Finally, the message in the finally block will always be printed.

