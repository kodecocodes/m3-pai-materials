# Instructions

## Dictionaries

Python’s dictionaries are collections of key-value pairs, where you use a key to access the value associated with that key. They’re like JavaScript’s objects, Java’s HashMaps, C#’s and Swift’s dictionaries, PHP’s associative arrays, and Kotlin’s MutableMaps.

Python dictionary literals are a series of items separated by commas and surrounded by braces (a.k.a. “curly brackets”), as shown below:

```python
{"name": "Guido van Rossum", "position": "Python creator", "rank": "1"}
```

For readability, you can format a dictionary this way:

```python
{
    "name": "Guido van Rossum", 
    "position": "Python creator", 
    "rank": "1"
}
```

It shouldn’t be surprising that dictionary values can be of any Python type, but you may be surprised to find out that _keys_ can be any immutable type — a number, a string, a list, even another dictionary! For readability’s sake, you can expect to use strings as dictionary keys most of the time.

Since each value is a dictionary is accessed using its key as the “index,” each key in any dictionary is unique.

### Creating an Empty Dictionary

The simplest way to create an empty dictionary is to assign an empty dictionary literal to a variable:

```python
empty_dictionary = {}
```

You can confirm the dictionary’s type with the `type()` function:

```python
type(empty_dictionary)  # dict
```

You can also create a dictionary using object initialization syntax:

```python
another_empty_dictionary = dict()
```

### Creating Non-Empty Strings, Lists, and Tuples 

Here’s an example of creating a non-empty dictionary using a literal dictionary value:

```python
# Information about Alice the employee
employee = {
    "name": "Alice",
    "level": 5,
    "years": 2,
    "salary": 150_000
}
```

### Accessing Dictionary Values

One way to access values from a dictionary uses a notation similar to the one for lists. The difference is that instead of an index, you use the _key_ for the value you want to retrieve:

```python
employee = {
    "name": "Alice",
    "level": 5,
    "years": 2,
    "salary": 150_000
}

# Get the employee's salary
employee["salary"]  # 150000
```

Trying to accessing a value for a non-existent key results in an error:

```python
# Try to get a value for a non-existent key
employee["stock options"]  # KeyError
```

Fortunately, the `get()` method is a way access values in a dictionary with a “fallback value” in case the key doesn’t exist:

```python
# Try to get the value for the key "stock options" --
# if it doesn’t exist, use the value "n/a"
employee.get("stock options", "n/a")  # "n/a"
```

### Updating Dictionary Values

Updating a dictionary value is pretty straightforward: you use the assignment (`=`) operator on an existing key and provide a new value:

```python
employee = {
    "name": "Alice",
    "level": 5,
    "years": 2,
    "salary": 150_000
}

# Give our employee a raise
employee["salary"] += 10_000
```

With this update, the dictionary is now:

```python
{
    'name': 'Alice', 
    'level': 5, 
    'years': 2, 
    'salary': 160000
}
```

### Adding a New Key-Value Pair to a Dictionary

Adding a new key-value pair is similar to updating an existing value. The difference is that you use the assignment operator and use both a _new key_ and a new value:

```python
employee = {
    "name": "Alice",
    "level": 5,
    "years": 2,
    "salary": 150_000
}

# Give our employee some stock options
employee["stock options"] = 7_500
```

The dictionary is now:

```python
{
    'name': 'Alice',
    'level': 5,
    'years': 2,
    'salary': 150000,
    'stock options': 7500
}
```

### Removing a Key-Value Pair From a Dictionary Based on Its Key With `pop()`

The `pop()` method takes a key, removes the key-value pair for that key from the dictionary, and returns the value corresponding from that key-value pair:

```python
employee = {
    "name": "Alice",
    "level": 5,
    "years": 2,
    "salary": 150_000,
    "stock_options": 7_500
}

# Remove the `stock options` key and
# retrieve its value
stock_options = employee.pop("stock_options")
print(f"Removed value: {stock_options}")
print(employee)
```

The output for the code above is:

```
Removed value: 7500
{'name': 'Alice', 'level': 5, 'years': 2, 'salary': 150000}
```

Unlike lists, dictionaries aren’t considered ordered collections, so calling `pop()` without an argument — which removes and returns the last item in a list — has no meaning when done on a dictionary. Doing so results in an error.

### Removing a Key-Value Pair From a Dictionary Based on Its Key With `del`

Python’s all-purpose object-deleting `del` can also remove a key-value pair from a dictionary, but unlike `pop()`, it doesn’t return the value from the key-value pair.

```python
employee = {
    "name": "Alice",
    "level": 5,
    "years": 2,
    "salary": 150_000,
    "stock_options": 7_500
}

# Let’s remove the employee's stock options
# before they find out we gave them some
del employee["stock_options"]
print(employee)
```

