# Naming That Tells a Story

**Date:** October 28, 2025  
**Course:** CS101 - Computer Science Fundamentals  
**Week:** 1, Lesson 01

## What You'll Learn

This lesson trains you to write descriptive variable and function names that make your code self-documenting. You'll learn naming conventions, practice consistent renaming, and understand how good names eliminate guesswork for anyone reading your code.

---

## Why Good Naming Matters

Code is read far more often than it's written. When you return to your code weeks later, or when a teammate opens your file, clear names make the difference between instant understanding and frustrating detective work.

**Good naming = clear code, no guessing needed.**

Names should communicate:
- **What** the data represents
- **Why** it exists in your program
- **How** it should be used

### The Cost of Bad Names

```python
# What does this code do?
x = 7
y = x * 9/5 + 32
print(y)
# Output: 44.6
```

The math works, but the intent is hidden. You need to reverse-engineer the formula to understand it converts Celsius to Fahrenheit.

### The Clarity of Good Names

```python
# Same logic, clear intent
temp_celsius = 7
temp_fahrenheit = temp_celsius * 9/5 + 32
print(f"Temperature: {temp_fahrenheit}°F")
# Output: Temperature: 44.6°F
```

The names explain the purpose immediately. No mental translation required.

---

## Python Naming Convention: snake_case

Python uses **snake_case** for variable and function names: lowercase words separated by underscores.

### Basic Pattern

```python
# Variables use snake_case
max_temperature = 100
user_name = "Marco"
items_in_cart = 5

# Functions use snake_case
def calculate_total():
    pass

def send_email():
    pass
```

**Why snake_case?**
- Reads naturally like written language
- Standard across Python code
- Improves searchability in codebases

### Comparing Naming Styles

```python
# Bad: Single letters give no context
x = 5
y = 10
z = x + y

# Better: Abbreviated but still cryptic
tmp = 5
cnt = 10
tot = tmp + cnt

# Best: Full descriptive names
hours_worked = 5
hourly_rate = 10
total_pay = hours_worked * hourly_rate
```

---

## The Noun/Verb Rule

Use **nouns** for data (things), **verbs** for actions (functions).

### Nouns for Data

Variables hold information, so name them with nouns that describe what they contain.

```python
# Data as nouns
playlist = ["Song 1", "Song 2", "Song 3"]
max_score = 100
user_email = "marco@example.com"
shopping_cart = []
current_temperature = 72
```

### Verbs for Actions

Functions perform operations, so name them with verbs that describe what they do.

```python
# Actions as verbs
def calculate_average(numbers):
    return sum(numbers) / len(numbers)

def sort_playlist(songs):
    return sorted(songs)

def send_notification(user):
    print(f"Notification sent to {user}")

def validate_email(email):
    return "@" in email
```

**Pattern Recognition:**
- If it stores something: use a noun
- If it does something: use a verb

---

## Consistent Renaming: The Full Pass

When you rename a variable, update **every reference** to it. Partial renaming creates confusion and bugs.

### The Problem: Partial Renaming

```python
# Original confusing code
a = [25, 32, 27]
b = []
for c in a:
    b.append((c * 9/5) + 32)

# Partial rename - still confusing!
daily_scores = [25, 32, 27]
fahrenheit_temps = []
for c in a:  # Wait, what's 'a'? What's 'c'?
    b.append((c * 9/5) + 32)  # And 'b'?
```

### The Solution: Complete Renaming

```python
# All references updated consistently
daily_scores = [25, 32, 27]
fahrenheit_temps = []
for score in daily_scores:
    fahrenheit_temps.append((score * 9/5) + 32)

print(fahrenheit_temps)
# Output: [77.0, 89.6, 80.6]
```

**Rule:** Find-and-replace is your friend. Change the name everywhere, then test.

---

## Loop Variables: Tell the Story

Loop variables should describe what each item represents.

### Generic vs Descriptive

