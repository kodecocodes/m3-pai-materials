# Instructions

## Data Types and Variables

### Data Types

Python supports the following basic data types:

- **`int`**: integers
- **`float`**: floating-point numbers
- **`complex`**: complex numbers
- **`str`**: strings
- **`bool`**: booleans
  
### Creating Variables

Python doesn’t have keywords like `var` or `let` for declaring variables. To create a new variable in Python, simply use the assignment (`=`) operator to assign a value to a new variable name. Python does _not_ require you to specify the variable’s type. Instead, it infers the variable’s type from the value assigned to it.

Here are some examples:

```python
# Creating an integer variable
score = 200

# Creating a floating-point variable
time_travel_gigawatts = 1.21

# Creating a string variable
greeting = "Welcome to Python"

# Creating a boolean variable
is_user_logged_in = True
```

> The only thing that you might find surprising about Python’s data types is that its boolean values are capitalized: they’re `True` and `False`, not `true` and `false`.

### Variable Names

The variables in the code above are named using the “snake case” format, which uses all lowercase letters and separates words with underscores. This is one of the stylistic conventions that has been widely adopted by the Python community.

### (No) Constants

Unlike many high-level programming languages, Python _does not_ have constants — just variables.

To make up for a lack of constants, many Python programmers follow the convention of naming them using only uppercase letters with underscore characters (`_`) separating words for legibility.

### The `None` Value

Python has a special value called `None`, which represents a null value or the absence of a value, like `nil` or `null` in other programming languages.

One common use of `None` is to initialize variables that will be assigned a value at a later time. This is as close to declaring a variable as Python gets:

```python
# The game hasn’t started yet
player_current_level = None
```

One common use of `None` is to initialize variables that will be assigned a value at a later time. This is as close to declaring a variable as Python gets:

```python
# The game hasn’t started yet
player_current_level = None
```

### Determining a value’s type

Python’s `type()` function takes an object and returns that object’s type. 

Run each of the following in a code cell to see the result:

- `type(2)`  
- `type(3.14159)` 
- `type(4+5j)`
- `type("Testing one, two, three")`
- `type(False)`
- `type(None)`

The results should be `int`, `float`, `complex`, `str`, `bool`, and `NoneType`.

### Converting Values to Other Types

Everything in Python is an object — even basic data types. Because of this, you can create a new integer and string variable using object initializer syntax:

```python
score = int(200)
message = str("Hi there!")
```

While you probably wouldn’t want to create variables for simple data types this way, it’s useful for converting values of one type to another.

You can use any of these initializer methods to do type conversion:

- `int()` to convert to an integer
- `float()` to convert to a floating-point number
- `complex()` to convert to a complex number
- `str()` to convert to a string
- `bool()` to convert to a boolean

### Deleting Variables

Unlike most languages, Python has a statement that deletes objects from memory, which includes variables: `del`.

Here’s an example:

```python
my_variable = "I won't be around for long."
print(my_variable)
del my_variable
print(my_variable)  # "NameError: name 'my_variable' is not defined"
```

Notice that `del` is a statement, not a function. You don’t need to put parentheses around the variable to be deleted.

## Strings and User Input

### String Interpolation With f-Strings

The simplest and most readable way to do string interpolation in Python is to use _f-strings_, whose name is short for “formatted strings”. 

Like regular strings, f-strings are delimited by quotes (either `'` or `"`), but the opening quote is preceded by `f`. Any value, object, or expression that you want interpolated into the f-string should be contained in braces (`{` and `}` ).

For example, the following code...

```python
name = "Alice"
print(f"{name} needs {21 * 34} floor tiles.")
```

...results in this output:

```
Alice needs 714 floor tiles.
```

### Multi-Line Strings

Python uses triple quotes (`'''` or `"""`) to delimit string literals with multiple lines.

Here’s an example:

```python
message = """Here is
an example
of a multi-line string
in Python."""
```

Multi-line strings can also be f-strings:

