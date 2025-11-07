# Lists III: Mastering List Iteration

**Date:** November 7, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 3, Lesson 06

## What You'll Learn

Iteration is how you process every item in a list. This lesson teaches you multiple ways to loop through lists, from simple value-based loops to index-based approaches. You'll learn when to use each technique, how to perform calculations during iteration, and how to safely check for specific items or conditions.

---

## Why List Iteration Matters

Lists hold collections of data, but that data only becomes useful when you can process it. You need iteration to calculate totals from a list of prices, search for specific records in user data, or transform each item in a collection. Mastering iteration patterns is fundamental to working with any data structure in Python.

Real programs constantly loop through lists: e-commerce sites calculate cart totals, weather apps process temperature readings, and social media platforms filter posts. Every interactive system depends on efficient list iteration.

---

## Looping by Value (The Direct Approach)

The most common iteration pattern accesses each value directly without worrying about positions.

### Basic Value Loop

```python
# Display temperature readings from sensors
temps = [17, 22, 19, 25]

for temp in temps:
    print(f"{temp}°C")
# Output: 17°C
# Output: 22°C
# Output: 19°C
# Output: 25°C
```

This pattern works when you only need the values themselves. The loop variable (`temp`) takes on each value in sequence, from first to last.

### Processing Values During Iteration

```python
# Calculate total from daily sales
sales = [120, 340, 280, 450]
total = 0

for amount in sales:
    print(f"Sale: ${amount}")
    total += amount  # Accumulate the running total

print(f"Total sales: ${total}")
# Output: Sale: $120
# Output: Sale: $340
# Output: Sale: $280
# Output: Sale: $450
# Output: Total sales: $1190
```

**Key Pattern:** Initialize the accumulator (`total = 0`) before the loop. Update it inside the loop. Use the final value after the loop completes.

### Checking Conditions on Values

```python
# Identify even and odd temperature readings
temps = [17, 22, 19, 25]

for temp in temps:
    print(f"{temp}°C", end=" - ")
    
    if temp % 2 == 0:
        print("even")
    else:
        print("odd")
# Output: 17°C - odd
# Output: 22°C - even
# Output: 19°C - odd
# Output: 25°C - odd
```

The modulo operator (`%`) returns the remainder after division. Even numbers divided by 2 have zero remainder.

---

## Looping by Index (Position-Based Approach)

Sometimes you need both the value and its position in the list. Index-based loops give you this control.

### Basic Index Loop

```python
# Display numbered list of tasks
tasks = ["email", "meeting", "report", "calls"]

for i in range(len(tasks)):
    task = tasks[i]
    print(f"Task #{i}: {task}")
# Output: Task #0: email
# Output: Task #1: meeting
# Output: Task #2: report
# Output: Task #3: calls
```

**How It Works:**
- `len(tasks)` returns 4 (the number of items)
- `range(4)` generates numbers 0, 1, 2, 3
- Each number becomes an index to access `tasks[i]`

### Working with Start Position 1

```python
# Display numbered list starting from 1 (more human-friendly)
tasks = ["email", "meeting", "report", "calls"]

for i in range(len(tasks)):
    task = tasks[i]
    print(f"Task #{i + 1}: {task}")
# Output: Task #1: email
# Output: Task #2: meeting
# Output: Task #3: report
# Output: Task #4: calls
```

Adding 1 to the index when displaying makes the output match how humans typically count (starting from 1).

---

## The Guard Pattern: Selective Processing

The guard pattern lets you act on specific items based on their position.

### Processing a Single Index

```python
# Highlight a specific temperature reading
temps = [17, 22, 19, 25]
target_index = 2

for i in range(len(temps)):
    value = temps[i]
    
    if i == target_index:
        print(f"TARGET: {value}°C at position {i}")
    else:
        print(f"{value}°C at position {i}")
# Output: 17°C at position 0
# Output: 22°C at position 1
# Output: TARGET: 19°C at position 2
# Output: 25°C at position 3
```

The guard (`if i == target_index`) protects the special processing so it only happens for the chosen position.

### Processing Multiple Positions

```python
# Mark first and last items differently
items = ["start", "middle1", "middle2", "end"]

for i in range(len(items)):
    if i == 0:
        print(f"FIRST: {items[i]}")
    elif i == len(items) - 1:
        print(f"LAST: {items[i]}")
    else:
        print(f"Middle: {items[i]}")
# Output: FIRST: start
# Output: Middle: middle1
# Output: Middle: middle2
# Output: LAST: end
```

Multiple guards let you handle different positions with different logic.

---

## Membership Testing: Fast Lookups

Python provides the `in` operator to check if a value exists in a list without looping manually.

### Basic Membership Check

```python
# Check if product is in stock
inventory = ["apple", "banana", "orange", "grape"]

if "banana" in inventory:
    print("Banana is available")
else:
    print("Banana is out of stock")
# Output: Banana is available

print("mango" in inventory)
# Output: False
```

The `in` operator returns `True` if the value exists, `False` otherwise. This is faster than writing your own loop to search.

### Using Membership Before Processing

