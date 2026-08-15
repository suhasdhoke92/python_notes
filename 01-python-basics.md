# Python Basics Notes

A beginner-friendly reference covering Python data types, strings, lists, dictionaries, tuples, sets, booleans, file I/O, comparison operators, and conditional statements.

---

## 1. Data Types

Python uses **dynamic typing**, which means you do not need to explicitly declare the type of a variable.

```python
x = 10
x = "Hello"
```

The same variable can refer to objects of different types during execution.

### Common Python Data Types

| Name | Type | Description | Example |
|---|---|---|---|
| Integers | `int` | Whole numbers | `3`, `300`, `200` |
| Floating point | `float` | Numbers with a decimal point | `2.3`, `4.6`, `100.0` |
| Strings | `str` | Ordered sequence of characters | `"hello"`, `"Sammy"`, `"2000"` |
| Lists | `list` | Ordered sequence of objects | `[10, "hello", 200.3]` |
| Dictionaries | `dict` | Key-value pairs | `{"mykey": "value", "name": "Frankie"}` |
| Tuples | `tuple` | Ordered immutable sequence | `(10, "hello", 200.3)` |
| Sets | `set` | Collection of unique elements | `{"a", "b"}` |
| Booleans | `bool` | Logical value | `True`, `False` |

---

### `type()`

Used to check the data type of an object.

```python
x = 10
print(type(x))
```

Output:

```text
<class 'int'>
```

### `len()`

Returns the number of items in an object.

```python
name = "Python"
print(len(name))
```

Output:

```text
6
```

### `print()`

Used to display information.

```python
print("Hello World")
```

---

## 2. Strings

A string is an **ordered sequence of characters**.

```python
x = "Hello World"
```

### String Indexing

Python uses zero-based indexing.

```python
x = "Hello"

print(x[0])   # H
print(x[1])   # e
```

### String Slicing

```python
x[1]       # Character at index 1
x[:2]      # From beginning up to index 2 (not included)
x[3:]      # From index 3 to the end
x[::2]     # Every second character
x[::-1]    # Reverse the string
```

Example:

```python
x = "Python"

print(x[1])      # y
print(x[:2])     # Py
print(x[3:])     # hon
print(x[::2])    # Pto
print(x[::-1])   # nohtyP
```

### Strings Are Immutable

Strings are **immutable**, meaning you cannot change an individual character using indexing.

```python
x = "Hello"

# x[0] = "J"     # TypeError
```

Instead, create a new string:

```python
x = "J" + x[1:]
print(x)
```

### Common String Methods

```python
x = "hello world"

x.upper()       # HELLO WORLD
x.lower()       # hello world
x.split("i")    # Splits the string wherever "i" occurs
```

Example:

```python
x = "This is Python"

print(x.split("i"))
```

---

## 3. `.format()` Method

The `.format()` method is used to insert values into a string.

### Basic Replacement

```python
print("This is a string {}".format("INSERTED"))
```

Output:

```text
This is a string INSERTED
```

### Positional Arguments

You can use indexes inside `{}` to specify which argument should be inserted.

```python
print("The {0} {0} {0}".format("fox", "brown", "quick"))
```

Output:

```text
The fox fox fox
```

The same index refers to the same value each time.

### Keyword Arguments

You can provide names for the values and reference those names inside the string.

```python
print("The {q} {b} {f}".format(
    f="fox",
    b="brown",
    q="quick"
))
```

Output:

```text
The quick brown fox
```

### Using Variables

```python
name = "Jose"

print("Hello, his name is {}".format(name))
```

Output:

```text
Hello, his name is Jose
```

### Float Formatting

Float formatting follows this pattern:

```text
{value:width.precisionf}
```

Example:

```python
result = 100 / 777

print(result)
```

Output:

```text
0.1287001287001287
```

To limit the number of decimal places:

```python
print("The result was {r:10.3f}".format(r=result))
```

Output:

```text
The result was      0.129
```

Here:

- `r` is the variable.
- `10` is the field width.
- `.3f` displays the number with **3 digits after the decimal point**.
- `f` indicates floating-point formatting.

---

## 4. F-String Formatting

F-strings provide a simple way to insert variables and expressions directly into a string.

Use the `f` before the opening quote:

```python
name = "Jose"

print(f"Hello, his name is {name}")
```

Output:

```text
Hello, his name is Jose
```

### Why Use F-Strings?

