### Python Strings: 

### 1. Introduction to Strings
+ **string** is a sequence of characters or list of char ( char and string is same in python). It can include letters, numbers, symbols, and whitespace.

#### a. Creation
In Python, you can create a string using three types of quotes:
* **Single Quotes:** `'Hello'`
* **Double Quotes:** `"Hello"` (Most common)
* **Triple Quotes:** `'''Hello'''` or `"""Hello"""` (Used for multi-line strings).

```python
simple_string = "Python is fun!"
multi_line = """This string
spans across
multiple lines."""
```
#### b. F-Strings (Formatted String Literals)
1. Introduced in Python 3.6, **f-strings** best and modern allow you to embed expressions directly inside string literals by prefixing the string with `f` or `F`.

```python
name = "Pythn"
version = 3.12
# F-string automatically replaces {variable} with its value
print(f"I am {name} My version is: {version}")
f"Next year I’ll be {age + 1}"   # {age + 1} is a Python expression. It gets evaluated before converting to string
```
2. str.format() (still useful)
```
s = "My name is {} and I am {}".format(name, age)
"{0} scored {1} marks".format("Alice", 95)  # with index
"{name} scored {marks}".format(name="Bob", marks=90)  # with name
```
3. Old % formatting (C-style – avoid)
` s = "My name is %s and I am %d" % (name, age)`

4. Formatting numbers (VERY common)
```
pi = 3.14159
f"{pi:.2f}" # Float precision formatting output: 3.14
```
5. Padding numbers with zeros
`f"{42:05d}"`
+ 5 → total width
+ 0 → pad with zeros
+ d → integer
6. Text alignment
`f"{'hi':<10}"  output: "hi        "`
+ < → left align
+ 10 → total width
```
f"{'hi':>10}"   # right
f"{'hi':^10}"   # center
```
> **Note:** There is no difference between `' '` and `" "`, but you should be consistent.

### 2. String Properties
1. **Ordered:** Every character has a specific position (index).
2. **Immutable:** Once a string is created, its characters **cannot** be changed.
3. **Iterable:** You can loop through a string character by character.

```
s = "Python"
print(s[0])    # 'P'  Each String start with index 0
print(s[-1])   # 'n' (last character)
# s[0] = 'J'   # ERROR: Strings cannot be changed!
```

### 3. Indexing and Slicing
Python uses **0-based indexing**, meaning the first character is at index `0`.

#### Indexing
Access a single character using square brackets `[]`.
* **Positive Indexing:** Starts from `0` (left to right).
* **Negative Indexing:** Starts from `-1` (right to left).

```python
word = "PYTHON"
# P  Y  T  H  O  N
# 0  1  2  3  4  5 (Positive)
#-6 -5 -4 -3 -2 -1 (Negative)

print(word[0])  # Output: P
print(word[-1]) # Output: N
```

#### Slicing
Extract a portion of a string using the syntax: `[start : stop : step]`
* **Start:** Starting index (inclusive).
* **Stop:** Ending index (exclusive).
* **Step:** How many characters to jump (default is 1).

```python
text = "Programming"
print(text[0:4])   # Output: Prog
print(text[:7])    # Output: Program (starts from 0)
print(text[7:])    # Output: ming (goes to the end)
print(text[::-1])  # Output: gnimmargorP (reverses the string)
```
> **Note**: Each slice create a new string

### 4. Basic Operations
* **Concatenation (+):** Joining strings together.
* **Repetition (*):** Repeating a string multiple times.
* **Length (`len()`):** Getting the total number of characters.

```python
first = "Hello"
second = "World"
print(first + " " + second) # Output: Hello World
print("Ha" * 3)             # Output: HaHaHa
print("Ha"*"Ka")            # Error
print(len("Python"))        # Output: 6
```


### 5. Built-in Methods
Methods are functions that "belong" to the string object. They return **new** strings because the original is immutable.
s = "PyThoN"

| Method | Usage | Result |Output|
| :--- | :--- | :--- | :---|
| `.upper()` | `s.upper()` | Converts to ALL CAPS |"PYTHON"|
| `.lower()` | `s.lower()` | Converts to all lowercase |"python"|
| `.title()` | `s.title()` | Capitalizes the first letter of every word |"PyThoN"|
| `.strip()` | `s.strip()` | Removes leading/trailing whitespace (trim() in java) |"PyThoN"|
| `.find()` | `s.find('x')` | Returns index of first 'x' found |return -1 if not found|
| `.replace()`|`s.replace('oN', 'oFF'|replace & return new string| "PyThoFF"|
| `.split()`| `s.split("T")`| return a list of string| ['Py', 'hoN'] |

### 6. String Formatting (F-Strings)
F-strings are the easiest way to inject variables into strings.

```python
name = "Alice"
age = 25
message = f"My name is {name} and I am {age} years old."
print(message)
```

---

## 📒 Space for Further Additions
> Use this section to add new beginner-level observations or specific edge cases you encounter during practice.

* **Addition 1:** _________________________________________________
* **Addition 2:** _________________________________________________
* **Addition 3:** _________________________________________________

---

## 🛠 Beginner Exercises to Try
1. Create a string and print only the middle character.
2. Take a user's name as input and print it in reverse.
3. Check if the word "Python" exists in the sentence "I love Python programming" using the `in` keyword.
