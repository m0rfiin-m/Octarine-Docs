# PY101 - Python Fundamentals Reference

**Course:** PY101 - Introduction to Python  
**Purpose:** Comprehensive reference of all concepts, vocabulary, and syntax learned throughout the course

**Last Updated:** November 9, 2025

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
- [Week 3: Advanced Strings, Lists, and Dictionaries](#week-3-advanced-strings-lists-and-dictionaries)
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

## Week 3: Advanced Strings, Lists, and Dictionaries

### String Indexing and Slicing

**What it does:** Accesses individual characters or portions of a string.

**Indexing Syntax:**
```python
text[index]  # Access single character
```

**Examples - Positive Indexing:**
```python
text = "Python"
print(text[0])  # "P" (first character)
print(text[1])  # "y" (second character)
print(text[5])  # "n" (last character)
```

**Examples - Negative Indexing:**
```python
text = "Python"
print(text[-1])  # "n" (last character)
print(text[-2])  # "o" (second to last)
print(text[-6])  # "P" (first character)
```

**Slicing Syntax:**
```python
text[start:stop]       # From start up to (not including) stop
text[start:stop:step]  # With custom step
```

**Slicing Examples:**
```python
text = "Python"

# Basic slicing
print(text[0:3])   # "Pyt" (indices 0, 1, 2)
print(text[2:5])   # "tho" (indices 2, 3, 4)

# Omitting bounds
print(text[:3])    # "Pyt" (from beginning to index 3)
print(text[3:])    # "hon" (from index 3 to end)
print(text[:])     # "Python" (entire string)

# With step
print(text[::2])   # "Pto" (every other character)
print(text[1::2])  # "yhn" (every other, starting at index 1)
print(text[::-1])  # "nohtyP" (reverse string)

# Negative indices in slicing
print(text[-4:-1]) # "tho" (from -4 up to -1)
```

**Key Rules:**
- Indexing starts at 0 (zero-based)
- Stop index is EXCLUSIVE (not included in result)
- Negative indices count from end (-1 is last)
- Slicing never raises IndexError (returns empty string if out of range)

**Common Uses:**
- Extract portions of strings
- Reverse strings with `[::-1]`
- Get first/last n characters
- Skip characters with step parameter

**Related Concepts:** strings, lists (same indexing/slicing rules)

---

### Common String Methods

**What they do:** Built-in functions that process and transform strings.

#### Cleaning Methods

**strip() - Remove whitespace from both ends:**
```python
text = "  Hello  "
print(text.strip())  # "Hello"

# Remove specific characters
text = "!!!Hello!!!"
print(text.strip("!"))  # "Hello"
```

**Common Pattern - Method Chaining:**
```python
user_input = "  MARCO  "
clean = user_input.strip().lower()  # "marco"
```

#### Case Conversion

```python
text = "hello world"

print(text.lower())       # "hello world"
print(text.upper())       # "HELLO WORLD"
print(text.title())       # "Hello World"
print(text.capitalize())  # "Hello world" (only first letter)
```

#### Searching

**in keyword - Check if substring exists:**
```python
text = "Hello World"
print("Hello" in text)    # True
print("Goodbye" in text)  # False
```

**find() - Get position of substring:**
```python
text = "Hello World"
print(text.find("World"))   # 6 (starting index)
print(text.find("Goodbye")) # -1 (not found)
```

**When to use:**
- Use `in` when you only need to know if substring exists
- Use `find()` when you need the position

#### Replacing

**replace() - Replace all occurrences:**
```python
text = "Hello World"
print(text.replace("World", "Python"))  # "Hello Python"
print(text.replace("l", "L"))           # "HeLLo WorLd"

# Delete by replacing with empty string
text = "Hello!!!"
print(text.replace("!", ""))  # "Hello"
```

#### Method Chaining

**Combining multiple methods:**
```python
text = "  HELLO WORLD!!!  "
result = text.strip().lower().replace("!", "")
print(result)  # "hello world"
```

**Important:** 
- String methods return NEW strings (don't modify original)
- Must assign result to use it: `text = text.strip()`
- Order matters in chains: usually `.strip()` first

**Common Uses:**
- Cleaning user input
- Standardizing text for comparison
- Formatting output
- Data preprocessing

**Related Concepts:** strings, splitting and joining

---

### Splitting and Joining

**What they do:** Convert between strings and lists of strings.

#### Splitting Strings

**split() - Divide string into list:**
```python
# Split on whitespace (default)
text = "apple banana cherry"
words = text.split()
print(words)  # ['apple', 'banana', 'cherry']

# Split on specific separator
text = "apple,banana,cherry"
words = text.split(",")
print(words)  # ['apple', 'banana', 'cherry']
```

**Important Behaviors:**
```python
# Default split() removes ALL whitespace
text = "apple    banana"  # Multiple spaces
words = text.split()
print(words)  # ['apple', 'banana'] (no empty strings)

# Specific separator keeps empty strings
text = "a,,b"
parts = text.split(",")
print(parts)  # ['a', '', 'b'] (empty string in middle)
```

**Common Pattern - Split and Clean:**
```python
text = "apple, banana, cherry"
# Split, then strip each piece
items = [item.strip() for item in text.split(",")]
print(items)  # ['apple', 'banana', 'cherry']
```

#### Joining Strings

**join() - Combine list into string:**
```python
words = ["apple", "banana", "cherry"]

# Join with space
result = " ".join(words)
print(result)  # "apple banana cherry"

# Join with comma and space
result = ", ".join(words)
print(result)  # "apple, banana, cherry"

# Join with hyphen
result = "-".join(words)
print(result)  # "apple-banana-cherry"

# Join with nothing (concatenate)
letters = ["H", "e", "l", "l", "o"]
result = "".join(letters)
print(result)  # "Hello"
```

**Important:** Separator goes BEFORE `.join()`, not inside.

**Common Workflow:**
```python
# Split → Clean → Filter → Join
text = "apple, , banana, cherry, "
parts = text.split(",")                      # Split on comma
clean = [item.strip() for item in parts]     # Clean each piece
filtered = [item for item in clean if item]  # Remove empties
result = "; ".join(filtered)                 # Join with semicolon
print(result)  # "apple; banana; cherry"
```

**Common Uses:**
- Parsing CSV or delimited data
- Processing user input with multiple values
- Building formatted output from lists
- Converting between string and list formats

**Related Concepts:** strings, lists, string methods

---

### Creating Lists

**What it does:** Creates ordered collections of items.

#### Manual Creation

**Syntax:**
```python
list_name = [item1, item2, item3]
```

**Examples:**
```python
# List of numbers
numbers = [1, 2, 3, 4, 5]

# List of strings
names = ["Alice", "Bob", "Charlie"]

# Mixed types (not recommended)
mixed = [1, "two", 3.0, True]

# Empty list
empty = []
```

**Best Practice:** Keep lists homogeneous (same type of items).

#### Using range()

**Create lists from range:**
```python
# Convert range to list
numbers = list(range(1, 6))
print(numbers)  # [1, 2, 3, 4, 5]

# With step
evens = list(range(2, 11, 2))
print(evens)  # [2, 4, 6, 8, 10]

# Countdown
countdown = list(range(10, 0, -1))
print(countdown)  # [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
```

#### List Properties

```python
numbers = [10, 20, 30, 40, 50]

# Length
print(len(numbers))  # 5

# Access items by index
print(numbers[0])    # 10 (first item)
print(numbers[-1])   # 50 (last item)

# Modify items
numbers[0] = 99
print(numbers)  # [99, 20, 30, 40, 50]
```

**Key Differences from Strings:**
- Lists are MUTABLE (can change after creation)
- Strings are IMMUTABLE (cannot change after creation)

**Common Uses:**
- Storing collections of related items
- Building lists dynamically with loops
- Processing multiple values together

**Related Concepts:** range(), list methods, iteration

---

### List Indexing and Slicing

**What it does:** Accesses and modifies list elements.

#### Indexing

**Accessing values:**
```python
fruits = ["apple", "banana", "cherry", "date"]

# Positive indexing (from start)
print(fruits[0])   # "apple"
print(fruits[2])   # "cherry"

# Negative indexing (from end)
print(fruits[-1])  # "date" (last)
print(fruits[-2])  # "cherry" (second to last)
```

**Modifying values:**
```python
fruits = ["apple", "banana", "cherry"]

# Change single item
fruits[1] = "blueberry"
print(fruits)  # ['apple', 'blueberry', 'cherry']

# Change using negative index
fruits[-1] = "dragonfruit"
print(fruits)  # ['apple', 'blueberry', 'dragonfruit']
```

#### Slicing

**Extracting sublists:**
```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Basic slicing
print(numbers[2:5])    # [2, 3, 4]
print(numbers[:3])     # [0, 1, 2] (first 3)
print(numbers[7:])     # [7, 8, 9] (from index 7 to end)
print(numbers[:])      # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] (entire list)

# With step
print(numbers[::2])    # [0, 2, 4, 6, 8] (every other)
print(numbers[1::2])   # [1, 3, 5, 7, 9] (every other, start at 1)
print(numbers[::-1])   # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0] (reverse)
```

#### References vs Copies

**Assignment creates reference (alias):**
```python
original = [1, 2, 3]
reference = original  # Points to SAME list

reference[0] = 99
print(original)  # [99, 2, 3] - ORIGINAL CHANGED!
print(reference is original)  # True (same object)
```

**Slicing creates copy:**
```python
original = [1, 2, 3]
copy = original[:]  # Creates NEW list

copy[0] = 99
print(original)  # [1, 2, 3] - unchanged
print(copy)      # [99, 2, 3]
print(copy is original)  # False (different objects)
```

**Other ways to copy:**
```python
original = [1, 2, 3]

copy1 = original.copy()    # Using .copy() method
copy2 = list(original)     # Using list() constructor
copy3 = original[:]        # Using slice
```

**Identity vs Equality:**
```python
list1 = [1, 2, 3]
list2 = [1, 2, 3]
list3 = list1

print(list1 == list2)  # True (same values)
print(list1 is list2)  # False (different objects)
print(list1 is list3)  # True (same object)
```

**Common Uses:**
- Extract portions of lists
- Create independent copies
- Reverse lists
- Get first/last n items

**Related Concepts:** strings (same slicing syntax), list methods, mutability

---

### List Iteration

**What it does:** Loops through list items.

#### Value-Based Loops

**When to use:** You only need the values, not the positions.

```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)
# Output:
# apple
# banana
# cherry
```

**Processing values:**
```python
numbers = [1, 2, 3, 4, 5]
total = 0

for num in numbers:
    total += num

print(f"Sum: {total}")  # Sum: 15
```

#### Index-Based Loops

**When to use:** You need positions or want to modify the list.

```python
fruits = ["apple", "banana", "cherry"]

for i in range(len(fruits)):
    print(f"Index {i}: {fruits[i]}")
# Output:
# Index 0: apple
# Index 1: banana
# Index 2: cherry
```

**Modifying list during iteration:**
```python
numbers = [1, 2, 3, 4, 5]

for i in range(len(numbers)):
    numbers[i] = numbers[i] * 2

print(numbers)  # [2, 4, 6, 8, 10]
```

#### Guard Patterns

**Selective processing based on position:**
```python
scores = [85, 92, 78, 95, 88]

for i in range(len(scores)):
    if i == 0:
        print(f"First score: {scores[i]}")
    elif i == len(scores) - 1:
        print(f"Last score: {scores[i]}")
    else:
        print(f"Score: {scores[i]}")
```

#### Membership Testing

**Check if item exists before processing:**
```python
fruits = ["apple", "banana", "cherry"]

# Check membership
if "banana" in fruits:
    print("We have bananas!")

# Check absence
if "grape" not in fruits:
    print("No grapes available")
```

#### Accumulation Patterns

**Building values during iteration:**
```python
numbers = [10, 20, 30, 40, 50]

# Sum
total = 0
for num in numbers:
    total += num
print(f"Total: {total}")  # Total: 150

# Count matching items
count = 0
for num in numbers:
    if num > 25:
        count += 1
print(f"Count: {count}")  # Count: 3
```

**Critical Rule:** Never modify a list while iterating over it directly. Build a new list instead.

```python
# BAD - Don't do this
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num % 2 == 0:
        numbers.remove(num)  # Can cause unexpected behavior!

# GOOD - Build new list
numbers = [1, 2, 3, 4, 5]
odds = []
for num in numbers:
    if num % 2 != 0:
        odds.append(num)
```

**Common Uses:**
- Processing each item in collection
- Accumulating totals or counts
- Searching for specific items
- Building new lists from existing ones

**Related Concepts:** for loops, range(), list methods

---

### Common List Methods

**What they do:** Built-in functions that modify or query lists.

#### Adding Items

**append() - Add to end (most common):**
```python
fruits = ["apple", "banana"]
fruits.append("cherry")
print(fruits)  # ['apple', 'banana', 'cherry']
```

**insert() - Add at specific position:**
```python
fruits = ["apple", "cherry"]
fruits.insert(1, "banana")  # Insert at index 1
print(fruits)  # ['apple', 'banana', 'cherry']
```

**extend() - Add all items from another iterable:**
```python
fruits = ["apple", "banana"]
more_fruits = ["cherry", "date"]

fruits.extend(more_fruits)
print(fruits)  # ['apple', 'banana', 'cherry', 'date']
```

**append() vs extend():**
```python
# append adds the entire object
fruits = ["apple"]
fruits.append(["banana", "cherry"])
print(fruits)  # ['apple', ['banana', 'cherry']] - nested!

# extend adds each item individually
fruits = ["apple"]
fruits.extend(["banana", "cherry"])
print(fruits)  # ['apple', 'banana', 'cherry'] - flattened!
```

#### Removing Items

**remove() - Remove first matching value:**
```python
fruits = ["apple", "banana", "cherry", "banana"]
fruits.remove("banana")  # Removes first "banana"
print(fruits)  # ['apple', 'cherry', 'banana']

# Always check first to avoid ValueError
if "grape" in fruits:
    fruits.remove("grape")
else:
    print("Grape not found")
```

**pop() - Remove and return item:**
```python
fruits = ["apple", "banana", "cherry"]

# Remove last item
last = fruits.pop()
print(last)    # "cherry"
print(fruits)  # ['apple', 'banana']

# Remove at specific index
first = fruits.pop(0)
print(first)   # "apple"
print(fruits)  # ['banana']
```

**Method Comparison:**

| Method | Finds By | Returns | Raises Error? |
|--------|----------|---------|---------------|
| `.remove(value)` | Value | None | Yes (ValueError if not found) |
| `.pop(index)` | Position | Removed item | Yes (IndexError if invalid index) |
| `.pop()` | Last position | Removed item | Yes (IndexError if empty) |

**Safe removal pattern:**
```python
fruits = ["apple", "banana", "cherry"]

# Safe remove by value
item = "banana"
if item in fruits:
    fruits.remove(item)
    print(f"Removed {item}")
else:
    print(f"{item} not found")

# Safe pop by index
if len(fruits) > 0:
    last = fruits.pop()
    print(f"Removed {last}")
```

**Common Uses:**
- Building lists dynamically
- Adding user input to collections
- Removing unwanted items
- Processing queues or stacks

**Related Concepts:** lists, iteration, list building patterns

---

### Sorting Lists

**What it does:** Arranges list items in order.

#### sorted() Function

**Returns NEW sorted list (original unchanged):**
```python
numbers = [3, 1, 4, 1, 5, 9, 2]
sorted_numbers = sorted(numbers)

print(sorted_numbers)  # [1, 1, 2, 3, 4, 5, 9]
print(numbers)         # [3, 1, 4, 1, 5, 9, 2] - unchanged
```

**Syntax:**
```python
sorted(list, reverse=False, key=None)
```

#### .sort() Method

**Modifies list IN PLACE (returns None):**
```python
numbers = [3, 1, 4, 1, 5, 9, 2]
numbers.sort()

print(numbers)  # [1, 1, 2, 3, 4, 5, 9]
```

**Syntax:**
```python
list.sort(reverse=False, key=None)
```

**Important:** Don't assign the result of `.sort()`!
```python
# WRONG - result will be None
numbers = [3, 1, 2]
numbers = numbers.sort()  # numbers is now None!

# RIGHT - .sort() modifies in place
numbers = [3, 1, 2]
numbers.sort()  # numbers is now [1, 2, 3]
```

#### Reverse Parameter

**Descending order:**
```python
numbers = [3, 1, 4, 1, 5, 9, 2]

# sorted() with reverse
desc = sorted(numbers, reverse=True)
print(desc)  # [9, 5, 4, 3, 2, 1, 1]

# .sort() with reverse
numbers.sort(reverse=True)
print(numbers)  # [9, 5, 4, 3, 2, 1, 1]
```

#### Key Parameter

**Custom sort criterion:**

**Sort by length:**
```python
words = ["apple", "pie", "banana", "cherry"]
sorted_words = sorted(words, key=len)
print(sorted_words)  # ['pie', 'apple', 'banana', 'cherry']
```

**Sort by absolute value:**
```python
numbers = [-5, 2, -10, 3, -1]
sorted_nums = sorted(numbers, key=abs)
print(sorted_nums)  # [-1, 2, 3, -5, -10]
```

**Case-insensitive string sorting:**
```python
names = ["alice", "Bob", "Charlie", "david"]
sorted_names = sorted(names, key=str.lower)
print(sorted_names)  # ['alice', 'Bob', 'Charlie', 'david']
```

**Sort tuples by specific element:**
```python
students = [("Alice", 85), ("Bob", 92), ("Charlie", 78)]

# Sort by second element (score)
by_score = sorted(students, key=lambda x: x[1])
print(by_score)
# [('Charlie', 78), ('Alice', 85), ('Bob', 92)]
```

#### When to Use Each

**Use sorted():**
- When you need both original and sorted versions
- When sorting is temporary for one operation
- When working with immutable data

**Use .sort():**
- When you only need the sorted version
- When memory efficiency matters
- When you won't use the original order again

**Stable Sorting:**
Equal items maintain their original relative order.

```python
# Two-level sort: sort by secondary first, then primary
students = [("Alice", 85), ("Bob", 85), ("Charlie", 90)]
students.sort(key=lambda x: x[0])  # Sort by name first
students.sort(key=lambda x: x[1], reverse=True)  # Then by score
# Students with same score keep name order
```

**Common Uses:**
- Organizing data alphabetically or numerically
- Finding min/max values (sort then access first/last)
- Preparing data for display
- Ranking items

**Related Concepts:** lists, lambda functions, comparison operators

---

### Dictionary Basics

**What it does:** Stores data as key-value pairs for fast lookup.

#### Creating Dictionaries

**Syntax:**
```python
dict_name = {
    "key1": value1,
    "key2": value2,
    "key3": value3
}
```

**Examples:**
```python
# Simple dictionary
person = {
    "name": "Marco",
    "age": 25,
    "city": "Phoenix"
}

# Different value types
student = {
    "name": "Alice",
    "grades": [85, 90, 92],
    "is_active": True
}

# Empty dictionary
empty_dict = {}
```

#### Accessing Values

**Direct access with []:**
```python
person = {"name": "Marco", "age": 25}

print(person["name"])  # "Marco"
print(person["age"])   # 25

# KeyError if key doesn't exist
print(person["city"])  # KeyError: 'city'
```

**Safe access with .get():**
```python
person = {"name": "Marco", "age": 25}

# Returns None if key missing
print(person.get("city"))  # None

# Returns default value if key missing
print(person.get("city", "Unknown"))  # "Unknown"

# Still works if key exists
print(person.get("name", "Unknown"))  # "Marco"
```

**When to use each:**
- Use `[]` when you're sure the key exists
- Use `.get()` when key might be missing

#### Adding and Updating

**Add new key-value pair:**
```python
person = {"name": "Marco"}
person["age"] = 25
print(person)  # {'name': 'Marco', 'age': 25}
```

**Update existing value:**
```python
person = {"name": "Marco", "age": 25}
person["age"] = 26
print(person)  # {'name': 'Marco', 'age': 26}
```

**Same syntax for both add and update:**
```python
scores = {}
scores["math"] = 85      # Adds
scores["math"] = 90      # Updates
scores["science"] = 88   # Adds
```

#### Key Rules

**Keys must be immutable:**
```python
# Valid keys
valid = {
    "string_key": 1,      # String ✓
    42: "number",         # Number ✓
    (1, 2): "tuple"       # Tuple ✓
}

# Invalid keys
invalid = {
    [1, 2]: "list"        # List ✗ - TypeError!
}
```

**Keys must be unique:**
```python
# Duplicate keys - last one wins
person = {
    "name": "Marco",
    "age": 25,
    "age": 26  # This overwrites the previous "age"
}
print(person)  # {'name': 'Marco', 'age': 26}
```

**Values can be any type:**
```python
data = {
    "number": 42,
    "list": [1, 2, 3],
    "dict": {"nested": "value"},
    "bool": True
}
```

#### Basic Operations

**Length:**
```python
person = {"name": "Marco", "age": 25, "city": "Phoenix"}
print(len(person))  # 3
```

**Get all values:**
```python
scores = {"math": 85, "science": 90, "english": 88}
print(scores.values())  # dict_values([85, 90, 88])

# Calculate average
average = sum(scores.values()) / len(scores)
print(average)  # 87.666...
```

**Check if key exists:**
```python
person = {"name": "Marco", "age": 25}

if "name" in person:
    print(f"Name: {person['name']}")

if "city" not in person:
    print("City not specified")
```

**Common Uses:**
- Storing structured data (like JSON)
- Fast lookups by key
- Counting occurrences
- Mapping relationships

**Related Concepts:** lists, iteration, nested structures

---

### Dictionary Iteration

**What it does:** Loops through dictionary keys, values, or pairs.

#### Loop Through Keys

**Using .keys() method:**
```python
scores = {"math": 85, "science": 90, "english": 88}

for subject in scores.keys():
    print(subject)
# Output:
# math
# science
# english
```

**Shortcut (default behavior):**
```python
scores = {"math": 85, "science": 90, "english": 88}

for subject in scores:  # Same as scores.keys()
    print(subject)
```

#### Loop Through Values

**Using .values() method:**
```python
scores = {"math": 85, "science": 90, "english": 88}

for score in scores.values():
    print(score)
# Output:
# 85
# 90
# 88
```

**Calculations on values:**
```python
scores = {"math": 85, "science": 90, "english": 88}

total = 0
for score in scores.values():
    total += score

average = total / len(scores)
print(f"Average: {average}")  # Average: 87.666...
```

#### Loop Through Key-Value Pairs

**Using .items() method (most common):**
```python
scores = {"math": 85, "science": 90, "english": 88}

for subject, score in scores.items():
    print(f"{subject}: {score}")
# Output:
# math: 85
# science: 90
# english: 88
```

**With conditionals:**
```python
scores = {"math": 85, "science": 90, "english": 88}

for subject, score in scores.items():
    if score >= 90:
        print(f"{subject}: A grade!")
    else:
        print(f"{subject}: {score}")
```

#### When to Use Each Method

| Method | Use When | Example |
|--------|----------|---------|
| `.keys()` | Only need keys | Check if certain keys exist |
| `.values()` | Only need values | Calculate sum/average |
| `.items()` | Need both | Display formatted output |

**Common Patterns:**

**Finding maximum value:**
```python
scores = {"math": 85, "science": 90, "english": 88}

max_score = 0
max_subject = ""

for subject, score in scores.items():
    if score > max_score:
        max_score = score
        max_subject = subject

print(f"Best: {max_subject} ({max_score})")
```

**Counting occurrences:**
```python
votes = ["apple", "banana", "apple", "cherry", "banana", "apple"]
count = {}

for fruit in votes:
    if fruit in count:
        count[fruit] += 1
    else:
        count[fruit] = 1

print(count)  # {'apple': 3, 'banana': 2, 'cherry': 1}
```

**Filtering:**
```python
scores = {"math": 85, "science": 90, "english": 88, "history": 75}

# Build new dict with scores >= 85
high_scores = {}
for subject, score in scores.items():
    if score >= 85:
        high_scores[subject] = score

print(high_scores)  # {'math': 85, 'science': 90, 'english': 88}
```

**Common Uses:**
- Processing all entries in dictionary
- Calculating statistics on values
- Filtering or transforming data
- Building formatted output

**Related Concepts:** dictionaries, for loops, tuples (unpacking in .items())

---

### Copy Semantics

**What it does:** Explains the difference between assigning and copying collections.

#### Assignment Creates Alias

**Lists:**
```python
original = [1, 2, 3]
alias = original  # Points to SAME list

alias[0] = 99
print(original)  # [99, 2, 3] - CHANGED!
print(alias)     # [99, 2, 3]

print(alias is original)  # True (same object)
```

**Dictionaries:**
```python
original = {"name": "Marco", "age": 25}
alias = original  # Points to SAME dict

alias["age"] = 26
print(original)  # {'name': 'Marco', 'age': 26} - CHANGED!
print(alias)     # {'name': 'Marco', 'age': 26}

print(alias is original)  # True (same object)
```

#### Creating Independent Copies

**Lists:**
```python
original = [1, 2, 3]

# Method 1: .copy()
copy1 = original.copy()

# Method 2: slice
copy2 = original[:]

# Method 3: list() constructor
copy3 = list(original)

# All are independent
copy1[0] = 99
print(original)  # [1, 2, 3] - unchanged
print(copy1)     # [99, 2, 3]
```

**Dictionaries:**
```python
original = {"name": "Marco", "age": 25}

# Method 1: .copy()
copy1 = original.copy()

# Method 2: dict() constructor
copy2 = dict(original)

# Both are independent
copy1["age"] = 26
print(original)  # {'name': 'Marco', 'age': 25} - unchanged
print(copy1)     # {'name': 'Marco', 'age': 26}
```

#### Identity vs Equality

**== checks values (equality):**
```python
list1 = [1, 2, 3]
list2 = [1, 2, 3]

print(list1 == list2)  # True (same values)
```

**is checks if same object (identity):**
```python
list1 = [1, 2, 3]
list2 = [1, 2, 3]
list3 = list1

print(list1 is list2)  # False (different objects)
print(list1 is list3)  # True (same object)
```

**When it matters:**
```python
# Equality check (usually what you want)
if my_list == [1, 2, 3]:
    print("List contains 1, 2, 3")

# Identity check (less common)
if my_list is original_list:
    print("These are the exact same list object")
```

**Common Uses:**
- Creating independent copies before modifying
- Understanding why changing one variable affects another
- Avoiding unintended side effects in functions
- Deep vs shallow copying (for nested structures)

**Related Concepts:** lists, dictionaries, mutability, nested structures

---

### Nested Structures

**What it does:** Stores collections inside other collections.

#### Accessing Nested Data

**List of lists:**
```python
grid = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Access outer list first, then inner
print(grid[0])     # [1, 2, 3] (first row)
print(grid[0][0])  # 1 (first row, first column)
print(grid[1][2])  # 6 (second row, third column)
print(grid[2][1])  # 8 (third row, second column)
```

**Dictionary of dictionaries:**
```python
users = {
    "user1": {"name": "Alice", "age": 25},
    "user2": {"name": "Bob", "age": 30}
}

# Access outer key first, then inner
print(users["user1"])         # {'name': 'Alice', 'age': 25}
print(users["user1"]["name"]) # "Alice"
print(users["user2"]["age"])  # 30
```

**List of dictionaries:**
```python
students = [
    {"name": "Alice", "grade": 85},
    {"name": "Bob", "grade": 92},
    {"name": "Charlie", "grade": 78}
]

# Access list index first, then dictionary key
print(students[0])          # {'name': 'Alice', 'grade': 85}
print(students[0]["name"])  # "Alice"
print(students[1]["grade"]) # 92
```

**Dictionary of lists:**
```python
courses = {
    "math": [85, 90, 88],
    "science": [92, 87, 95]
}

# Access dictionary key first, then list index
print(courses["math"])     # [85, 90, 88]
print(courses["math"][0])  # 85
print(courses["science"][2])  # 95
```

#### Modifying Nested Data

**Modify nested list:**
```python
grid = [[1, 2], [3, 4]]
grid[0][1] = 99
print(grid)  # [[1, 99], [3, 4]]
```

**Modify nested dictionary:**
```python
users = {"user1": {"name": "Alice", "age": 25}}
users["user1"]["age"] = 26
print(users)  # {'user1': {'name': 'Alice', 'age': 26}}
```

#### The Alias Trap

**Extracting nested item creates alias:**
```python
data = [[1, 2], [3, 4]]
sublist = data[0]  # Alias, not copy!

sublist[0] = 99
print(data)  # [[99, 2], [3, 4]] - ORIGINAL CHANGED!
```

**Solution - Make explicit copy:**
```python
data = [[1, 2], [3, 4]]
sublist = data[0][:]  # Create copy with slice

sublist[0] = 99
print(data)     # [[1, 2], [3, 4]] - unchanged
print(sublist)  # [99, 2]
```

#### Safe Dictionary Access

**Use .get() to avoid KeyError:**
```python
users = {
    "user1": {"name": "Alice", "age": 25},
    "user2": {"name": "Bob"}  # Missing "age"
}

# BAD - can raise KeyError
age = users["user2"]["age"]  # KeyError!

# GOOD - safe access
age = users.get("user2", {}).get("age", "Unknown")
print(age)  # "Unknown"

# Even better - check at each level
if "user2" in users and "age" in users["user2"]:
    age = users["user2"]["age"]
else:
    age = "Unknown"
```

#### Iterating Nested Structures

**Loop through list of dictionaries:**
```python
students = [
    {"name": "Alice", "grade": 85},
    {"name": "Bob", "grade": 92}
]

for student in students:
    print(f"{student['name']}: {student['grade']}")
```

**Loop through dictionary of lists:**
```python
courses = {
    "math": [85, 90, 88],
    "science": [92, 87, 95]
}

for course, grades in courses.items():
    avg = sum(grades) / len(grades)
    print(f"{course}: {avg:.1f}")
```

**Common Uses:**
- Storing structured data (like JSON)
- Representing tables or grids
- Managing complex data relationships
- Building data from APIs or files

**Related Concepts:** lists, dictionaries, copy semantics, .get() method

---

### Text Parsing

**What it does:** Converts raw text into structured data.

#### Parsing Multi-line Text

**splitlines() - Split text into lines:**
```python
data = """Alice|Paris|29
Bob|London|32
Charlie|Tokyo|28"""

lines = data.splitlines()
print(lines)
# ['Alice|Paris|29', 'Bob|London|32', 'Charlie|Tokyo|28']
```

#### Converting to Structured Data

**Parse into list of dictionaries:**
```python
raw_data = """Alice|Paris|29
Bob|London|32
Charlie|Tokyo|28"""

records = []
lines = raw_data.splitlines()

for line in lines:
    parts = line.split("|")
    record = {
        "name": parts[0],
        "city": parts[1],
        "age": int(parts[2])  # Convert to integer
    }
    records.append(record)

print(records)
# [
#   {'name': 'Alice', 'city': 'Paris', 'age': 29},
#   {'name': 'Bob', 'city': 'London', 'age': 32},
#   {'name': 'Charlie', 'city': 'Tokyo', 'age': 28}
# ]
```

**Access parsed data:**
```python
# Get first person's name
print(records[0]["name"])  # "Alice"

# Loop through all records
for record in records:
    print(f"{record['name']} lives in {record['city']}")
```

#### Type Conversion During Parsing

**Convert numeric strings:**
```python
line = "Product|19.99|50"
parts = line.split("|")

product = {
    "name": parts[0],           # String
    "price": float(parts[1]),   # Convert to float
    "quantity": int(parts[2])   # Convert to integer
}

print(product)
# {'name': 'Product', 'price': 19.99, 'quantity': 50}
```

#### Values Are Copied

**Dictionary values are independent from source:**
```python
line = "Alice|25"
parts = line.split("|")

person = {
    "name": parts[0],
    "age": parts[1]
}

# Modifying parts doesn't affect dictionary
parts[0] = "Bob"
print(person["name"])  # "Alice" (unchanged)
```

#### Practical Parsing Pattern

**Complete workflow:**
```python
# 1. Raw data (multi-line string)
raw_data = """Math|85|3
Science|90|4
English|88|3"""

# 2. Split into lines
lines = raw_data.splitlines()

# 3. Parse each line
courses = []
for line in lines:
    parts = line.split("|")
    course = {
        "subject": parts[0],
        "grade": int(parts[1]),
        "credits": int(parts[2])
    }
    courses.append(course)

# 4. Use structured data
total_points = 0
total_credits = 0

for course in courses.items():
    points = course["grade"] * course["credits"]
    total_points += points
    total_credits += course["credits"]

gpa = total_points / total_credits
print(f"GPA: {gpa:.2f}")
```

**Common Uses:**
- Reading CSV or delimited files
- Processing configuration files
- Parsing API responses
- Converting text data to structured format

**Related Concepts:** strings, split(), dictionaries, lists, type conversion

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

### String Slicing Patterns

| Pattern | Example | Result | Use Case |
|---------|---------|--------|----------|
| `text[start:stop]` | `"Python"[0:3]` | `"Pyt"` | Extract substring |
| `text[:n]` | `"Python"[:3]` | `"Pyt"` | First n characters |
| `text[n:]` | `"Python"[3:]` | `"hon"` | From position to end |
| `text[:]` | `"Python"[:]` | `"Python"` | Copy entire string |
| `text[::2]` | `"Python"[::2]` | `"Pto"` | Every other character |
| `text[::-1]` | `"Python"[::-1]` | `"nohtyP"` | Reverse string |
| `text[-n:]` | `"Python"[-3:]` | `"hon"` | Last n characters |

---

### List Methods Quick Reference

| Method | What It Does | Example | Returns |
|--------|--------------|---------|---------|
| `.append(item)` | Add to end | `list.append(5)` | None (modifies in place) |
| `.insert(i, item)` | Add at position | `list.insert(0, 5)` | None (modifies in place) |
| `.extend(iterable)` | Add all items | `list.extend([1,2])` | None (modifies in place) |
| `.remove(value)` | Remove first match | `list.remove(5)` | None (raises ValueError if not found) |
| `.pop()` | Remove last item | `item = list.pop()` | Removed item |
| `.pop(i)` | Remove at index | `item = list.pop(0)` | Removed item |
| `.sort()` | Sort in place | `list.sort()` | None (modifies in place) |
| `.copy()` | Create copy | `new = list.copy()` | New list |
| `sorted(list)` | Return sorted | `new = sorted(list)` | New sorted list |
| `len(list)` | Get length | `n = len(list)` | Integer |

---

### Dictionary Methods Quick Reference

| Method | What It Does | Example | Returns |
|--------|--------------|---------|---------|
| `dict[key]` | Access value | `dict["name"]` | Value (raises KeyError if missing) |
| `.get(key)` | Safe access | `dict.get("name")` | Value or None |
| `.get(key, default)` | Safe with default | `dict.get("name", "Unknown")` | Value or default |
| `dict[key] = value` | Add/update | `dict["name"] = "Alice"` | None (modifies in place) |
| `.keys()` | Get all keys | `for k in dict.keys():` | View of keys |
| `.values()` | Get all values | `for v in dict.values():` | View of values |
| `.items()` | Get key-value pairs | `for k,v in dict.items():` | View of (key, value) tuples |
| `len(dict)` | Count pairs | `n = len(dict)` | Integer |
| `.copy()` | Create copy | `new = dict.copy()` | New dictionary |
| `key in dict` | Check key exists | `if "name" in dict:` | Boolean |

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

### Text Parsing Pipeline
```python
# Split → Clean → Filter → Join
text = "apple, , banana, cherry, "

# Step 1: Split on delimiter
parts = text.split(",")

# Step 2: Strip whitespace from each part
clean = [item.strip() for item in parts]

# Step 3: Filter out empty strings
filtered = [item for item in clean if item]

# Step 4: Join with new delimiter
result = "; ".join(filtered)
print(result)  # "apple; banana; cherry"
```

### Safe Dictionary Access
```python
# Pattern 1: Using .get() with default
person = {"name": "Marco", "age": 25}
city = person.get("city", "Unknown")
print(city)  # "Unknown"

# Pattern 2: Check before accessing
if "city" in person:
    city = person["city"]
else:
    city = "Unknown"

# Pattern 3: Nested safe access
users = {"user1": {"name": "Alice"}}
age = users.get("user1", {}).get("age", "Unknown")
```

### List Building Pattern
```python
# Initialize empty list
results = []

# Process items and build list
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
for num in numbers:
    if num % 2 == 0:  # Filter condition
        doubled = num * 2  # Transform
        results.append(doubled)

print(results)  # [4, 8, 12, 16, 20]
```

### Dictionary Counter Pattern
```python
# Count occurrences
items = ["apple", "banana", "apple", "cherry", "banana", "apple"]
counts = {}

for item in items:
    if item in counts:
        counts[item] += 1
    else:
        counts[item] = 1

print(counts)  # {'apple': 3, 'banana': 2, 'cherry': 1}
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

**IndexError:**
```python
# Error: list index out of range
numbers = [1, 2, 3]
print(numbers[5])  # IndexError!
# Fix: Check length first
if 5 < len(numbers):
    print(numbers[5])
else:
    print("Index out of range")
```

**KeyError:**
```python
# Error: key doesn't exist in dictionary
person = {"name": "Marco"}
print(person["age"])  # KeyError: 'age'
# Fix: Use .get() for safe access
age = person.get("age", "Unknown")
# Or check first
if "age" in person:
    print(person["age"])
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