```python
items_count = 3
price = 8.62
print(f"""Your cost
for {items_count} items at ${price} each
is {items_count * price}.""")
```
### Getting User Input with `input()`

Python’s `input()` function presents the user with an optional prompt, waits for them to enter something, and returns the user’s input as a string. In Jupyter, it presents the prompt beside a text box where the user can enter text.

Try running the following in a code cell:

```python
# Putting a space at the end of an `input()` prompt
# provides a little distance between the prompt
# and the text input box.
name = input("What is your name? ")
print(f"That's funny, my dog's name is {name}.")
```

Remember that `input()` returns a string. If your program needs numeric input, use `int()` or `float()` convert the return value.

### Useful String Methods

You may find the following string methods useful for processing user input:

- **`lower()`**: Returns a version of the string with all its letters converted to lowercase.
- **`strip()`**: Returns a version of the string with any leading or trailing whitespace removed.
- **`upper()`**: Returns a version of the string with all its letters converted to uppercase.

## Comparison and Boolean Logic Operators in Python

Python uses the standard comparison operators found in other programming languages...

- `==`: Equal to
- `!=`: Not equal to
- `>`: Greater than
- `<`: Less than
- `>=`: Greater than or equal to
- `<=`: Less than or equal to

...but its boolean logic operators may differ from the ones you usually use:

- `not` instead of `!`
- `and` instead of `&&`
- `or` instead of `||`

`not` has higher precedence than `and`, which has higher precedence than `or`.

## Branching With `if`, `elif`, and `else`

### `if` and Indentation

Python’s `if` statement works _almost_ as you might expect, but there are differences in syntax from other programming languages.

Run this code in a new code cell a couple of times. See what happens when you enter `y` or `yes`, and what happens when you enter anything else.

```python
status = input("Is the job complete? ").strip().lower()

if status == "y" or status == "yes":
	print("Hooray! The job is complete!")
	print("Take a moment to celebrate.")
	print("But afterward, get back to work!")
print("Now on to the rest of the program.")
```

### Test Expressions Don’t Need Parentheses

Take a closer look at the `if` statement:

```python
if status == "y" or status == "yes":
```

The first thing you should notice is that the expression following `if` is _not_ in parentheses. Python doesn’t require parentheses around an `if` statement’s test expression. It’s part of the Python philosophy of readability and simplicity.

### Code Blocks Begin With `:` and Are Indented

Here’s the entire `if` section of the code:

```python
if status == "y" or status == "yes":
	print("Hooray! The job is complete!")
	print("Take a moment to celebrate.")
	print("But afterward, get back to work!")
```

The `if` statement, `if status == "y" or status == "yes":`, ends with the colon (`:`) character. This character is a very important one in Python, since it says the following:

- A block of code, made up of the following indented lines, starts below.
- The code block will execute if and only if the conditions on this line are met.

The end of the `if` block is indicated by the end of the indentation. In this example, this line of code is _outside_ the `if` block and executes regardless of the value in `status`:

```python
print("Now on to the rest of the program.")
```

### `else`

If you take Python’s syntax into account, the `else` keyword works as you might expect:

```python
status = input("Is the job complete? ").strip().lower()

if status == "y" or status == "yes":
	print("Hooray! The job is complete!")
	print("Take a moment to celebrate.")
	print("But afterward, get back to work!")
else:
	print("Well, keep working at it.")
	print("We'll celebrate when it's done.")

print("Now on to the rest of the program.")
```

In this version of the code, there are now two specific responses to the user’s input:

- One when the user enters `y` or `yes`.
- One when the user enters anything else.

After either case, the code proceeds to the next line - `print("Now on to the rest of the program.")` — which is at the same level of indentation as the `if` and `else` statements. This line will execute, regardless of what the user entered.

### `elif`

Python has the `elif` keyword, which is a compressed, combined version of the `else if` statement used in other programming languages:

```python
status = input("Is the job complete? ").strip().lower()

if status == "y" or status == "yes":
	print("Hooray! The job is complete!")
	print("Take a moment to celebrate.")
	print("But afterward, get back to work!")
elif status == "n" or status == "no":
	print("Well, keep working at it.")
	print("We'll celebrate when it's done.")
else:
    print("You're not good at following instructions.")
    print("This will go in your permanent record.")

print("Now on to the rest of the program.")
```

In this code, there are now _three_ responses to the user’s input:

- One when the user enters `y` or `yes`.
- Another one when the user enters `n` or `no`.
- A final one when the user enters anything other than `y`, `yes`, `n`, or `no`.

After all of these cases, the code proceeds to the next line - `print("Now on to the rest of the program.")` — which is at the same level of indentation as the `if`, `elif`, and `else` statements. This line will execute, regardless of what the user entered.

## `while` Loops

Python has only two kinds of loop statements, the first of which is the `while` loop. It functions like the `while` loops in most other programming languages:

```python
count = 0
while count < 5:
    print(f"The current count is {count}.")
    count += 1
```

Note that you don’t have to put the conditional expression — the `count < 5` part — in parentheses, just as they’re not required in Python’s `if` and `elif` statements. This makes sense; like `if` and `elif`, loops are a form of branching.

### `break`

Like other programming languages, you can use the `break` statement to exit a loop from within:


```python
while True:
    response = input("Continue? Enter \"y\" or \"n\". ")
    if response == "y" or response == "n":
        break
print(f"Your response was \"{response}\".")
```

### `continue`

Python also provides the `continue` statement, which sends the program back to the start of the loop, where it starts the next iteration:

```python
count = 0

while count < 20:
    count += 1
    # True if `count` is evenly divisible by 3
    if count % 3 == 0:
        continue
    print(f"The current number is {count},")
    print("and it's not evenly divisible by 3.")
```

### `else`

An unusual and often overlooked feature of Python’s loops is the `else` keyword. It allows you to define a block of code that will execute only when the loop completes “normally” — that is, without executing the `break` statement while in the loop.

In this first example, the code prints out the numbers 0 through 4 followed by "Done!" because the `break` statement is never executed:

```python
count = 0
while count < 5:
    print(count)
    count += 1
else:
    print("Done!")
```

This code prints out the numbers 0 through 3, but _does not_ print "Done!"

```python
count = 0
while count < 5:
    print(count)
    if count == 3:
        break
    count += 1
else:
    print("Done!")
```

If the code in a loop never executes, then it never encounters the `break` statement, and therefore it exits normally. This means that the `else` block is executed:

```python
while False:
    print("This will never execute...")
else:
    print("...but this will!")
```

## Sequence Types: Strings, Lists, and Tuples

Python has three built-in _sequence types_, which are data types that hold multiple values in a specific order. They are:

- **Strings**, which are like strings in other programming languages, and are delimited by quotes (`'` or `"`). Example: `"Hello there"`.
- **Lists**, which are similar to arrays in other languages (but more flexible), and are delimited by `[` and `]`. Example: `[1, 2, 3, 4.0, "Test", True]`
- **Tuples**, which are like Python lists, but immutable, and are delimited by `(` and `)`.
Example: `(1, 2, 3, 4.0, "Test", True)`

### Creating Empty Strings, Lists, and Tuples

The simplest way to create an empty string, list, and tuple is to assign an string, list, and tuple literals to variables:

```python
empty_string = ""
empty_list = []
empty_tuple = ()
```

You can confirm their types with the `type()` function:

```python
empty_string = ""
empty_list = []
empty_tuple = ()

print(type(empty_string))  # <class 'str'>
print(type(empty_list))    # <class 'list'>
print(type(empty_tuple))   # <class 'tuple'>
```

You can also create a string, list, and tuple using object initialization syntax:

```python
another_empty_string = str()
another_empty_list = list()
another_empty_tuple = tuple()
```