The dictionary is now:

```python
{
    'name': 'Alice', 
    'level': 5, 
    'years': 2, 
    'salary': 150000
}
```

### Removing All Items From a Dictionary

The `clear()` method removes all items from a dictionary:

```python
another_employee = {
    "name": "Bob",
    "level": 1,
    "years": 0
}
another_employee.clear()
```

After running the code above, `another_employee` is now `{}`.

### Determining if a Given Key Is in a Dictionary

To determine if a dictionary has a given _key_ — not value — use the `in` operator, which returns `True` if the key is in the dictionary, and `False` otherwise:

```python
# `employee` has a key called "name"
if "name" in employee:
    print("There's a \"name\" key in this dictionary.")
    print(f"Its corresponding value is \"{employee["name"]}.\"")

# `employee` DOES NOT have a key called "has executive bathroom key"
if "has executive bathroom key" not in employee:
    print("This dictionary doesn't have a \"has executive bathroom key\" key.")
```

### Getting Lists of a Dictionary’s Keys and Values

#### Getting a Dictionary’s Keys and Values as Individual Collections

The `keys()` and `values()` methods return collections containing a dictionary’s keys and values:

```python
employee = {
    "name": "Alice",
    "level": 5,
    "years": 2,
    "salary": 150_000
}
print(f"keys:\n{employee.keys()}")
print(f"values:\n{employee.values()}")
```

The output should look like this:

```
keys:
dict_keys(['name', 'level', 'years', 'salary'])
values:
dict_values(['Alice', 5, 2, 150000])
```

Note that the keys and values, when printed out, aren’t lists, but `dict_keys` and `dict_values` objects. Since they’re not lists, you can’t access their items like lists:

```python
# Try to get the first item in `keys`
keys[0]  # "TypeError: 'dict_keys' object is not subscriptable"
```

While you can’t directly access items in `dict_keys` and `dict_values` objects, you _can_ use a `for` loop to iterate over them:

```python
# Iterating over `keys()` and `values()` 
# with a `for` loop
print("keys")
for key in keys:
    print(f"- {key}")
print("\nvalues")
for value in values:
    print(f"- {value}")
```

You can also create lists from `dict_keys` and `dict_values` objects using the `list()` function:

```python
# Turn the keys and values objects into lists
keys_list = list(keys)
values_list = list(values)
print(f"keys list:\n{keys_list}")
print(f"values list:\n{values_list}")
```

The `dict_keys` and `dict_values` objects returned by `keys()` and `values()` are dynamic view objects connected to their dictionary. Updating the dictionary also updates its `dict_keys` and `dict_values` objects.

Suppose the following were defined:

```python
employee = {
    "name": "Alice",
    "level": 5,
    "years": 2,
    "salary": 150_000
}
keys = employee.keys()
values = employee.values()
```

Now suppose these changes were made to the dictionary:

```python
# Suppose our employee social-engineered their way
# into the records
employee["name"] = "Alice the Great"
employee["level"] = 10
employee["salary"] = 1_000_000
employee["stock options"] = 100_000  # new key-value pair!
```

What would the output of the following code look like?

```python
print(f"keys:\n{keys}")
print(f"values:\n{values}")
```

Here’s what it would look like:

```
keys:
dict_keys(['name', 'level', 'years', 'salary', 'stock options'])
values:
dict_values(['Alice the Great', 10, 2, 1000000, 100000])
```

Even though you haven’t directly changed `keys` or `values` (you can’t; `dict_keys` and `dict_values` objects are read-only), the items in `keys` and `values` have updated to reflect the changes you made to the dictionary.

That’s because the `keys()` and `values()` method return objects that are connected to the dictionary. When the dictionary is updated, so are they.

#### Getting a Dictionary’s Keys and Values as Key-Value Tuples

The `items()` method is similar to the `keys()` and `values()` methods, except that it returns a dynamic view collection of the dictionary’s keys and values as tuples.

For the following code...

```python
employee = {
    "name": "Alice",
    "level": 5,
    "years": 2,
    "salary": 150_000
}
print(employee.items())
```

the output should look like this:

```python
dict_items([('name', 'Alice'), ('level', 5), ('years', 2), ('salary', 150000)])
```

`items()` doesn’t return a list, but a `dict_items` object. It’s not a list, and you can’t access its items like a list, but you _can_ iterate over its contents with a `for` loop:

```python
for item in employee.items():
    print(item)
```

Here’s its output:

```python
('name', 'Alice the Great')
('level', 10)
('years', 2)
('salary', 1000000)
('stock options', 100000)
```

You can also create a list from `items()` using the `list()` function.

### Determining if a Given Value Is in a Dictionary

There’s no built-in way to determine if a dictionary contains a given value, but you can use the `values()` method to get its values or the `items()` methods to get its key-value pairs and then see if they contain the value you’re looking for.