```python
# Generic - acceptable for simple cases
for i in range(5):
    print(i)

# Descriptive - better for clarity
for day_number in range(5):
    print(f"Day {day_number}")
```

### Context-Rich Loop Variables

```python
# Processing temperatures
temperatures = [72, 75, 68, 71]
for temp in temperatures:
    print(f"Current reading: {temp}°F")

# Processing user data
users = ["Marco", "Alex", "Sam"]
for username in users:
    print(f"Welcome, {username}!")

# Processing financial data
transactions = [100, 250, 75, 300]
for amount in transactions:
    print(f"Transaction: ${amount}")
```

**Tip:** The loop variable should be the singular form of the collection name when possible.

---

## Function Parameters: Signal Flexibility

Function parameters should indicate their purpose and acceptable values.

### Evolution of a Function Name

```python
# Version 1: Cryptic
def pl(d, fn):
    return sorted(d, key=fn)

# Version 2: Better data name
def pl(music, fn):
    return sorted(music, key=fn)

# Version 3: Better function name
def sort_playlist(music, fn):
    return sorted(music, key=fn)

# Version 4: Flexible parameter name
def sort_playlist(music, sort_key):
    """Sort a playlist using a custom sorting function."""
    return sorted(music, key=sort_key)
```

**Why `sort_key` is better than `title`:**
- Works for sorting by title, artist, duration, or any attribute
- Signals that the parameter accepts a function
- Remains accurate if sorting logic changes

### Using the Flexible Function

```python
# Define music data
playlist = [
    {"title": "Imagine", "artist": "John Lennon"},
    {"title": "Bohemian Rhapsody", "artist": "Queen"},
    {"title": "Hey Jude", "artist": "The Beatles"}
]

# Sort by title
by_title = sort_playlist(playlist, lambda song: song["title"])

# Sort by artist
by_artist = sort_playlist(playlist, lambda song: song["artist"])
```

---

## Copy vs Alias: Understanding List References

When you assign one variable to another containing a list, you create an **alias** (both point to the same data). To create an independent **copy**, use slicing.

### Alias: Shared Reference

```python
# Original list
temperatures = [22, 24, 21]

# Create an alias (same list, different name)
daily_temps = temperatures

# Modify through the alias
daily_temps[0] = 100

# Both variables show the change
print(temperatures)
# Output: [100, 24, 21]

print(daily_temps)
# Output: [100, 24, 21]
```

**What happened:** Both variables point to the same underlying list. Changing one changes both.

### Copy: Independent List

```python
# Original list
temperatures = [22, 24, 21]

# Create a copy using slice notation
daily_temps_copy = temperatures[:]

# Modify the copy
daily_temps_copy[0] = 100

# Original remains unchanged
print(temperatures)
# Output: [22, 24, 21]

print(daily_temps_copy)
# Output: [100, 24, 21]
```

**What happened:** The slice `[:]` created a new list with the same values. Changes to the copy don't affect the original.

### When to Use Each

**Use Alias when:**
- You want changes to reflect everywhere
- You're passing data to a function that should modify the original
- Memory efficiency matters (large lists)

**Use Copy when:**
- You need to preserve the original data
- You're experimenting with transformations
- You want to compare before/after states

```python
# Practical example: data analysis
raw_data = [100, 250, 75, 300, 150]

# Keep original for audit trail
working_data = raw_data[:]

# Experiment with transformations
working_data.sort()
working_data.append(500)

# Original data preserved
print(f"Original: {raw_data}")
# Output: Original: [100, 250, 75, 300, 150]

print(f"Modified: {working_data}")
# Output: Modified: [75, 100, 150, 250, 300, 500]
```

---

## Common Naming Mistakes

### Mistake 1: Reusing Names for Different Purposes

```python
# Bad: 'data' used for multiple things
data = [1, 2, 3]
data = sum(data)
data = data / len(data)  # Error! data is now a number
```