```python
# Safely remove an item only if it exists
shopping_cart = ["milk", "eggs", "bread"]
item_to_remove = "butter"

if item_to_remove in shopping_cart:
    shopping_cart.remove(item_to_remove)
    print(f"Removed {item_to_remove}")
else:
    print(f"{item_to_remove} not in cart")
# Output: butter not in cart

print(f"Cart: {shopping_cart}")
# Output: Cart: ['milk', 'eggs', 'bread']
```

Checking membership prevents errors when trying to remove items that don't exist.

---

## Combining Iteration Techniques

Real programs often combine multiple patterns to solve complex problems.

### Calculate Statistics While Filtering

```python
# Calculate average of temperatures above freezing
temps = [-5, 2, 8, -2, 15, 20]
above_freezing = []

for temp in temps:
    if temp > 0:
        above_freezing.append(temp)

if above_freezing:  # Check if list has items
    average = sum(above_freezing) / len(above_freezing)
    print(f"Temps above freezing: {above_freezing}")
    print(f"Average: {average:.1f}°C")
else:
    print("No temperatures above freezing")
# Output: Temps above freezing: [2, 8, 15, 20]
# Output: Average: 11.2°C
```

This combines value iteration, conditional filtering, and accumulation into a new list.

### Position-Based Value Comparison

```python
# Compare each score to the previous one
scores = [85, 90, 88, 95, 92]

for i in range(1, len(scores)):  # Start at 1, not 0
    current = scores[i]
    previous = scores[i - 1]
    
    if current > previous:
        print(f"Score {i}: {current} - IMPROVED from {previous}")
    elif current < previous:
        print(f"Score {i}: {current} - DECLINED from {previous}")
    else:
        print(f"Score {i}: {current} - SAME as {previous}")
# Output: Score 1: 90 - IMPROVED from 85
# Output: Score 2: 88 - DECLINED from 90
# Output: Score 3: 95 - IMPROVED from 88
# Output: Score 4: 92 - DECLINED from 95
```

Starting `range(1, len(scores))` at index 1 ensures you can safely access `i - 1` without going below index 0.

---

## Common Errors and Fixes

### Error 1: Modifying List While Iterating

**Bad Code:**

```python
# Attempting to remove items during iteration
numbers = [1, 2, 3, 4, 5]

for num in numbers:
    if num % 2 == 0:
        numbers.remove(num)  # Dangerous!

print(numbers)
# Output: [1, 3, 5] - might miss items or cause errors
```

**Why This Fails:**  
Removing items during iteration changes list size and shifts indices, causing the loop to skip items or access invalid positions.

**Fixed Code:**

```python
# Build new list with only items you want to keep
numbers = [1, 2, 3, 4, 5]
odd_numbers = []

for num in numbers:
    if num % 2 != 0:  # Keep odd numbers
        odd_numbers.append(num)

print(odd_numbers)
# Output: [1, 3, 5]
```

**Why This Works:**  
Creating a new list avoids modifying the original during iteration. The loop processes all items safely.

### Error 2: Accumulator Outside Loop Scope

**Bad Code:**

```python
# Trying to use accumulator before initializing
temps = [17, 22, 19, 25]

for temp in temps:
    total += temp  # NameError: name 'total' is not defined
```

**Why This Fails:**  
The variable `total` doesn't exist when the loop tries to use it.

**Fixed Code:**

```python
# Initialize accumulator before loop
temps = [17, 22, 19, 25]
total = 0  # Start with zero

for temp in temps:
    total += temp

print(f"Total: {total}")
# Output: Total: 83
```

**Why This Works:**  
Initializing `total = 0` before the loop creates the variable. Each iteration adds to this existing value.

### Error 3: Off-by-One Index Error

**Bad Code:**

```python
# Accessing index that doesn't exist
scores = [85, 90, 95]

for i in range(len(scores)):
    current = scores[i]
    next_score = scores[i + 1]  # IndexError on last iteration
    print(f"Current: {current}, Next: {next_score}")
# Error: IndexError: list index out of range
```

**Why This Fails:**  
When `i` equals 2 (last valid index), `i + 1` equals 3, which doesn't exist in a 3-item list.

**Fixed Code:**

```python
# Stop loop before last index
scores = [85, 90, 95]

for i in range(len(scores) - 1):  # Stop at second-to-last item
    current = scores[i]
    next_score = scores[i + 1]
    print(f"Current: {current}, Next: {next_score}")
# Output: Current: 85, Next: 90
# Output: Current: 90, Next: 95
```

**Why This Works:**  
Using `range(len(scores) - 1)` stops the loop at index 1, ensuring `i + 1` never exceeds valid indices.

### Error 4: Printing Inside Loop Instead of After

**Bad Code:**

```python
# Printing total on every iteration
prices = [10, 20, 30, 40]
total = 0

for price in prices:
    total += price
    print(f"Total: {total}")  # Wrong: prints partial totals
# Output: Total: 10
# Output: Total: 30
# Output: Total: 60
# Output: Total: 100
```

**Why This Fails:**  
Printing inside the loop shows intermediate values, not the final total.

**Fixed Code:**

```python
# Print total after loop completes
prices = [10, 20, 30, 40]
total = 0

for price in prices:
    total += price

print(f"Total: {total}")  # Correct: prints final total
# Output: Total: 100
```

