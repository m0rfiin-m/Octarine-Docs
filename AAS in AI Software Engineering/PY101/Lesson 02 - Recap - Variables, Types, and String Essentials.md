# Recap: Variables, Types, and String Essentials

**Date:** October 21, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 1, Lesson 2

## What You'll Learn

This lesson covers Python's type system, variable assignment, and essential string operations. Understanding types is fundamental to avoiding errors and writing effective Python code.

---

## Python's Type System

Every value in Python has a type. The type determines what operations you can perform on that value.

### Checking Types with `type()`

Use the `type()` function to see what type a value has.

```python
x = 5
print(type(x))
# Output: <class 'int'>

x = "five"
print(type(x))
# Output: <class 'str'>
```

**Key Insight:** Variables in Python can hold different types at different times. The same variable `x` held an integer, then a string.

---

## The Three Core Types

### 1. Integers (`int`)

Whole numbers without decimal points.

```python
age = 25
temperature = -10
score = 0

print(type(age))
# Output: <class 'int'>
```

**Characteristics:**
- No decimal point
- Can be positive, negative, or zero
- Used for counting, indexing, and whole-number math

### 2. Floats (`float`)

Numbers with decimal points.

```python
price = 19.99
pi = 3.14159
percentage = 0.85

print(type(price))
# Output: <class 'float'>
```

**Characteristics:**
- Always include a decimal point (even `3.0`)
- Used for precise measurements, money, percentages
- Can represent very large or very small numbers

### 3. Strings (`str`)

Text data enclosed in quotes.

```python
name = "Marco"
message = 'Hello, World!'
number_as_text = "123"

print(type(name))
# Output: <class 'str'>
```

**Characteristics:**
- Enclosed in single `'...'` or double `"..."` quotes
- Can contain letters, numbers, symbols, spaces
- Even numbers in quotes are strings, not numbers

---

## Type Detection in Practice

### Multiple Types in a List

```python
items = [42, 3.14, "hello"]
for item in items:
    print(type(item))

# Output:
# <class 'int'>
# <class 'float'>
# <class 'str'>
```

**What This Shows:**
- `42` is an integer
- `3.14` is a float
- `"hello"` is a string
- Python automatically determines types

---

## Variable Assignment and Reassignment

### Creating Variables

Use the assignment operator `=` to store values in variables.

```python
total_cost = 20
print(total_cost)
# Output: 20
```

**Syntax:** `variable_name = value`

### Reassigning Variables

Variables can be reassigned to new values at any time.

```python
total_cost = 20
print(total_cost)
# Output: 20

total_cost = 54
print(total_cost)
# Output: 54
```

**Important:** The old value is replaced. There's no history kept.

### Type Changes

Variables can change types when reassigned.

```python
x = 100        # x is an int
print(type(x))  # <class 'int'>

x = "text"     # Now x is a string
print(type(x))  # <class 'str'>

x = 3.14       # Now x is a float
print(type(x))  # <class 'float'>
```

**Python's Flexibility:** Unlike some languages, Python variables aren't locked to one type.

---

## String Operations

### Escape Sequences

Use the backslash `\` to include special characters in strings.

#### Quotes Inside Strings

```python
print("Marco's \"python\"")
# Output: Marco's "python"
```

**Common Escape Sequences:**
- `\"` - Double quote
- `\'` - Single quote
- `\n` - New line
- `\t` - Tab
- `\\` - Backslash itself

**Examples:**

```python
print('It\'s a beautiful day')
# Output: It's a beautiful day

print("Line 1\nLine 2")
# Output:
# Line 1
# Line 2

print("Column1\tColumn2")
# Output: Column1    Column2
```

### Alternative: Single vs Double Quotes

You can avoid some escaping by mixing quote types.

```python
# Using double quotes outside, single inside
print("Marco's code")
# Output: Marco's code

# Using single quotes outside, double inside
print('He said "Hello"')
# Output: He said "Hello"
```

---

## F-Strings for Variable Insertion

F-strings (formatted string literals) let you embed variables directly in strings.

### Basic F-String Syntax

```python
name = "Marco"
print(f"Hello, {name}!")
# Output: Hello, Marco!
```

**Format:** `f"text {variable} more text"`

### Spacing Matters

```python
name = "Marco"

# No space after comma
print(f"Hello,{name}!")
# Output: Hello,Marco!

# With space after comma
print(f"Hello, {name}!")
# Output: Hello, Marco!
```

**Tip:** Spaces inside the f-string template are preserved exactly as written.

### Multiple Variables