## Boolean Evaluations, “Truthy,” and “Falsy”

Now that the major data types have been covered, it’s time to talk about how they’re evaluated as as `True` or `False` by decision-making statements like `if`/`elif`/`else` and `while` and `for` loops.

It’s quite clear that the following values and expressions evaluate as `True` or `False`:

- `True`
- `False`
- `True and True or False`
- `some_value > 5`
- `some_value > 5 and some_other_value != "stop"`

It’s not obvious that _all_ values and expressions also evaluate as `True` or `False`. In Python, there are the concepts of _truthy_ and _falsy_ where:

- **truthy** refers to a value that evaluates to `True`.
- **falsy** refers to a value that evaluates to `False`.

Here’s an example:

```python
name = None
while not name:
    # The `strip()` method removes leading and trailing
    # whitespace from a string.
    name = input("Please enter your name: ").strip()
    if name:
        break

print(f"Hello, {name}!")
```

This code continues to ask the user to enter their name until they enter at least one non-whitespace character into the `input()` text box.

Notice that the `while` and `if` statements in the code aren’t operating on a boolean value or expression. They’re operating on `name`, which initially contains `None` and later contains the user’s input.

At the start of the `while` loop, the condition to enter the loop is `not name`. `name`’s initial value is `None`, which is falsy; in other words, Python evaluates None, which represents the absence of a value, as `False`.

Inside the loop, the `if name:` statement executes immediate after the user has provided input. If the user enters any text at all, `name` contains a non-empty string. Non-empty strings are truthy, and Python evaluates `name`’s value as `True`.

On the other hand, if the user did not enter any text and simply pressed the “return” key at the input prompt, `name` contains an empty string. Empty strings are falsy, and Python evaluates `name`’s value as `False`.

#### “Falsy” Values

The general rule to follow is that if a value indicates absence, emptiness, or the value zero, it probably evaluates as `False`. These include:

- `None`
- Any numerical value for zero
- Any empty string or collection

Here are some examples of falsy values in action:

```python
# `False` (of course) evaluates as `False`
if False:
    print("You'll never see this.")

# `None` evaluates as `False`
if None:
    print("You'll never see this.")

# Zero, whether in integer, floating-point, or complex,
# evaluates as `False`
if 0 or 0.0 or 0+0j:
    print("You'll never see this.")

# Any empty sequence, whether it's string, list, or tuple,
# evaluates as `False`
if "" or [] or ():
    print("You'll never see this.")

# Any empty dictionary evaluates as `False`
if {}:
    print("You'll never see this.")

print("You saw nothing!")
```

The only output you should see is `You saw nothing!`.

#### “Truthy” Values

The general rule to follow is that if a value indicates presence, non-emptiness, or a non-zero value, it probably evaluates as `True`. These include:

- Any object that isn’t `None` and meets one of the criteria below
- Any numerical value that isn’t zero
- Any string containing at least one character
- Any collection containing at least one item

Here are some examples of truthy values in action:

```python
# `True` (of course) evaluates as `True`
if True:
    print("True is True.")

# Any non-zero number, whether in integer, floating-point, or complex,
# evaluates as `True`
if -1 and 2.0 and -3+4j:
    print("Any non-zero number is True.")

# Any non-empty sequence, whether it's string, list, or tuple,
# evaluates as `True`
if "anything" and [11, 5, 8] and (False, False):
    print("Any non-empty sequence is True.")

# Any non-empty dictionary evaluates as `True`
if {"status": "non-empty"}:
    print("Any non-empty dictionary is True.")
```


## Functions

### Basic Functions

Here’s a definition of the simplest type of function — the type that take any arguments and it doesn’t return any values:

```python
def say_hello():
    """Say hello to the user.""" # This is a docstring (see below)
    print("Hey there! Welcome.")
```

Function definitions start with the `def` keyword — short for _define_ — followed by the function name, which in this case is `say_hello()`. Like many other programming languages, the function name ends with parentheses.

When you run a code cell with one or more function definitions in it, those functions will not execute unless some other code in that cell calls them. Once you run a code cell containing function definitions, those functions will remain “in scope” and available to any other code cells for as long as Jupyter is running.

### Docstrings

You may have been wondering about the first line of `say_hello()`’s body (shown below without the comment that followed it):

```python
    """Say hello to the user"""
```

That’s a _docstring_ — short for “documentation string” — and it’s a triple-quoted string literal on the first line in a function, method, class, or module. They’re for providing a concise explanation of the purpose, behavior, and usage of the function, method, class, or module.

> Defining methods, and classes will be covered in Lesson 2 of this course.

Docstrings are more than mere comments. As long as you put the docstring on the first line of the function, method, class, or module, it becomes accessible via the special built in `__doc__` property of those objects!