**Why This Works:**  
Moving `print()` outside the loop waits until all values are accumulated before displaying the result.

---

## Practice Exercises

**Exercise 1: Calculate Product Price Total**

You have a list of prices: `[12.99, 8.50, 15.00, 22.75]`. Write a loop that calculates the total cost and prints each price with a running subtotal.

<details>
<summary>Solution</summary>

```python
# Calculate shopping cart total with running subtotal
prices = [12.99, 8.50, 15.00, 22.75]
total = 0

for price in prices:
    total += price
    print(f"Item: ${price:.2f} - Subtotal: ${total:.2f}")

print(f"Final total: ${total:.2f}")
# Output: Item: $12.99 - Subtotal: $12.99
# Output: Item: $8.50 - Subtotal: $21.49
# Output: Item: $15.00 - Subtotal: $36.49
# Output: Item: $22.75 - Subtotal: $59.24
# Output: Final total: $59.24
```

**Explanation:** This solution accumulates the running total inside the loop and displays both the individual price and current subtotal. The `:.2f` format specifier displays exactly 2 decimal places.

</details>

**Exercise 2: Find Maximum Value**

Given `numbers = [23, 45, 12, 67, 34, 89, 15]`, write a loop that finds and prints the largest number without using the `max()` function.

<details>
<summary>Solution</summary>

```python
# Find maximum value by comparing each item
numbers = [23, 45, 12, 67, 34, 89, 15]
max_value = numbers[0]  # Start with first value

for num in numbers:
    if num > max_value:
        max_value = num  # Update if we find a larger value

print(f"Maximum value: {max_value}")
# Output: Maximum value: 89
```

**Explanation:** Initialize `max_value` with the first item, then compare each subsequent value. Update `max_value` only when you find a larger number. This pattern works for finding minimum, maximum, or any extremal value.

</details>

**Exercise 3: Count Specific Items**

Given `grades = ["A", "B", "A", "C", "A", "B", "D", "A"]`, count how many times "A" appears using a loop.

<details>
<summary>Solution</summary>

```python
# Count occurrences of a specific grade
grades = ["A", "B", "A", "C", "A", "B", "D", "A"]
count = 0
target = "A"

for grade in grades:
    if grade == target:
        count += 1

print(f"Number of {target} grades: {count}")
# Output: Number of A grades: 4
```

**Explanation:** Initialize a counter at zero, then increment it each time you find a match. This pattern works for counting any specific value in a list.

</details>

**Exercise 4: Create Filtered List**

Given `temps = [15, 22, 18, 30, 25, 12, 28]`, create a new list containing only temperatures at or above 20 degrees.

<details>
<summary>Solution</summary>

```python
# Filter temperatures based on threshold
temps = [15, 22, 18, 30, 25, 12, 28]
warm_temps = []
threshold = 20

for temp in temps:
    if temp >= threshold:
        warm_temps.append(temp)

print(f"Original temps: {temps}")
# Output: Original temps: [15, 22, 18, 30, 25, 12, 28]

print(f"Temps >= {threshold}°C: {warm_temps}")
# Output: Temps >= 20°C: [22, 30, 25, 28]
```

**Explanation:** Create an empty list before the loop, then append items that meet your criteria. This filtering pattern builds a new list without modifying the original.

</details>

**Exercise 5: Index-Based Comparison**

Given `scores = [85, 92, 78, 92, 88]`, use an index loop to print each score with its position number (starting from 1) and mark the highest score with "★ BEST".

<details>
<summary>Solution</summary>

```python
# Display scores with position and mark the best
scores = [85, 92, 78, 92, 88]
max_score = max(scores)  # Find highest score first

for i in range(len(scores)):
    score = scores[i]
    position = i + 1  # Human-friendly numbering
    
    if score == max_score:
        print(f"#{position}: {score} ★ BEST")
    else:
        print(f"#{position}: {score}")
# Output: #1: 85
# Output: #2: 92 ★ BEST
# Output: #3: 78
# Output: #4: 92 ★ BEST
# Output: #5: 88
```

**Explanation:** Find the maximum value before looping, then use index-based iteration to display position numbers. The guard pattern marks any score matching the maximum. Note that both 92s get marked because they tie for best.

</details>

---

## Key Takeaways

✅ **Value loops access items directly** - Use `for item in list:` when you only need values, not positions  
✅ **Index loops provide position control** - Use `for i in range(len(list)):` when you need to know where items are  
✅ **Initialize accumulators before loops** - Create variables like `total = 0` outside the loop, update inside  
✅ **Guard patterns enable selective processing** - Use `if` conditions inside loops to act on specific positions  
✅ **Membership tests are efficient** - Use `in` operator instead of writing manual search loops  
✅ **Never modify lists during iteration** - Build new lists instead to avoid skipped items and index errors  
✅ **Print results after loops complete** - Unless you want to see intermediate values, move print statements outside loops

**Remember:** Value loops are for "what," index loops are for "where." Choose your iteration style based on whether you need positions or just the data itself.

---

**Last Updated:** November 6, 2025