F-strings are generally easier to read than `.format()` because the variable is placed directly inside `{}`.

```python
name = "Jose"
age = 30

print(f"My name is {name} and I am {age} years old.")
```

You can also include expressions:

```python
a = 10
b = 20

print(f"The total is {a + b}")
```

### Float Formatting with F-Strings

The same formatting rules can be used with f-strings:

```python
result = 100 / 777

print(f"The result was {result:10.3f}")
```

Output:

```text
The result was      0.129
```

---

## 5. Lists

A list is an **ordered sequence** that can hold different types of objects.

```python
my_list = [1, 2, 3]
```

Lists can contain different data types:

```python
my_list = ["STRING", 100, 23.2]
```

### Length of a List

```python
print(len(my_list))
```

Output:

```text
3
```

### List Indexing

```python
my_list[0]
my_list[1]
my_list[2]
```

### List Slicing

Lists support the same slicing syntax as strings:

```python
my_list[:2]
my_list[1:]
my_list[::2]
my_list[::-1]
```

### Lists Are Mutable

Unlike strings, list elements can be reassigned.

```python
my_list = [1, 2, 3]

my_list[0] = 100

print(my_list)
# [100, 2, 3]
```

### Common List Methods

#### `append()`

Adds an item to the end of the list.

```python
my_list.append(4)
```

#### `pop()`

Removes and returns an item.

By default, it removes the **last item**:

```python
my_list.pop()
```

You can provide an index:

```python
my_list.pop(1)
```

#### `sort()`

Sorts a list in place.

```python
my_list = [3, 1, 2]
my_list.sort()

print(my_list)
# [1, 2, 3]
```

`sort()` modifies the original list and returns `None`.

```python
result = my_list.sort()
print(result)
# None
```

#### `reverse()`

Reverses the list in place.

```python
my_list.reverse()
```

---

## 6. Dictionaries

Dictionaries store data using **key-value pairs**.

```python
my_dict = {
    "key1": "value1",
    "key2": "value2"
}
```

### Accessing Values

Use the key to retrieve its associated value.

```python
print(my_dict["key1"])
```

### Adding a New Key-Value Pair

```python
d = {
    "k1": 100,
    "k2": 200
}

d["k3"] = 300

print(d)
# {'k1': 100, 'k2': 200, 'k3': 300}
```

### Updating an Existing Value

```python
d["k1"] = "NEW VALUE"
```

Dictionaries are mutable, so existing values can be changed.

### `keys()`

Returns the dictionary's keys.

```python
d.keys()
```

Example result:

```text
dict_keys(['k1', 'k2', 'k3'])
```

### `values()`

Returns the dictionary's values.

```python
d.values()
```

Example result:

```text
dict_values([100, 200, 300])
```

### `items()`

Returns the dictionary's key-value pairs.

```python
d.items()
```

You can use it when you need both the key and value.

### `get()`

Another way to retrieve a value:

```python
d.get("k1")
```

Unlike `d["missing_key"]`, `get()` returns `None` by default if the key does not exist.

### Important Point

Modern Python dictionaries preserve **insertion order**. They are mappings based on keys rather than sequences based on numeric indexes.

---

## 7. Tuples

Tuples are similar to lists, but they are **immutable**.

```python
t = ("a", "a", "b")
```

Once an element is stored in a tuple, it cannot be reassigned.

```python
# t[0] = "x"    # TypeError
```

### `count()`

Counts how many times a value occurs.

```python
t.count("a")
```

Output:

```text
2
```

### `index()`

Returns the index of the first occurrence of a value.

```python
t.index("a")
```

For the tuple:

```python
t = ("a", "a", "b")
```

the result is:

```text
0
```

Tuples have two commonly used methods:

- `count()`
- `index()`

---

## 8. Sets

Sets are collections of **unique elements**.

```python
myset = set()
```

### Adding Elements

Use `add()`:

```python
myset.add(1)

print(myset)
# {1}
```

### Removing Duplicates

A set can be created from a list to remove duplicate values.

```python
mylist = [1, 1, 1, 1, 2, 2, 2, 3, 3, 3]

print(set(mylist))
```

Output:

```text
{1, 2, 3}
```

### Important Properties

- Sets contain unique values.
- Sets do not support indexing like lists.
- Sets are useful for removing duplicates.
- Use `set()` to create an empty set.

Important:

```python
myset = {}
```

creates an **empty dictionary**, not an empty set.

Use:

```python
myset = set()
```