```python
first = "Marco"
last = "Morfin"
age = 25

print(f"{first} {last} is {age} years old")
# Output: Marco Morfin is 25 years old
```

### Expressions in F-Strings

You can include calculations inside the curly braces.

```python
price = 10
quantity = 3

print(f"Total: ${price * quantity}")
# Output: Total: $30
```

```python
width = 5
height = 8

print(f"Area: {width * height} square feet")
# Output: Area: 40 square feet
```

---

## Type Compatibility and Conversion

### The Problem: Mixing Types

Not all operations work with all types.

```python
age = 25
# This works (int + int)
next_year = age + 1

# This doesn't work (str + int)
message = "Age: " + age  # TypeError!
```

### Solution 1: Converting to String with `str()`

```python
age = 25
message = "Age: " + str(age)
print(message)
# Output: Age: 25
```

### Solution 2: Use F-Strings (Easier)

```python
age = 25
print(f"Age: {age}")
# Output: Age: 25
```

**Why F-Strings Are Better:** They handle type conversion automatically.

---

## Common Type Errors and Fixes

### Error 1: Concatenating String and Number

```python
# Bad: TypeError
score = 100
print("Score: " + score)  # Can't add str + int
```

```python
# Fix 1: Convert to string
score = 100
print("Score: " + str(score))

# Fix 2: Use f-string (recommended)
print(f"Score: {score}")

# Fix 3: Use comma in print (adds space)
print("Score:", score)
```

### Error 2: Math on Strings

```python
# Bad: These look like numbers but they're strings
x = "10"
y = "5"
print(x + y)
# Output: 105 (concatenation, not addition!)
```

```python
# Fix: Convert to numbers first
x = "10"
y = "5"
print(int(x) + int(y))
# Output: 15
```

---

## Practical Examples

### Example 1: Student Record

```python
student_name = "Marco"
student_age = 25
student_gpa = 3.85

print(f"Student: {student_name}")
print(f"Age: {student_age}")
print(f"GPA: {student_gpa}")

# Output:
# Student: Marco
# Name: 25
# GPA: 3.85
```

### Example 2: Shopping Cart

```python
item = "laptop"
price = 999.99
quantity = 2

total = price * quantity
print(f"Item: {item}")
print(f"Price: ${price}")
print(f"Quantity: {quantity}")
print(f"Total: ${total}")

# Output:
# Item: laptop
# Price: $999.99
# Quantity: 2
# Total: $1999.98
```

### Example 3: Type Inspection

```python
data = [42, "hello", 3.14, True]

for item in data:
    print(f"Value: {item} | Type: {type(item)}")

# Output:
# Value: 42 | Type: <class 'int'>
# Value: hello | Type: <class 'str'>
# Value: 3.14 | Type: <class 'float'>
# Value: True | Type: <class 'bool'>
```

---

## Practice Exercises

**Exercise 1: Variable Types**

Create variables of each type (int, float, str) and print their types.

<details>
<summary>Solution</summary>

```python
age = 25
price = 19.99
name = "Marco"

print(type(age))    # <class 'int'>
print(type(price))  # <class 'float'>
print(type(name))   # <class 'str'>
```
</details>

**Exercise 2: F-String Practice**

Create variables for first name, last name, and age. Print a complete sentence using an f-string.

<details>
<summary>Solution</summary>

```python
first = "Marco"
last = "Morfin"
age = 25

print(f"My name is {first} {last} and I am {age} years old.")
# Output: My name is Marco Morfin and I am 25 years old.
```
</details>

**Exercise 3: Type Conversion**

Fix this code that tries to add a string and a number:

```python
score = 100
bonus = "50"
total = score + bonus  # This will error!
```

<details>
<summary>Solution</summary>

```python
score = 100
bonus = "50"
total = score + int(bonus)  # Convert string to int
print(total)  # Output: 150
```
</details>

---

## Key Takeaways

✅ **Every value has a type** - int, float, str are the basics  
✅ **Use `type()` to check types** - Essential for debugging  
✅ **Variables can change types** - Python is flexible  
✅ **F-strings handle formatting** - Use `f"text {variable}"` for clean output  
✅ **Escape sequences work in strings** - `\"`, `\n`, `\t`, etc.  
✅ **Types must be compatible** - Convert when needed with `str()`, `int()`, `float()`  
✅ **Spacing matters in f-strings** - Spaces are preserved exactly as written

**Remember:** Understanding types prevents many common errors. When Python gives you a `TypeError`, check if you're mixing incompatible types.

---

**Last Updated:** October 25, 2025