### Creating Non-Empty Strings, Lists, and Tuples 

Here are examples of creating a non-empty string, list, and tuple using literal string, list, and tuple values:

```python
my_string = "Python" 
my_list = ["P", "y", "t", "h", "o", "n"]
my_tuple = ("P", "y", "t", "h", "o", "n")
```

The string, list, and tuple above will be used in the examples that follow.

### Accessing Individual Elements of a Sequence

Python uses array index notation to access elements of a sequence, where the first element’s index is `0`. For example:

```python
# These all produce the output "P"
print(my_string[0])
print(my_list[0])
print(my_tuple[0])

# These all produce the output "t"
print(my_string[2])
print(my_list[2])
print(my_tuple[2])
```

Python uses negative indexes to access sequence elements starting from the end, where the index for the last item is `-1`, the index for the second-lasty item is `-2`, and so on. For example:

```python
# These all produce the output "n"
print(my_string[-1])
print(my_list[-1])
print(my_tuple[-1])

# These all produce the output "h"
print(my_string[-3])
print(my_list[-3])
print(my_tuple[-3])
```

### Accessing Slices of a Sequence

Python has a syntax for accessing a _slice_ — a smaller sequence — from a string, list, or tuple. The simplest version of the slice syntax is `sequence[start:stop]`. For example:

```python
# Get a slice that starts at element 0
# and ends *before* element 3
print(my_string[0:3])  # Pyt
print(my_list[0:3])    # ['P', 'y', 't']
print(my_tuple[0:3])   # ('P', 'y', 't')
```

You can use negative indexes to get slices:

```python
# Get a slice that starts at element -4
# and ends *before* element -2
print(my_string[-4:-2])  # th
print(my_list[-4:-2])    # ['t', 'h']
print(my_tuple[-4:-2])   # ('t', 'h')
```

You can omit the first index to start the slice from the beginning of the sequence or omit the second index to end the slice at the end of the sequence:

```python
# Get a slice that starts at
# the start of the sequence
# and ends *before* element 2
print(my_string[:2])  # Py
print(my_list[:2])    # ['P', 'y']
print(my_tuple[:2])   # ('P', 'y')

# Get a slice that starts with element -2
# and ends at the end of the sequence
print(my_string[-2:])  # on
print(my_list[-2:])    # ['o', 'n']
print(my_tuple[-2:])   # ('o', 'n')
```

### Getting the Length of a Sequence

Use the `len()` function to get a sequence’s length (i.e. the number of elements in the sequence):

```python
print(len(my_string))  # 6
print(len(my_list))    # 6
print(len(my_tuple))   # 6
```

### Determining if a Given Item Is in a Sequence

Use Python’s `in` operator to test if a given item is contained within a sequence:

```python
print("h" in my_string)  # True
print("h" in my_list)    # True
print("h" in my_tuple)   # True

print("A" in my_string)  # False
print("A" in my_list)    # False
print("A" in my_tuple)   # False
```

### Determining How Many Instances of an Item Are in a Sequence

Use the `count()` method to find out how many instances of an item are in a sequence:

```python
# How many instances of `t`?
print(my_string.count("t"))  # 1
print(my_list.count("t"))    # 1
print(my_tuple.count("t"))   # 1

# How many instances of `$`?
print(my_string.count("$"))  # 0
print(my_list.count("$"))    # 0
print(my_tuple.count("$"))   # 0
```

### Finding the First Instance of an Item in a Sequence

The `index()` method, returns the location the first instance of a given item in a sequence — but only if it’s actually in the sequence:

```python
# If the item is in the sequence, 
# index() returns the item’s index
print(my_string.index("t"))  # 2
print(my_list.index("t"))    # 2
print(my_tuple.index("t"))   # 2

# If the item is NOT in the sequence, 
# index() raises a ValueError
print(my_string.index("$"))  # ValueError
print(my_list.index("$"))    # ValueError
print(my_tuple.index("$"))   # ValueError
```