```python
# Good: Distinct names for distinct values
numbers = [1, 2, 3]
total = sum(numbers)
average = total / len(numbers)
```

### Mistake 2: Ambiguous Abbreviations

```python
# Bad: What does 'temp' mean?
temp = get_data()  # Temporary? Temperature?
temp = process(temp)
```

```python
# Good: Full words remove ambiguity
temporary_data = get_data()
processed_result = process(temporary_data)
```

### Mistake 3: Names That Lie

```python
# Bad: Name doesn't match behavior
def get_user():
    user = fetch_from_database()
    user.last_seen = datetime.now()  # Modifying, not just getting!
    return user
```

```python
# Good: Name reflects actual behavior
def get_and_update_user():
    user = fetch_from_database()
    user.last_seen = datetime.now()
    return user
```

---

## Practice Exercises

**Exercise 1: Rename for Clarity**

Rename the variables in this temperature conversion code to be descriptive and consistent.

```python
a = [0, 10, 20, 30]
b = []
for c in a:
    b.append(c * 9/5 + 32)
print(b)
```

<details>
<summary>Solution</summary>

```python
# Descriptive names for temperature conversion
celsius_temps = [0, 10, 20, 30]
fahrenheit_temps = []
for temp_celsius in celsius_temps:
    fahrenheit_temps.append(temp_celsius * 9/5 + 32)

print(fahrenheit_temps)
# Output: [32.0, 50.0, 68.0, 86.0]
```

**Explanation:** Clear names indicate this converts Celsius to Fahrenheit. The loop variable `temp_celsius` describes each item being processed.

</details>

**Exercise 2: Improve Function Names**

Rename this function and its parameters to be more descriptive.

```python
def calc(x, y):
    return x * y

result = calc(5, 10)
print(result)
```

<details>
<summary>Solution</summary>

```python
# Descriptive function and parameter names
def calculate_area(width, height):
    """Calculate the area of a rectangle."""
    return width * height

rectangle_area = calculate_area(5, 10)
print(f"Area: {rectangle_area} square units")
# Output: Area: 50 square units
```

**Explanation:** The function name uses a verb (`calculate`). Parameters describe what values are expected. The return variable name indicates what the result represents.

</details>

**Exercise 3: Copy vs Alias**

Create a list of scores. Make an alias and a copy. Modify the first score in each. Print all three to see the difference.

<details>
<summary>Solution</summary>

```python
# Original scores
original_scores = [85, 90, 78, 92]

# Create alias (shares same list)
score_alias = original_scores

# Create copy (independent list)
score_copy = original_scores[:]

# Modify first score in alias
score_alias[0] = 100

# Modify first score in copy
score_copy[0] = 50

# Check results
print(f"Original: {original_scores}")
# Output: Original: [100, 90, 78, 92]

print(f"Alias: {score_alias}")
# Output: Alias: [100, 90, 78, 92]

print(f"Copy: {score_copy}")
# Output: Copy: [50, 90, 78, 92]
```

**Explanation:** The alias modification changed both `original_scores` and `score_alias` because they reference the same list. The copy modification only affected `score_copy` because it's an independent list.

</details>

---

## Key Takeaways

✅ **Use snake_case for Python** - Lowercase with underscores between words  
✅ **Nouns for data, verbs for actions** - Variables are things, functions do things  
✅ **Rename consistently** - Update all references when changing a variable name  
✅ **Descriptive loop variables** - `for user in users` not `for x in users`  
✅ **Flexible parameter names** - `sort_key` works better than `title` for general functions  
✅ **Slicing creates copies** - `new_list = old_list[:]` makes an independent copy  
✅ **Names eliminate comments** - Good names explain code without additional documentation

**Remember:** Code is written once but read many times. Invest 10 seconds choosing a clear name and save 10 minutes of confusion later.

---

**Last Updated:** November 12, 2025