to create an empty set.

---

## 9. Booleans

Booleans represent one of two values:

```python
True
False
```

They are commonly used with conditions and logical operations.

```python
is_logged_in = True

print(is_logged_in)
```

---

## 10. Basic File I/O

Python provides built-in functionality for reading and writing files.

### Opening a File

```python
myfile = open("myfile.txt")
```

### Reading a File

```python
myfile.read()
```

### Resetting the File Position

After reading a file, the file pointer is at the end.

Use `seek(0)` to move it back to the beginning:

```python
myfile.seek(0)
myfile.read()
```

### Reading Lines

```python
myfile.readlines()
```

### Closing a File

```python
myfile.close()
```

### Recommended Approach: `with open()`

Using `with` automatically closes the file.

```python
with open("myfile.txt") as my_new_file:
    contents = my_new_file.read()

print(contents)
```

---

### File Modes

The `mode` argument determines what you can do with the file.

| Mode | Meaning |
|---|---|
| `r` | Read only |
| `w` | Write only; overwrites an existing file or creates a new one |
| `a` | Append; adds data to the end of the file |
| `r+` | Reading and writing |
| `w+` | Writing and reading; overwrites an existing file or creates a new one |

### Read Mode

```python
with open("my_new_file.txt", mode="r") as f:
    contents = f.read()

print(contents)
```

### Write Mode

```python
with open("test.txt", mode="w") as f:
    f.write("Hello World")
```

**Warning:** `w` can overwrite the existing contents of a file.

---

### Append Mode

Use `a` when you want to add content without replacing existing content.

```python
with open("my_new_file.txt", mode="a") as f:
    f.write("\nFOUR ON FOURTH")
```

If the file previously contained:

```text
ONE ON FIRST
TWO ON SECOND
THREE ON THIRD
```

after the append operation it will contain:

```text
ONE ON FIRST
TWO ON SECOND
THREE ON THIRD
FOUR ON FOURTH
```

This is useful when you want to add new data to an existing file.

---

## 11. Comparison Operators

Comparison operators compare values and return `True` or `False`.

### Examples

```python
"Bye" == "bye"
# False
```

String comparison is case-sensitive.

```python
2.0 == 2
# True
```

```python
2 <= 5
# True
```

### Common Comparison Operators

| Operator | Meaning |
|---|---|
| `==` | Equal to |
| `!=` | Not equal to |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal to |
| `<=` | Less than or equal to |

---

## 12. Chaining Comparison Operators

Python allows multiple comparisons to be chained.

```python
1 < 2 < 3
# True
```

```python
1 < 2 > 3
# False
```

This:

```python
1 < 2 < 3
```

is equivalent to:

```python
1 < 2 and 2 < 3
```

---

## 13. Logical Operators

Python provides three main logical operators:

### `and`

Returns `True` when all required conditions are true.

```python
(1 < 2) and (2 < 3)
# True
```

### `or`

Returns `True` when at least one condition is true.

```python
(1 > 5) or (2 < 3)
# True
```

### `not`

Reverses a Boolean result.

```python
not (1 == 1)
# False
```

Example:

```python
("h" == "h") and (2 == 2)
# True
```

---

## Quick Reference

| Topic | Key Point |
|---|---|
| Dynamic typing | Variable types do not need explicit declaration |
| `type()` | Checks the type of an object |
| `len()` | Returns the number of items |
| `print()` | Displays output |
| String | Immutable sequence of characters |
| List | Mutable ordered collection |
| Dictionary | Key-value mapping |
| Tuple | Immutable ordered collection |
| Set | Collection of unique elements |
| Boolean | `True` or `False` |
| `open()` | Opens a file |
| `read()` | Reads file contents |
| `write()` | Writes to a file |
| `==` | Checks equality |
| `and` | All conditions must be true |
| `or` | At least one condition must be true |
| `not` | Reverses a Boolean |

---

## Key Things to Remember

1. **Strings are immutable; lists are mutable.**
2. Python indexing starts at **0**.
3. `list.pop()` removes the **last item by default**.
4. `list.sort()` modifies the list and returns `None`.
5. Dictionaries use **keys**, not numeric indexes.
6. Tuples cannot be modified after creation.
7. Sets contain **unique elements**.
8. Use `with open(...)` when working with files whenever possible.
9. Comparison operators return Boolean values.
10. `and`, `or`, and `not` are logical operators used to combine Boolean conditions.