To avoid errors, use `in` or `count()` to test for the presence of the item before using `index()`.

### Merging Sequences

The `+` operator can concatenate two sequences together:

```python
print(my_string + my_string)  # PythonPython
print(my_list + my_list)      # ['P', 'y', 't', 'h', 'o', 'n', 'P', 'y', 't', 'h', 'o', 'n']
print(my_tuple + my_tuple)    # ('P', 'y', 't', 'h', 'o', 'n', 'P', 'y', 't', 'h', 'o', 'n')
```

### Repeating Sequences

The `*` operator can repeat a sequence a number of times:

```python
print(my_string * 3)  # PythonPythonPython
print(my_list * 3)    # ['P', 'y', 't', 'h', 'o', 'n', 'P', 'y', 't', 'h', 'o', 'n', 'P', 'y', 't', 'h', 'o', 'n']
print(my_tuple * 3)   # ('P', 'y', 't', 'h', 'o', 'n', 'P', 'y', 't', 'h', 'o', 'n', 'P', 'y', 't', 'h', 'o', 'n')
```

## Lists

Python’s lists have features that go beyond what you can do with other sequence types. The most-used ones are listed below.

### Updating Elements of a List

Use the assignment operator, `=` to update a list`s elements:

```python
# The 5 most popular ice cream flavors in the US
flavors = ["vanilla", "chocolate", "cookies and cream", "strawberry", "chocolate chip"]

# Update the first flavor in the list
flavors[0] = "spumoni"

# Update the last flavor in the list
flavors[-1] = "bubble gum"
```

After running this code, `flavors`’ value is `['spumoni', 'chocolate', 'cookies and cream', 'strawberry', 'bubble gum']`.

### Adding an Item to the End of a List

The `append()` method takes an item and adds it to the end of the list:

```python
flavors = ["vanilla", "chocolate", "cookies and cream", "strawberry", "chocolate chip"]
flavors.append("pistachio")
```

After running this code, `flavors`’ value is
`['vanilla', 'chocolate', 'cookies and cream', 'strawberry', 'chocolate chip', 'pistachio']`.

### Adding an Item at a Specific Position in a List

The `insert()` method takes two values:

1. The index where the new item should be added.
2. The item to be added.

```python
flavors = ["vanilla", "chocolate", "cookies and cream", "strawberry", "chocolate chip"]

# Add a new flavor - "cake batter" - at index 2.
flavors.insert(2, "cake batter")
```

After running this code, `flavors`’ value is
`['vanilla', 'chocolate', 'cake batter', 'cookies and cream', 'strawberry', 'chocolate chip']`.

### Removing an Element From a List Based on Its Position

The `pop()` method, when not given an argument, removes the last element from the list _and_ returns it:

```python
flavors = ["vanilla", "chocolate", "cookies and cream", "strawberry", "chocolate chip"]

# Remove the last element from the list
# and capture it in the variable `popped_flavor`.
popped_flavor = flavors.pop()
```

After running this code:

* `flavors`’ value is `['vanilla', 'chocolate', 'cookies and cream', 'strawberry']`.
* `popped_flavor`’s value is `'chocolate chip'`.

When given an index, `pop()` removes the element at that index _and_ returns it:

```python
flavors = ["vanilla", "chocolate", "cookies and cream", "strawberry", "chocolate chip"]

# Remove the element at index 2 from the list
# and capture it in the variable `popped_flavor`.
popped_flavor = flavors.pop(2)
```

After running this code:

* `flavors`’ value is `['vanilla', 'chocolate', 'strawberry', 'chocolate chip']`.
* `popped_flavor`’s value is `'cookies and cream'`.

You can also delete an element from a list using `del`, which deletes a given object from memory:

```python
flavors = ["vanilla", "chocolate", "cookies and cream", "strawberry", "chocolate chip"]

