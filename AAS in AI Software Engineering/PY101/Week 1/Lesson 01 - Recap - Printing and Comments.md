# Recap: Printing and Comments

**Date:** October 21, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 1, Lesson 1

## What You'll Learn

This recap covers the fundamentals of displaying output in Python and documenting your code with comments.

---

## The `print()` Function

The `print()` function displays output to the console. It's your primary tool for showing results to users.

### Basic Printing

```python
print("Hello, World!")
# Output: Hello, World!
```

### Printing Multiple Items

Use commas to separate multiple values. Python automatically adds spaces between them.

```python
print("red", "blue")
# Output: red blue
```

**Rule:** Python inserts one space between each comma-separated item.

### Printing on Separate Lines

Each `print()` statement creates a new line.

```python
print("A")
print("B")
# Output:
# A
# B
```

---

## Print with Expressions

You can include calculations directly in `print()` statements.

```python
print("2+3=", 2+3)
# Output: 2+3= 5
```

**How It Works:**
1. Python evaluates the expression `2+3` first (result: `5`)
2. Then prints the string `"2+3="` followed by the result
3. Adds a space between the string and the number

---

## Repetition with the `*` Operator

The multiplication operator works with strings to repeat them.

```python
print("=" * 8)
# Output: ========
```

**Pattern:**
- `"text" * n` repeats the string `n` times
- Only works with integers (whole numbers)
- Useful for creating visual separators or borders

**More Examples:**

```python
print("*" * 10)
# Output: **********

print("-" * 5)
# Output: -----

print("Hello " * 3)
# Output: Hello Hello Hello 
```

---

## Comments in Python

Comments are notes in your code that Python ignores. They explain what your code does for yourself and other programmers.

### Single-Line Comments

Use `#` to create a comment. Everything after `#` on that line is ignored.

```python
# TODO: say hello
print("hi")
```

**Uses for Comments:**
- Explain complex logic
- Mark tasks to complete later (TODO)
- Temporarily disable code (comment it out)
- Add context about why code exists

```python
# Calculate total cost including tax
total = price + (price * 0.08)

# This formula uses the distance-rate-time relationship
distance = speed * time
```

---

## String Formatting

Python offers multiple ways to format text output.

### Method 1: Basic String with Variables

```python
name = "Marco"
print("Hello, {name}!")
# Output: Hello, {name}!
```

**Problem:** Curly braces are treated as literal text, not as placeholders.

### Method 2: F-Strings (Formatted Strings)

Add `f` before the opening quote to create an f-string. Variables inside `{}` get replaced with their values.

```python
name = "Marco"
print(f"Hello, {name}!")
# Output: Hello, Marco!
```

**Why F-Strings Are Better:**
- Variables get inserted automatically
- More readable and concise
- Less error-prone than concatenation
- Can include expressions inside `{}`

**F-String Examples:**

```python
age = 25
print(f"I am {age} years old")
# Output: I am 25 years old

price = 19.99
print(f"Total cost: ${price}")
# Output: Total cost: $19.99

x = 5
y = 3
print(f"{x} + {y} = {x + y}")
# Output: 5 + 3 = 8
```

---

## Printing with Multiple Items

### Commas Create Spaces

```python
name = "Marco"
print("hi", name)
# Output: hi Marco
```

Each comma adds a space automatically.

### Combining Text and Numbers

```python
score = 100
print("Your score:", score, "points")
# Output: Your score: 100 points
```

### F-Strings vs Comma Separation

```python
# Using commas (automatic spaces)
print("Result:", 10 + 5)
# Output: Result: 15

# Using f-string (controlled spacing)
print(f"Result:{10 + 5}")
# Output: Result:15
```

**Tip:** F-strings give you more control over spacing and formatting.

---

## Common Patterns

### Creating Visual Separators

```python
print("=" * 40)
print("MENU")
print("=" * 40)
# Output:
# ========================================
# MENU
# ========================================
```

### Debug Output

```python
username = "player1"
score = 1500
print("DEBUG: username =", username, "score =", score)
# Output: DEBUG: username = player1 score = 1500
```

### User-Friendly Messages

```python
name = "Marco"
points = 75
print(f"Congratulations, {name}! You earned {points} points.")
# Output: Congratulations, Marco! You earned 75 points.
```

---

## Practice Exercises

**Exercise 1: Print Your Info**

Print your name, age, and favorite color on separate lines.

<details>
<summary>Solution</summary>

```python
print("Marco")
print(25)
print("Blue")
```
</details>

**Exercise 2: Create a Banner**

Print a banner with stars using the repetition operator.

<details>
<summary>Solution</summary>

```python
print("*" * 20)
print("Welcome to Python!")
print("*" * 20)
```
</details>

**Exercise 3: Use F-Strings**

Create variables for your name and favorite food, then print them in a sentence using an f-string.

<details>
<summary>Solution</summary>

```python
name = "Marco"
food = "pizza"
print(f"My name is {name} and I love {food}!")
# Output: My name is Marco and I love pizza!
```
</details>

---

## Key Takeaways

✅ **`print()` displays output** - Your primary tool for showing results  
✅ **Commas add automatic spaces** - Between items in print statements  
✅ **`*` repeats strings** - Useful for borders and patterns  
✅ **Comments start with `#`** - Python ignores them completely  
✅ **F-strings format text** - Use `f"text {variable}"` for clean output  
✅ **Each print creates a new line** - Unless specified otherwise

**Remember:** The `print()` function is how your program communicates with users. Master it early because you'll use it constantly for both output and debugging.

---

**Last Updated:** October 25, 2025