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

A string is a sequence of characters.

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

```python
name = "Suhas"
age = 30

print("My name is {} and I am {} years old.".format(name, age))
```

You can also use positional indexes:

```python
print("My name is {0} and I am {1} years old.".format(name, age))
```

---

## 4. F-String Formatting

F-strings provide a simpler way to insert variables into strings.

```python
name = "Suhas"
age = 30

print(f"My name is {name} and I am {age} years old.")
```

F-strings are commonly preferred in modern Python because they are readable and convenient.

---

## 5. Lists

A list is an **ordered sequence** that can hold different types of objects.

Lists support:

- Indexing
- Slicing
- Reassignment
- Duplicate values
- Different data types

```python
new_list = [1, "Hello", 3.14, True]
```

### Indexing

```python
new_list[0]
new_list[1]
```

### Slicing

```python
new_list[:2]
new_list[1:]
```

### Lists Are Mutable

Unlike strings, individual list elements can be changed.

```python
new_list = [1, 2, 3]

new_list[0] = 100

print(new_list)
# [100, 2, 3]
```

### Common List Methods

#### `append()`

Adds an item to the end of the list.

```python
new_list.append(4)
```

#### `pop()`

Removes and returns an item.

By default, it removes the **last item**.

```python
new_list.pop()
```

You can also provide an index:

```python
new_list.pop(1)
```

#### `sort()`

Sorts a list in place.

```python
new_list = [3, 1, 2]
new_list.sort()

print(new_list)
# [1, 2, 3]
```

Important: `sort()` returns `None`.

```python
result = new_list.sort()
print(result)
# None
```

#### `reverse()`

Reverses the list in place.

```python
new_list.reverse()
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

A dictionary allows you to retrieve values using keys instead of numeric indexes.

```python
person = {
    "name": "Suhas",
    "age": 30
}

print(person["name"])
# Suhas
```

### Important Point

Modern Python dictionaries preserve **insertion order**. They are not unordered in the sense that the order is lost, although they are still conceptually mappings rather than sequences indexed by position.

### Adding or Updating Values

```python
person["city"] = "Pune"
person["age"] = 31
```

### Getting a Value

```python
person["name"]
```

You can also use:

```python
person.get("name")
```

---

## 7. Tuples

Tuples are similar to lists, but they are **immutable**.

Once an element is stored in a tuple, it cannot be reassigned.

```python
my_tuple = (1, 2, 3)
```

This is not allowed:

```python
my_tuple[0] = 100
# TypeError
```

### Tuple Methods

Tuples have two commonly available methods:

```python
my_tuple.count(2)
my_tuple.index(2)
```

- `count()` — counts how many times a value occurs.
- `index()` — returns the index of the first occurrence.

---

## 8. Sets

Sets are collections of **unique elements**.

```python
my_set = {1, 2, 3}
```

Duplicate values are automatically removed:

```python
my_set = {1, 2, 2, 3, 3}

print(my_set)
# {1, 2, 3}
```

Sets are useful when you need to:

- Remove duplicates
- Test membership
- Perform mathematical set operations

Example:

```python
my_set.add(4)
my_set.remove(2)
```

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

Use `seek(0)` to move it back to the beginning.

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

### Explicit Read Mode

```python
with open("myfile.txt", mode="r") as myfile:
    contents = myfile.read()
```

`mode="r"` means **read**.

### Writing to a File

```python
a = open("test.txt", mode="w")
a.write("Hello World")
a.close()
```

`mode="w"` means **write**.

Be careful: writing with `w` can overwrite an existing file.

A safer modern pattern is:

```python
with open("test.txt", mode="w") as file:
    file.write("Hello World")
```

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