# Remove the element at index 3
del flavors[3]
```

Unlike `pop()`, `del` is not a function and does not return a value. It simply deletes objects.

### Removing an Item From a List Based on Its Value

Use the `remove()` method to specify the value of the item you want to remove. If there’s more than one instance of the first value, then `remove()` will remove only the first instance:

```python
flavors = ["vanilla", "chocolate", "cookies and cream", "strawberry", "chocolate chip"]

# Remove "cookies and cream"
flavors.remove("cookies and cream")
```
After running this code, `flavors`’ value is
`['vanilla', 'chocolate', 'strawberry', 'chocolate chip']`.

If the list _doesn’t_ contain the item you’re trying to remove, using `remove()` to remove that item results in an error.

### Clearing All Elements From a List

The `clear()` method removes all items from a list:

```python
flavors = ["vanilla", "chocolate", "cookies and cream", "strawberry", "chocolate chip"]

# Clear all elements
flavors.clear()
```

After running this code, `flavors`’ value is
`[]`.

### Sorting a List

Use the `sort()` method to sort the elements in a list. `sort()` sorts the list _in place_; that is, it doesn’t create a sorted copy of the list, but rearranges its items in sorted order.

Here’s how you sort a list in both ascending and descending orders:

```python
flavors = ["vanilla", "chocolate", "cookies and cream", "strawberry", "chocolate chip"]

# Sort the elements in place, in ascending order
flavors.sort()

# Prints ['chocolate', 'chocolate chip', 'cookies and cream', 'strawberry', 'vanilla']
print(flavors)

# Sort the elements in place, in descending order
flavors.sort(reverse=True)

# Prints ['vanilla', 'strawberry', 'cookies and cream', 'chocolate chip', 'chocolate']
print(flavors)
```

After running this code, `flavors`’ value is
`['chocolate', 'chocolate chip', 'cookies and cream', 'strawberry', 'vanilla']`.

### Reversing the Order of a List

Use the `reverse()` method to reverse the order of a list. Like `sort()`, `reverse()` reverses the order of the list in place:

```python
flavors = ["vanilla", "chocolate", "cookies and cream", "strawberry", "chocolate chip"]

# Reverse the order of the list
flavors.reverse()
```

After running this code, `flavors`’ value is
`['chocolate chip', 'strawberry', 'cookies and cream', 'chocolate', 'vanilla']`.



### Merging Two Lists

There are many ways to merge two lists in Python.

One of these ways is to use the `+` operator. The result is a new list made of the items in the first list in the order in which they appear, followed by the items in the second list in the first list in the order in which they appear:

```python
# Merging lists with +
lots_of_flavors = flavors + sorted_flavors
lots_of_flavors
```

Another way is to use the `extend()` method, which you call as a method of the first list, and pass the second list as a parameter. This changes the first list, which now contains the items in the first list in the order in which they appear, followed by the items in the second list in the first list in the order in which they appear:

```python
# Merging lists with `extend()`
flavors.extend(sorted_flavors)
print(f"flavors:\n{flavors}")
print(f"sorted_flavors:\n{sorted_flavors}")
```

## `for` Loops

Unlike `for` loops in many other programming languages — especially those that borrow their syntax from C — Python’s `for` loops are made _not_ to change the value of an index variable, but to iterate over a sequence and execute a block of code for each element in it.

### Iterating Over Sequences

Here’s how you iterate over a list with a `for` loop:

```python
greeting = "Hello"
languages = ["Python", "Java", "C", "JavaScript", "Swift", "Kotlin"]
the_numbers = (4, 8, 15, 16, 23, 42)

# Iterating over a string with `for`
for character in greeting:
    print(f"The current character in {character}.")

# Iterating over a list with `for`
for language in languages:
    print(f"I'm now reading up on {language}.")

# Iterating over a tuple with `for`
for number in the_numbers:
    print(f"The current number is {number}.")
