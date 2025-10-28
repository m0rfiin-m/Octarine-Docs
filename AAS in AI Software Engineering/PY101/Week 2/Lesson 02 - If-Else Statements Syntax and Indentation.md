# If/Else Statements: Syntax and Indentation

**Date:** October 28, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 2, Lesson 2  
**Lesson Link:** [Maestro Lesson](https://maestro.org/learn/688b5ab40508accc71b2ef49-4/688b5ab40508accc71b2e87a-56/68f5356d52288d89898846dc)

## What You'll Learn

This lesson covers conditional statements in Python, focusing on if/else syntax, indentation rules, and the mental model for making decisions in your code.

---

## Loops vs. If/Else

Understanding the difference between these two control structures is fundamental.

### Loops: Repetition

Loops repeat the same action multiple times.

```python
for i in range(3):
    print("Repeating")
# Output:
# Repeating
# Repeating
# Repeating
```

### If/Else: Decision-Making

If/else chooses between two possible paths based on a condition (yes/no decision).

```python
temp = 65

if temp < 60:
    print("wear jacket")
else:
    print("t-shirt")
# Output: t-shirt
```

**Key Difference:** Loops do something multiple times. If/else does one thing OR another, but not both.

---

## Python Indentation Rules

Indentation is not optional in Python. It defines code structure and determines what belongs together.

### The Golden Rules

**Rule 1:** Use 4 spaces for each indent level (standard convention)

**Rule 2:** Code blocks require indentation after a colon (`:`)

**Rule 3:** All lines at the same indent level belong to the same block

**Rule 4:** Never mix tabs and spaces (causes errors)

### What Happens Without Proper Indentation

```python
if True:
print("This will raise IndentationError")
```

**Result:** Python raises an `IndentationError` because the print statement is not indented.

### Correct Indentation

```python
if True:
    print("Both lines indented")
    print("Still inside the if")
# Output:
# Both lines indented
# Still inside the if
```

Both print statements execute because they are at the same indent level under the if block.

### Partial Indentation

```python
if True:
    print("This runs inside the if")
print("This always runs")
# Output:
# This runs inside the if
# This always runs
```

Only indented lines after the colon belong to the if block. Unindented lines are outside the block and always execute.

---

## If/Else Block Structure

The basic syntax for making decisions in Python.

### Required Elements

1. **`if` keyword** - Starts the decision
2. **Condition** - Expression that evaluates to True or False
3. **Colon (`:`)** - Marks the start of the code block
4. **Indented code** - What runs if condition is True
5. **`else` keyword** - Alternative path
6. **Another colon (`:`)** - Starts the else block
7. **Indented code** - What runs if condition is False

### Basic Template

```python
if condition:
    # Code that runs if condition is True
    action_1()
    action_2()
else:
    # Code that runs if condition is False
    alternative_1()
    alternative_2()
```

### Working Example

```python
temp = 40

if temp < 60:
    print("wear jacket")
else:
    print("t-shirt")
# Output: wear jacket
```

**Try This:** Change `temp` to 75. What prints now?

<details>
<summary>Answer</summary>

```python
temp = 75

if temp < 60:
    print("wear jacket")
else:
    print("t-shirt")
# Output: t-shirt
```

The condition `75 < 60` is False, so the else block runs.
</details>

---

## Assignment vs. Comparison

One of the most common mistakes in Python is confusing assignment with comparison.

### Assignment: The `=` Operator

Sets a value to a variable.

```python
score = 5  # Assigns the value 5 to score
name = "Marco"  # Assigns the string "Marco" to name
```

**Purpose:** Store data in variables.

### Comparison: The `==` Operator

Checks if two values are equal. Returns True or False.

```python
score = 5

if score == 10:
    print("You win!")
else:
    print("Keep trying")
# Output: Keep trying
```

**Purpose:** Make decisions based on equality.

### Common Error: Using `=` in Conditions

```python
if score = 10:  # SyntaxError! Cannot assign in condition
    print("This won't work")
```

**Error Message:** `SyntaxError: invalid syntax`

**Why It Fails:** Python expects a comparison (evaluates to True/False), not an assignment.

### Correct Usage

```python
# Assignment (sets value)
score = 10

# Comparison (checks value)
if score == 10:
    print("Perfect score!")
```

---

## Comparison Operators

Python provides multiple ways to compare values.

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `==` | Equal to | `5 == 5` | `True` |
| `!=` | Not equal to | `5 != 3` | `True` |
| `<` | Less than | `3 < 5` | `True` |
| `>` | Greater than | `5 > 3` | `True` |
| `<=` | Less than or equal | `5 <= 5` | `True` |
| `>=` | Greater than or equal | `5 >= 3` | `True` |

### Examples in Context

```python
age = 18

if age >= 18:
    print("Adult")
else:
    print("Minor")
# Output: Adult

score = 85

if score > 90:
    print("A grade")
else:
    print("Not an A")
# Output: Not an A

password = "secret123"

if password == "secret123":
    print("Access granted")
else:
    print("Access denied")
# Output: Access granted
```

---

## Combining Loops and Conditionals

The real power comes from using control structures together.

### Pattern: Loop Through Items, Decide on Each

```python
numbers = [2, -7, 0]

for number in numbers:
    if number > 0:
        print("positive")
    else:
        print("negative")
```

**Output:**
```
positive
negative
negative
```

**How It Works:**
1. Loop goes through each number in the list
2. For each number, the if/else decides: positive or negative
3. Prints the result for that specific number

### More Examples

**Example 1: Filter Even Numbers**

```python
numbers = [4, 7, 10, 15]

for num in numbers:
    if num % 2 == 0:
        print(f"{num} is even")
    else:
        print(f"{num} is odd")
```

**Output:**
```
4 is even
7 is odd
10 is even
15 is odd
```

**Example 2: Grade Checker**

```python
scores = [95, 72, 88, 61]

for score in scores:
    if score >= 90:
        print(f"{score}: Excellent")
    else:
        print(f"{score}: Good effort")
```

**Output:**
```
95: Excellent
72: Good effort
88: Good effort
61: Good effort
```

---

## Common Pitfalls

### Pitfall 1: Missing Colons

```python
# Wrong
if temp < 60
    print("jacket")

# Correct
if temp < 60:
    print("jacket")
```

**Error Message:** `SyntaxError: invalid syntax`

**Fix:** Add a colon after the condition.

### Pitfall 2: Assignment Instead of Comparison

```python
# Wrong - Using = instead of ==
if score = 10:  # SyntaxError
    print("Win")

# Correct
if score == 10:
    print("Win")
```

**Error Message:** `SyntaxError: invalid syntax`

**Fix:** Use `==` to compare, `=` only to assign.

### Pitfall 3: Inconsistent Indentation

```python
# Wrong - Different indent levels
if True:
    print("First line")
  print("Wrong indent")  # IndentationError

# Correct
if True:
    print("First line")
    print("Same indent level")
```

**Error Message:** `IndentationError: unindent does not match any outer indentation level`

**Fix:** Use consistent 4-space indentation for all lines in a block.

### Pitfall 4: Forgetting the Else Block Is Optional

```python
# This is valid - no else needed
if score > 100:
    print("Bonus points!")

# Only prints if condition is True
# If False, nothing happens
```

**Tip:** Use else when you need an alternative action. Skip it when you only care about one outcome.

---

## Mental Model: Code Blocks as Nested Boxes

Think of code execution as moving through nested boxes.

```
Main Program
│
├─ if condition:
│   ├─ Action 1 (runs if True)
│   └─ Action 2 (runs if True)
│
└─ else:
    ├─ Action 3 (runs if False)
    └─ Action 4 (runs if False)
```

### Key Principles

**Principle 1: Indentation Defines Blocks**

Everything at the same indent level is in the same box (block).

**Principle 2: Only One Branch Executes**

Either the if block OR the else block runs, never both.

**Principle 3: Conditions Evaluate to True/False**

Python checks the condition. If True, take the if path. If False, take the else path.

**Principle 4: Comparison vs. Assignment**

- Use `==` to check values (comparison)
- Use `=` to set values (assignment)
- Never use `=` in conditions

---

## Practice Exercises

### Exercise 1: Temperature Classifier

Write a program that checks if the temperature is freezing (32°F or below) or above freezing.

<details>
<summary>Solution</summary>

```python
temp = 28

if temp <= 32:
    print("Freezing")
else:
    print("Above freezing")
# Output: Freezing
```
</details>

**Challenge:** Add a third condition for temperatures above 80°F (hint: you'll learn about `elif` soon).

### Exercise 2: Even or Odd Checker

Create a loop that checks if numbers in a list are even or odd.

<details>
<summary>Solution</summary>

```python
numbers = [4, 7, 10, 15]

for num in numbers:
    if num % 2 == 0:
        print(f"{num} is even")
    else:
        print(f"{num} is odd")
```

**Output:**
```
4 is even
7 is odd
10 is even
15 is odd
```
</details>

### Exercise 3: Password Validator

Write code that checks if a password matches the correct password.

<details>
<summary>Solution</summary>

```python
correct_password = "python123"
user_input = "python123"

if user_input == correct_password:
    print("Access granted")
else:
    print("Access denied")
# Output: Access granted
```
</details>

### Exercise 4: Predict the Output

What will this code print?

```python
x = 10

if x > 5:
    print("A")
    if x > 8:
        print("B")
else:
    print("C")
```

<details>
<summary>Answer</summary>

**Output:**
```
A
B
```

**Explanation:**
1. `x > 5` is True (10 > 5), so the if block runs
2. Prints "A"
3. Inside that block, `x > 8` is also True (10 > 8)
4. Prints "B"
5. The else block never runs because the if condition was True
</details>

---

## Real-World Applications

### User Authentication

```python
username = "player1"
password = "secret"

if password == "secret":
    print(f"Welcome back, {username}!")
else:
    print("Incorrect password")
```

### Content Filtering

```python
age = 16

if age < 18:
    print("Content restricted")
else:
    print("Access granted")
```

### Game Logic

```python
score = 1500
high_score = 1200

if score > high_score:
    print("New high score!")
    high_score = score
else:
    print(f"Current high score: {high_score}")
```

### E-commerce

```python
items_in_cart = 3

if items_in_cart > 0:
    print("Proceed to checkout")
else:
    print("Your cart is empty")
```

---

## Key Takeaways

✅ **If/else makes decisions** - Chooses between two paths based on True/False  
✅ **Indentation is mandatory** - 4 spaces per level, defines code blocks  
✅ **Colons start blocks** - Every if and else needs a `:`  
✅ **Only one branch executes** - Either if or else, never both  
✅ **Use `==` to compare** - `=` assigns, `==` checks equality  
✅ **Conditions must be True/False** - Comparison operators return boolean values  
✅ **Combine with loops** - Make decisions for each item in a sequence

**Remember:** Indentation defines structure in Python. Unlike other languages that use braces `{}`, Python relies on whitespace. Get comfortable with the 4-space standard early, and your code will be clean and readable.

---

**Last Updated:** October 28, 2025