The following code prints the docstring for `say_hello()`:

```python
print(say_hello.__doc__)  # "Say hello to the user."
```

> `__doc__` is part of a family of special Python properties and methods that begins and ends with double underscores (`__`). They’re called _dunder properties_ and _dunder methods_, where “dunder” is a shortening of “**d**ouble **under**score”. `__doc__` can be pronounced “dunder doc.”

### Passing Values to a Function

Python functions can take single arguments, as shown in the code below:

```python
def say_oh_hi_with_name(name):
    print(f"Oh hi, {name}!")
```

You would call this function like so:

```python
say_oh_hi_with_name("Mark")
```

Like other languages’ functions, Python functions can also take multiple arguments:

```python
def say_oh_hi_multiple_times(name, repetitions):
    for count in range(repetitions):
        print(f"Oh hi, {name}!")
```

This call will print “Oh hi, Mark!” five times:

```python
say_oh_hi_multiple_times("Mark", 5)
```

Python supports _keyword arguments_, where the function caller can specify which arguments are for which parameters:

```python
say_oh_hi_multiple_times(repetitions=3, name="Lisa")
```

Keyword arguments, while they make a function call more verbose, have a couple of advantages:

- It’s very clear which argument corresponds with which parameter.
- It allows you to call a function without worrying about the order of arguments.

Finally, Python allows for default values for function parameters. Consider the function below:

```python
def say_oh_hi_multiple_times(name, repetitions=2):
    for count in range(repetitions):
        print(f"Oh hi, {name}!")
```

If `say_oh_hi_multiple_times()` were called this way...

```python
say_oh_hi_multiple_times("Denny")
```

...it would result in “Oh hi, Denny!” being printed two times. Since the call did not provide a value for `repetitions`, it used the default value specified in the function’s parameter list, `2`.

If you provide default values for a function’s parameters, they must be listed after all the parameters that don’t have default values, just as was done with `say_oh_hi_multiple_times()`, where `name` (which doesn’t have a default value) appears before `repetitions` (which does).

> By the way, for the purposes of this course, the term _argument_ is used to refer to data that is passed to a function when calling it, and the term _parameter_ is used to refer to a variable in a function that stores the value of an argument passed to the function.

### Returning a Value from a Function

Just like other programming languages’ functions, programs exit a function and return a single value with the `return` statement:

```python
def create_greeting(name):
    return f"Greetings and salutations, {name}!"
```

This code uses the return value of `create_greeting()`:

```python
print(f"My message is: {create_greeting("Johnny")}")
```

While `return` returns just one value, that value can be any Python object, which can be a number, string, or boolean, but could also be a list, tuple, dictionary, or any other type of object.

#### Every Function Returns a Value

While it’s obvious that functions with a `return` statement return a value, functions that _don’t_ have `return` statements also return a value: `None`.

For example, here are two functions — one that returns an integer, and one that doesn’t have a return value:

```python
# This function returns an integer
def return_5():
    return 5

# This function doesn’t have
# an explicit return value
def return_nothing():
    # This is how you mark an
    # empty code block 
    # (see "Empty Blocks," below)
    pass
```

If you were to run the code below to see the type returned by each function, you’d see the following:

- `type(return_5())`  # int
- `type(return_nothing())`  # NoneType

### Naming Functions

As with variables, there are generally-accepted rules for naming functions in Python. The key points are:

- Use snake case! Function names should be all lowercase, with multi-word names using underscores to separate words (e.g. use names like `my_function()` and not `myFunction()`.)
- Use only letters, numbers, and underscores in function names.
- Function names can start with a letter or underscore. They should not start with numbers.
- Names that begin or end with double underscores have special meaning in Python — don’t use these names unless you know what you’re doing.
- Don’t use Python’s reserved keywords as function names.


## Empty Blocks

In the process of writing a program, you will often start with empty “placeholder” blocks of code that you intend to fill later.

Consider this JavaScript function:

```javascript
// This is in JavaScript
function returnNothing() {
    // TODO: Implement later
}
```

The body of the `returnNothing()` function above is an empty code block, where the start and end of the block are clearly marked by _visible_ characters: `{` and `}` with nothing but whitespace and comments between them.

Python’s code blocks are marked by indentation, which is created using _invisible_ characters. Because of this, there’s no definitive way to tell the difference between and empty block of code and a missing block of code.

If you try to define an empty function like so...

```python
def empty_function():
    # You can’t see it, but this line is indented!
```

...this will cause an error (“SyntaxError: incomplete input”).

To solve this problem and allow you to create empty “placeholder” blocks, Python has the `pass` keyword, which specifies an empty code block.

The function below is the Python equivalent of the JavaScript `returnNothing()` function above:

```python
def return_nothing():
    # TODO: Implement later
    pass
```