```

Here’s the output for the code above:

```
The current character in H.
The current character in e.
The current character in l.
The current character in l.
The current character in o.
I'm now reading up on Python.
I'm now reading up on Java.
I'm now reading up on C.
I'm now reading up on JavaScript.
I'm now reading up on Swift.
I'm now reading up on Kotlin.
The current number is 4.
The current number is 8.
The current number is 15.
The current number is 16.
The current number is 23.
The current number is 42.
```

Like the `while` loop, Python’s `for` loop follows Python’s identation rules. The line with `for` ends with `:`, indicating that the indented lines that follow are the body of the loop.

### Traditional(ish) `for` Loops With the `range()` Function

There are times when you want a loop to perform an action a specific number of times. Many other programming languages provide a `for` loop to do this, using this syntax:

`for (`_set up counter variable_`;` _exit condition_ `;` _update counter variable_`)`

Python’s built-in `range()` function makes it possible emulate this kind of `for` loop by generating numbers as a sequence, which is what Python’s `for` loops are designed to do.

#### `range()` With a Stop Value

If you provide `range()` with a single integer _n_ — a _stop value_ — it creates a `range` object that generates a sequence of numbers beginning with 0, increasing by 1 each time, and going up to — but not including — the stop value _n_.

Run the following in a new code cell to see this form of `range()` in action:

```python
for number in range(5):
    print(number)
```

This prints the numbers 0 through 4, one number per line.

#### `range()` With a Start Value and a Stop Value

If you provide `range()` with two integers:

- _m_, a _start value_
- _n_, a _stop value_

...it creates a `range` object that generates a sequence of numbers beginning with the start value _m_, increasing by 1 each time, and going up to — but not including — the stop value _n_.

Run the following in a new code cell to see this form of `range()` in action.

```python
for number in range(-5, 5):
    print(number)
```

This prints the numbers -5 through 4, one number per line.

#### `range()` With a Start Value, a Stop Value, and a Step Value

If you provide `range()` with three integers:

- _m_, a _start value_
- _n_, a _stop value_
- _p_, a _step value_

...it creates a `range` object that generates a sequence of numbers beginning with the start value _m_, increasing by the step value _p_ each time, and going up to — but not including — the stop value _n_.

Run the following in a new code cell to see this form of `range()` in action. To show that it’s possible, this code assigns the range to a variable, and then has `for` use that variable:

```python
multiples_of_3 = range(-6, 20, 3)
for number in multiples_of_3:
    print(number)
```

This prints the numbers -6 through 18, one number per line.

### The Magic of `enumerate()`

When iterating over a sequence, it’s often necessary to be able to keep track of both the current item *and* its index. Here’s one way to do this:

```python
nato_letters = ["alfa", "bravo", "charlie", "delta", "echo"]
for index in range(len(nato_letters)):
    print(f"{index}. {nato_letters[index]}")
```

There’s a more Pythonic way to do this, and it’s by using Python’s built-in `enumerate()` function. When wrapped around an object that you can iterate over, it adds a counter to it.

`enumerate()` is one of those things where it’s better to show it in action rather than describe it:

```python
for index, letter in enumerate(nato_letters):
    print(f"{index}. {letter}")
```

## `else`

Like `while`, Python’s `for` loops also make use of the `else` keyword to define a block of code that will execute only when the loop completes “normally” — that is, without executing the `break` statement while in the loop:

```python
# Print all the oceans
oceans = ["Antarctic", "Artic", "Atlantic", "Indian", "Pacific"]
for ocean in oceans:
    print(ocean)
else:
    print("That's all of them!")
```

Here’s a `for` loop that _doesn’t_ end normally, which means that it skips the `else` block:

```python
# Skip the Pacific
for ocean in oceans:
    if ocean == "Pacific":
        break
    print(ocean)
else:
    print("That's all of them!")
```

If the code in a loop never executes, then it never encounters the `break` statement, and therefore it exits normally. This means that the `else` block is executed:

```python
for item in []:
    print("This will never execute...")
else:
    print("...but this will!")
```