# PY101 - Python Fundamentals Reference

**Course:** PY101 - Introduction to Python  
**Purpose:** Comprehensive reference of all concepts, vocabulary, and syntax learned throughout the course

**Last Updated:** October 30, 2025

---

## How to Use This Document

This is your living reference guide for PY101. As you progress through each week:

1. **Review** concepts you've learned
2. **Reference** syntax when writing code
3. **Add** new concepts as you learn them
4. **Practice** with the examples provided

Each section includes:
- Clear definition
- Syntax examples
- Common use cases
- Related concepts

---

## Table of Contents

- [Week 1: Python Basics](#week-1-python-basics)
- [Week 2: Control Flow](#week-2-control-flow)
- [Quick Reference Tables](#quick-reference-tables)

---

## Week 1: Python Basics

### Printing Output

**What it does:** Displays text or values to the screen.

**Syntax:**
```python
print("Hello, World!")
print(variable_name)
print(f"Value: {variable}")  # f-string formatting
```

**Common Uses:**
- Displaying messages to users
- Showing results of calculations
- Debugging (seeing what values variables have)

**Related Concepts:** f-strings, escape sequences

---

### Comments

**What it does:** Adds notes in code that Python ignores.

**Syntax:**
```python
# This is a single-line comment

# This is a multi-line comment
# that spans multiple lines
# using multiple # symbols
```

**Common Uses:**
- Explaining what code does
- Temporarily disabling code
- Adding TODOs or notes for later

**Best Practice:** Write comments that explain WHY, not WHAT the code does.

---

### Variables

**What it does:** Stores a value with a name you can reference later.

**Syntax:**
```python
variable_name = value
age = 25
name = "Marco"
price = 19.99
```

**Rules:**
- Must start with letter or underscore
- Can contain letters, numbers, underscores
- Cannot contain spaces
- Case-sensitive (`age` and `Age` are different)

**Common Uses:**
- Storing user input
- Saving calculation results
- Keeping track of values that change

**Related Concepts:** data types, assignment operator

---

### Data Types

**What it does:** Defines what kind of value a variable holds.

#### Integer (int)
Whole numbers (positive, negative, or zero).

```python
age = 25
score = -10
zero = 0
```

#### Float
Numbers with decimal points.

```python
price = 19.99
temperature = -5.5
pi = 3.14159
```

#### String (str)
Text, enclosed in quotes (single or double).

```python
name = "Marco"
message = 'Hello, World!'
empty = ""
```

#### Boolean (bool)
True or False values.

```python
is_student = True
game_over = False
```

**Check Type:**
```python
type(variable)  # Returns the data type
```

**Related Concepts:** type conversion, operators

---

### Type Conversion

**What it does:** Changes a value from one data type to another.

**Syntax:**
```python
int(value)    # Convert to integer
float(value)  # Convert to float
str(value)    # Convert to string
```

**Examples:**
```python
# String to integer
age = int("25")  # age = 25

# Integer to string
score_text = str(100)  # score_text = "100"

# String to float
price = float("19.99")  # price = 19.99
```

**Common Uses:**
- Converting user input (always strings) to numbers
- Formatting numbers as text for display

**Related Concepts:** input(), data types

---

### F-Strings (Formatted Strings)

**What it does:** Embeds variables and expressions directly into strings.

**Syntax:**
```python
f"text {variable} more text"
```

**Examples:**
```python
name = "Marco"
age = 25
print(f"Hello, {name}! You are {age} years old.")
# Output: Hello, Marco! You are 25 years old.

# With expressions
price = 19.99
print(f"Total: ${price * 2}")
# Output: Total: $39.98

# Formatting numbers
pi = 3.14159
print(f"Pi: {pi:.2f}")  # Two decimal places
# Output: Pi: 3.14
```

**Common Uses:**
- Creating readable output messages
- Combining text and variables
- Formatting numbers for display

**Related Concepts:** print(), string operations

---

### Escape Sequences

**What it does:** Inserts special characters in strings.

**Common Sequences:**
```python
\n  # New line
\t  # Tab
\"  # Double quote
\'  # Single quote
\\  # Backslash
```

**Examples:**
```python
print("Line 1\nLine 2")
# Output:
# Line 1
# Line 2

print("Name:\tMarco")
# Output: Name:    Marco

print("He said \"Hello\"")
# Output: He said "Hello"
```

**Related Concepts:** strings, print()

---

### Operators

#### Arithmetic Operators

**What they do:** Perform mathematical operations.

```python
+   # Addition: 5 + 3 = 8
-   # Subtraction: 5 - 3 = 2
*   # Multiplication: 5 * 3 = 15
/   # Division: 10 / 3 = 3.333...
//  # Floor division: 10 // 3 = 3
%   # Modulo (remainder): 10 % 3 = 1
**  # Exponent: 2 ** 3 = 8
```

**Examples:**
```python
total = 10 + 5  # 15
half = 10 / 2   # 5.0
quotient = 10 // 3  # 3
remainder = 10 % 3  # 1
squared = 5 ** 2  # 25
```

#### Assignment Operators

**What they do:** Assign and modify variable values.

```python
=    # Assign: x = 5
+=   # Add and assign: x += 3 (same as x = x + 3)
-=   # Subtract and assign: x -= 3
*=   # Multiply and assign: x *= 3
/=   # Divide and assign: x /= 3
//=  # Floor divide and assign: x //= 3
%=   # Modulo and assign: x %= 3
```

**Examples:**
```python
score = 10
score += 5  # score is now 15
score -= 3  # score is now 12
score *= 2  # score is now 24
```

#### Comparison Operators

**What they do:** Compare values, return True or False.

```python
==   # Equal to: 5 == 5 → True
!=   # Not equal to: 5 != 3 → True
>    # Greater than: 5 > 3 → True
<    # Less than: 3 < 5 → True
>=   # Greater than or equal: 5 >= 5 → True
<=   # Less than or equal: 3 <= 5 → True
```

**Examples:**
```python
age = 18
is_adult = age >= 18  # True
is_teen = age < 18    # False
```

**Related Concepts:** if statements, booleans

---

### Getting User Input

**What it does:** Asks the user to type something and returns it as a string.

**Syntax:**
```python
variable = input("prompt message")
```

**Examples:**
```python
name = input("Enter your name: ")
# User types: Marco
# name = "Marco"

age = int(input("Enter your age: "))
# User types: 25
# age = 25 (converted to integer)
```

**Important:** `input()` ALWAYS returns a string, even if user types numbers.

**Common Pattern:**
```python
# Get number from user
age_str = input("Enter age: ")
age = int(age_str)

# Or in one line:
age = int(input("Enter age: "))
```

**Related Concepts:** type conversion, strings

---

### String Operations

#### Concatenation

**What it does:** Combines strings together.

```python
first = "Hello"
last = "World"
combined = first + " " + last  # "Hello World"
```

#### Repetition

**What it does:** Repeats a string multiple times.

```python
line = "=" * 10  # "=========="
```

#### String Methods

**What they do:** Built-in functions that operate on strings.

```python
text = "Hello World"

text.lower()      # "hello world"
text.upper()      # "HELLO WORLD"
text.strip()      # Removes whitespace from ends
text.isdigit()    # Checks if all characters are digits
text.startswith("Hello")  # True
text.endswith("World")    # True
len(text)         # 11 (length of string)
```

**Examples:**
```python
# Case-insensitive comparison
user_input = "YES"
if user_input.lower() == "yes":
    print("User said yes")

# Validation
score = input("Enter score: ")
if score.isdigit():
    score_num = int(score)
```

**Related Concepts:** strings, validation

---

## Week 2: Control Flow

### If Statements

**What it does:** Executes code only if a condition is True.

**Syntax:**
```python
if condition:
    # Code runs if condition is True
    action()
```

**Examples:**
```python
age = 18
if age >= 18:
    print("You are an adult")

score = 85
if score >= 90:
    print("A grade")
```

**Key Rules:**
- Condition must evaluate to True or False
- Colon `:` required after condition
- Code block must be indented (4 spaces)

**Related Concepts:** comparison operators, booleans, indentation

---

### If-Else Statements

**What it does:** Executes one block if condition is True, another if False.

**Syntax:**
```python
if condition:
    # Runs if True
    action1()
else:
    # Runs if False
    action2()
```

**Examples:**
```python
temperature = 65
if temperature < 60:
    print("Wear a jacket")
else:
    print("T-shirt is fine")

# Only ONE block executes, never both
```

**Related Concepts:** if statements, decision making

---

### Elif Statements

**What it does:** Checks multiple conditions in sequence.

**Syntax:**
```python
if condition1:
    # Runs if condition1 is True
    action1()
elif condition2:
    # Runs if condition1 is False and condition2 is True
    action2()
elif condition3:
    # Runs if previous conditions False and condition3 is True
    action3()
else:
    # Runs if all conditions are False
    action4()
```

**Examples:**
```python
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"Grade: {grade}")  # Grade: B
```

**Key Points:**
- Checks conditions top to bottom
- Stops at first True condition
- Only one block executes
- `else` is optional

**Related Concepts:** if-else, comparison operators

---

### Logical Operators

**What they do:** Combine or modify boolean expressions.

#### and Operator

**What it does:** True only if BOTH conditions are True.

```python
age = 25
has_license = True

if age >= 18 and has_license:
    print("Can drive")
```

**Truth Table:**
```
True and True → True
True and False → False
False and True → False
False and False → False
```

#### or Operator

**What it does:** True if AT LEAST ONE condition is True.

```python
is_weekend = True
is_holiday = False

if is_weekend or is_holiday:
    print("No work today!")
```

**Truth Table:**
```
True or True → True
True or False → True
False or True → True
False or False → False
```

#### not Operator

**What it does:** Reverses the boolean value.

```python
game_over = False

if not game_over:
    print("Keep playing")  # This runs
```

**Truth Table:**
```
not True → False
not False → True
```

**Examples:**
```python
# Combining operators
age = 25
is_student = True
has_id = True

if (age >= 18 and has_id) or is_student:
    print("Discount applied")

# Using not
password = ""
if not password:
    print("Password cannot be empty")
```

**Related Concepts:** if statements, booleans, comparisons

---

### String Membership (in Operator)

**What it does:** Checks if a substring exists within a string.

**Syntax:**
```python
substring in string  # Returns True or False
```

**Examples:**
```python
text = "Hello World"

if "Hello" in text:
    print("Found it")  # This runs

if "Goodbye" in text:
    print("Found it")  # This doesn't run

# Case-sensitive
if "hello" in text:
    print("Found it")  # Doesn't run (lowercase vs uppercase)

# With user input
response = input("Continue? (yes/no): ")
if "yes" in response.lower():
    print("Continuing...")
```

**Common Uses:**
- Checking for keywords in text
- Validating user input
- Searching within strings

**Opposite:**
```python
if "error" not in message:
    print("No errors")
```

**Related Concepts:** strings, if statements, validation

---

### For Loops

**What it does:** Repeats code for each item in a sequence.

**Syntax:**
```python
for variable in sequence:
    # Code repeats for each item
    action(variable)
```

**Examples:**

**Iterating over a list:**
```python
names = ["Alice", "Bob", "Charlie"]
for name in names:
    print(f"Hello, {name}")
# Output:
# Hello, Alice
# Hello, Bob
# Hello, Charlie
```

**Iterating over a string:**
```python
for letter in "Python":
    print(letter)
# Output: P y t h o n (each on new line)
```

**With range():**
```python
for i in range(5):
    print(i)
# Output: 0 1 2 3 4
```

**Related Concepts:** range(), lists, iteration

---

### Range Function

**What it does:** Generates a sequence of numbers for loops.

**Syntax:**

**One parameter (stop):**
```python
range(stop)  # 0 to stop-1
```

**Two parameters (start, stop):**
```python
range(start, stop)  # start to stop-1
```

**Three parameters (start, stop, step):**
```python
range(start, stop, step)  # start to stop-1, incrementing by step
```

**Examples:**

**Basic counting:**
```python
for i in range(5):
    print(i)
# Output: 0 1 2 3 4
```

**Custom start:**
```python
for i in range(3, 7):
    print(i)
# Output: 3 4 5 6
```

**With step:**
```python
# Even numbers
for i in range(0, 11, 2):
    print(i)
# Output: 0 2 4 6 8 10

# Odd numbers
for i in range(1, 10, 2):
    print(i)
# Output: 1 3 5 7 9

# Countdown
for i in range(10, 0, -1):
    print(i)
# Output: 10 9 8 7 6 5 4 3 2 1
```

**Important Rules:**
- Stop value is ALWAYS exclusive (not included)
- Start defaults to 0
- Step defaults to 1
- Step cannot be 0
- For countdown, step must be negative

**Related Concepts:** for loops, iteration

---

### While Loops

**What it does:** Repeats code as long as a condition is True.

**Syntax:**
```python
while condition:
    # Code repeats while condition is True
    action()
```

**Examples:**

**Basic counting:**
```python
count = 0
while count < 5:
    print(count)
    count += 1
# Output: 0 1 2 3 4
```

**User input validation:**
```python
password = ""
while password != "secret":
    password = input("Enter password: ")
print("Access granted!")
```

**Game loop:**
```python
game_running = True
while game_running:
    action = input("What do you do? ")
    if action == "quit":
        game_running = False
```

**Four Parts of a While Loop:**
1. **Initialization:** Set variable before loop
2. **Condition:** Check at start of each iteration
3. **Body:** Code that repeats
4. **Update:** Change variable to eventually end loop

**Example with all four parts:**
```python
# 1. Initialization
n = 0

# 2. Condition
while n < 3:
    # 3. Body
    print(n)
    
    # 4. Update
    n += 1
```

**Infinite Loop Warning:**
```python
# BAD: Missing update - runs forever!
n = 0
while n < 3:
    print(n)
    # Forgot n += 1
```

**Related Concepts:** for loops, break, continue, conditions

---

### Break Statement

**What it does:** Immediately exits the current loop.

**Syntax:**
```python
break
```

**Examples:**

**Exit loop when condition met:**
```python
for i in range(10):
    if i == 5:
        break
    print(i)
# Output: 0 1 2 3 4 (stops at 5)
```

**Search pattern:**
```python
names = ["Alice", "Bob", "Charlie"]
target = "Bob"

for name in names:
    if name == target:
        print(f"Found {target}!")
        break
# Stops searching after finding Bob
```

**Infinite loop with exit:**
```python
while True:
    response = input("Continue? (yes/no): ")
    if response.lower() == "no":
        break
    print("Continuing...")
```

**Important:** 
- Only breaks out of innermost loop (if nested)
- Often used with `if` statement
- Execution continues after the loop

**Related Concepts:** while loops, for loops, continue

---

### Continue Statement

**What it does:** Skips rest of current iteration, moves to next one.

**Syntax:**
```python
continue
```

**Examples:**

**Skip even numbers:**
```python
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)
# Output: 1 3 5 7 9 (skips even numbers)
```

**Filter out invalid data:**
```python
numbers = [5, -2, 10, -7, 15]

for num in numbers:
    if num < 0:
        continue  # Skip negative numbers
    print(f"Processing: {num}")
# Output:
# Processing: 5
# Processing: 10
# Processing: 15
```

**With while loop:**
```python
n = 0
while n < 5:
    n += 1
    if n == 3:
        continue  # Skip when n is 3
    print(n)
# Output: 1 2 4 5 (skips 3)
```

**Important:**
- Loop continues running (unlike break)
- Skips code after continue in current iteration
- Be careful with while loops (make sure variable still updates)

**Related Concepts:** for loops, while loops, break

---

### Counters

**What it does:** Tracks how many times something happens.

**Pattern:**
```python
# 1. Initialize before loop
count = 0

# 2. Loop through items
for item in collection:
    # 3. Check condition
    if condition:
        # 4. Increment counter
        count += 1

# 5. Use count after loop
print(count)
```

**Examples:**

**Count even numbers:**
```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8]
even_count = 0

for num in numbers:
    if num % 2 == 0:
        even_count += 1

print(f"Even numbers: {even_count}")
# Output: Even numbers: 4
```

**Count vowels:**
```python
text = "Hello World"
vowel_count = 0

for letter in text:
    if letter.lower() in "aeiou":
        vowel_count += 1

print(f"Vowels: {vowel_count}")
# Output: Vowels: 3
```

**Common Use Cases:**
- Counting items that meet criteria
- Tracking frequency
- Progress indicators
- Game scores

**Critical Rule:** ALWAYS initialize counter BEFORE the loop, never inside.

**Related Concepts:** loops, accumulator pattern, totals

---

### Totals (Accumulators)

**What it does:** Builds up a sum by adding values incrementally.

**Pattern:**
```python
# 1. Initialize before loop
total = 0

# 2. Loop through items
for item in collection:
    # 3. Add to total
    total += value

# 4. Use total after loop
print(total)
```

**Examples:**

**Sum of numbers:**
```python
numbers = [10, 20, 30, 40]
total = 0

for num in numbers:
    total += num

print(f"Sum: {total}")
# Output: Sum: 100
```

**Sum of even numbers only:**
```python
numbers = [1, 2, 3, 4, 5, 6]
total = 0

for num in numbers:
    if num % 2 == 0:
        total += num

print(f"Sum of evens: {total}")
# Output: Sum of evens: 12
```

**Running total:**
```python
prices = [10.99, 5.50, 3.25]
total = 0

for price in prices:
    total += price
    print(f"Current total: ${total:.2f}")
# Output:
# Current total: $10.99
# Current total: $16.49
# Current total: $19.74
```

**Combining Counter and Total:**
```python
numbers = [5, 10, 15, 20, 25]
count = 0
total = 0

for num in numbers:
    count += 1
    total += num

average = total / count
print(f"Average: {average}")
# Output: Average: 15.0
```

**Critical Rule:** ALWAYS initialize accumulator BEFORE the loop, never inside.

**Related Concepts:** loops, counters, average calculations

---

### Functions (Basic)

**What it does:** Groups code into reusable blocks with a name.

**Syntax:**
```python
def function_name(parameters):
    """Docstring explaining what function does."""
    # Code here
    return result  # Optional
```

**Examples:**

**Function without parameters:**
```python
def greet():
    """Print a greeting message."""
    print("Hello, World!")

# Call the function
greet()
# Output: Hello, World!
```

**Function with parameters:**
```python
def greet_person(name):
    """Print a personalized greeting."""
    print(f"Hello, {name}!")

greet_person("Marco")
# Output: Hello, Marco!
```

**Function with return value:**
```python
def add(a, b):
    """Add two numbers and return the result."""
    return a + b

result = add(5, 3)
print(result)
# Output: 8
```

**Function with multiple parameters:**
```python
def display_score(team, score):
    """Display team name and their score."""
    print(f"{team}: {score}")

display_score("Tigers", 15)
# Output: Tigers: 15
```

**Why Use Functions:**
- Organize code into logical pieces
- Reuse code without copying
- Make code easier to read and maintain
- Break complex problems into smaller parts

**Related Concepts:** parameters, return values, docstrings

---

## Quick Reference Tables

### Operator Precedence (Order of Operations)

**From highest to lowest priority:**

1. `()`  - Parentheses
2. `**`  - Exponent
3. `*`, `/`, `//`, `%`  - Multiplication, Division, Floor Division, Modulo
4. `+`, `-`  - Addition, Subtraction

**Example:**
```python
result = 2 + 3 * 4  # 14 (not 20)
result = (2 + 3) * 4  # 20 (parentheses first)
```

---

### Comparison Operators Quick Reference

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `==` | Equal to | `5 == 5` | `True` |
| `!=` | Not equal to | `5 != 3` | `True` |
| `>` | Greater than | `5 > 3` | `True` |
| `<` | Less than | `3 < 5` | `True` |
| `>=` | Greater than or equal | `5 >= 5` | `True` |
| `<=` | Less than or equal | `3 <= 5` | `True` |

---

### Logical Operators Truth Tables

**AND:**
| A | B | A and B |
|---|---|---------|
| True | True | True |
| True | False | False |
| False | True | False |
| False | False | False |

**OR:**
| A | B | A or B |
|---|---|--------|
| True | True | True |
| True | False | True |
| False | True | True |
| False | False | False |

**NOT:**
| A | not A |
|---|-------|
| True | False |
| False | True |

---

### Common String Methods

| Method | What It Does | Example | Result |
|--------|--------------|---------|--------|
| `.lower()` | Convert to lowercase | `"HELLO".lower()` | `"hello"` |
| `.upper()` | Convert to uppercase | `"hello".upper()` | `"HELLO"` |
| `.strip()` | Remove whitespace | `"  hi  ".strip()` | `"hi"` |
| `.isdigit()` | Check if all digits | `"123".isdigit()` | `True` |
| `.startswith()` | Check if starts with | `"hello".startswith("he")` | `True` |
| `.endswith()` | Check if ends with | `"hello".endswith("lo")` | `True` |
| `len()` | Get length | `len("hello")` | `5` |

---

### When to Use Each Loop Type

| Loop Type | Use When | Example |
|-----------|----------|---------|
| `for` with `range()` | You know exact number of iterations | `for i in range(10):` |
| `for` with list | Processing each item in collection | `for name in names:` |
| `while` | Continue until condition changes | `while score < 100:` |
| `while True` with `break` | Need explicit exit point | `while True: if done: break` |

---

### Common Validation Patterns

**Check if input is a number:**
```python
user_input = input("Enter number: ")
if user_input.isdigit():
    number = int(user_input)
else:
    print("Invalid number")
```

**Check if input is in range:**
```python
score = int(input("Enter score: "))
if 0 <= score <= 100:
    print("Valid score")
else:
    print("Score must be 0-100")
```

**Check if input is yes/no:**
```python
response = input("Continue? (yes/no): ")
if response.lower() in ["yes", "y"]:
    print("Continuing...")
elif response.lower() in ["no", "n"]:
    print("Stopping...")
else:
    print("Invalid response")
```

**Validate with loop:**
```python
valid_input = False
while not valid_input:
    age = input("Enter age: ")
    if age.isdigit():
        age_num = int(age)
        if age_num > 0:
            valid_input = True
        else:
            print("Age must be positive")
    else:
        print("Please enter a number")
```

---

## Common Patterns

### Average Calculation
```python
numbers = [10, 20, 30, 40, 50]
count = 0
total = 0

for num in numbers:
    count += 1
    total += num

if count > 0:
    average = total / count
    print(f"Average: {average}")
```

### Finding Maximum
```python
numbers = [5, 12, 3, 19, 7]
max_value = numbers[0]

for num in numbers:
    if num > max_value:
        max_value = num

print(f"Maximum: {max_value}")
```

### Input Validation Loop
```python
valid = False
while not valid:
    value = input("Enter value: ")
    if value.isdigit():
        number = int(value)
        valid = True
    else:
        print("Invalid input. Try again.")
```

### Search Pattern
```python
items = ["apple", "banana", "cherry"]
target = "banana"
found = False

for item in items:
    if item == target:
        print(f"Found {target}!")
        found = True
        break

if not found:
    print(f"{target} not found")
```

---

## Debugging Tips

### Common Errors

**NameError:**
```python
# Error: variable not defined
print(name)
# Fix: Define variable first
name = "Marco"
print(name)
```

**TypeError:**
```python
# Error: wrong type
age = "25"
result = age + 5  # Can't add string and int
# Fix: Convert types
age = int("25")
result = age + 5
```

**IndentationError:**
```python
# Error: incorrect indentation
if True:
print("Hello")  # Not indented
# Fix: Add 4 spaces
if True:
    print("Hello")
```

**ValueError:**
```python
# Error: can't convert string to int
age = int("twenty")
# Fix: Validate input first
age_str = input("Enter age: ")
if age_str.isdigit():
    age = int(age_str)
```

---

## Study Strategies

### When Learning New Concepts

1. **Read the definition** - Understand what it does
2. **Study the syntax** - Learn the exact format
3. **Try examples** - Type them out, don't just read
4. **Modify examples** - Change values, see what happens
5. **Create your own** - Apply to a new problem
6. **Explain it** - Teach it to someone (or yourself)

### Before Writing Code

1. **Understand the problem** - What are you trying to do?
2. **Break it down** - What are the steps?
3. **Identify concepts** - Which Python features do you need?
4. **Write pseudocode** - Plan in plain English
5. **Code small pieces** - Test each part before moving on
6. **Test thoroughly** - Try to break your code

### When Stuck

1. **Read error messages** - They tell you exactly what's wrong
2. **Check syntax** - Colons? Indentation? Parentheses?
3. **Print variables** - See what values they actually have
4. **Review examples** - Compare to working code
5. **Take a break** - Fresh eyes see problems faster

---

## Notes Section

*Use this space to add your own notes, examples, and insights as you learn.*

---

**Remember:** This document grows with you. Add to it as you learn new concepts, and refer back to it when you need a quick reminder. The more you use it, the more valuable it becomes!

---

**Last Updated:** October 30, 2025
