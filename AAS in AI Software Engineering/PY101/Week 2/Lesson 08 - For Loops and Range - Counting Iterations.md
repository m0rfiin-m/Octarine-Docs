# For Loops and Range(): Counting Iterations

**Date:** October 29, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 2, Lesson 8

## What You'll Learn

This lesson covers the `for` loop with Python's `range()` function, teaching you how to control iteration counts precisely, count from custom starting points, skip values with step parameters, and use the accumulator pattern to build values incrementally.

---

## The `range()` Function Overview

The `range()` function generates sequences of numbers for iteration. Unlike looping through lists or strings, `range()` gives you precise control over how many times a loop executes and what values it generates.

### Why `range()` Matters

**Counting Operations:** Run code exactly N times without creating a list.

**Memory Efficient:** Generates numbers on demand instead of storing them all in memory.

**Flexible Control:** Start at any number, stop at any point, skip values with custom steps.

**Pattern Generation:** Create sequences for mathematical operations, indexing, and scheduling.

---

## Basic `range()`: `range(stop)`

The simplest form generates numbers from 0 up to (but not including) the stop value.

### Syntax

```python
range(stop)
```

**How It Works:**
- Starts counting at 0
- Stops before reaching the stop value
- Generates exactly `stop` numbers

### Example 1: Counting 0 to 4

```python
for i in range(5):
    print(i)
```

**Output:**
```
0
1
2
3
4
```

**Analysis:** `range(5)` generates 5 numbers: 0, 1, 2, 3, 4. The loop runs exactly 5 times.

### Example 2: Printing a Message Multiple Times

```python
for i in range(3):
    print("Hello, Python!")
```

**Output:**
```
Hello, Python!
Hello, Python!
Hello, Python!
```

**Key Point:** The variable `i` takes values 0, 1, 2, but we don't use it in the print statement. We only need `range(3)` to execute the loop 3 times.

### Example 3: Counting Iterations

```python
for i in range(8):
    print(f"Iteration {i}")
```

**Output:**
```
Iteration 0
Iteration 1
Iteration 2
Iteration 3
Iteration 4
Iteration 5
Iteration 6
Iteration 7
```

**Use Case:** Tracking which iteration you're on, useful for debugging and progress indicators.

### Mental Model: Zero-Based Counting

Python (like most programming languages) counts from 0. This means:
- First item is at position 0
- Second item is at position 1
- `range(5)` gives you positions 0-4 (5 total positions)

```
range(5) → [0, 1, 2, 3, 4]
           ↑           ↑
         start       stop-1
```

---

## Two-Parameter `range()`: `range(start, stop)`

Control where counting begins and ends by specifying both start and stop values.

### Syntax

```python
range(start, stop)
```

**How It Works:**
- Starts at `start` value
- Stops before reaching `stop` value
- Counts up by 1 each time

### Example 1: Counting 3 to 6

```python
for i in range(3, 7):
    print(i)
```

**Output:**
```
3
4
5
6
```

**Analysis:** Starts at 3, stops before 7. Generates numbers: 3, 4, 5, 6.

### Example 2: Countdown Timer (Partial)

```python
for i in range(10, 15):
    print(f"T-minus {i} seconds")
```

**Output:**
```
T-minus 10 seconds
T-minus 11 seconds
T-minus 12 seconds
T-minus 13 seconds
T-minus 14 seconds
```

### Example 3: Year Range

```python
for year in range(2020, 2025):
    print(f"Year: {year}")
```

**Output:**
```
Year: 2020
Year: 2021
Year: 2022
Year: 2023
Year: 2024
```

**Real-World Use:** Processing data for specific time periods, generating date sequences.

### Understanding Start and Stop

```
range(3, 7) → [3, 4, 5, 6]
              ↑        ↑
            start   stop-1
```

**Rule:** Start is included, stop is excluded.

**Why?** This makes math easier. `range(3, 7)` generates exactly `7 - 3 = 4` numbers.

---

## Three-Parameter `range()`: `range(start, stop, step)`

Add a step parameter to control how much the counter increases (or decreases) each iteration.

### Syntax

```python
range(start, stop, step)
```

**How It Works:**
- Starts at `start`
- Increments by `step` each time
- Stops before reaching `stop`

### Example 1: Even Numbers

```python
for i in range(2, 11, 2):
    print(i)
```

**Output:**
```
2
4
6
8
10
```

**Analysis:** Start at 2, increment by 2 each time, stop before 11. Generates: 2, 4, 6, 8, 10.

### Example 2: Odd Numbers

```python
for i in range(1, 12, 2):
    print(i)
```

**Output:**
```
1
3
5
7
9
11
```

**Analysis:** Start at 1, increment by 2, stop before 12. Generates all odd numbers from 1 to 11.

### Example 3: Counting by Fives

```python
for i in range(0, 26, 5):
    print(f"Count: {i}")
```

**Output:**
```
Count: 0
Count: 5
Count: 10
Count: 15
Count: 20
Count: 25
```

**Use Case:** Batch processing (process every 5th item), scheduling (every 5 minutes), score intervals.

### Example 4: Countdown with Step

```python
for i in range(10, 0, -1):
    print(f"T-minus {i}")
print("Liftoff!")
```

**Output:**
```
T-minus 10
T-minus 9
T-minus 8
T-minus 7
T-minus 6
T-minus 5
T-minus 4
T-minus 3
T-minus 2
T-minus 1
Liftoff!
```

**Key Point:** Negative step counts down. Start must be larger than stop.

### Step Parameter Rules

**Positive Step (counting up):**
- `start` must be less than `stop`
- Example: `range(0, 10, 2)` → 0, 2, 4, 6, 8

**Negative Step (counting down):**
- `start` must be greater than `stop`
- Example: `range(10, 0, -1)` → 10, 9, 8, 7, 6, 5, 4, 3, 2, 1

**Step Cannot Be Zero:**
```python
# This raises ValueError
for i in range(0, 10, 0):
    print(i)
# ValueError: range() arg 3 must not be zero
```

---

## The Accumulator Pattern

A fundamental programming pattern where you build up a value (accumulate) step-by-step inside a loop.

### Core Concept

1. **Initialize** a variable before the loop (usually to 0 or empty value)
2. **Update** that variable inside the loop (add, multiply, append, etc.)
3. **Use** the final accumulated value after the loop

### Pattern Template

```python
# Step 1: Initialize accumulator
accumulator = starting_value

# Step 2: Loop and update
for item in sequence:
    accumulator = accumulator + item  # or other operation

# Step 3: Use final result
print(accumulator)
```

### Example 1: Sum of Numbers 1 to 10

```python
total = 0  # Initialize accumulator

for i in range(1, 11):
    total += i  # Accumulate: add current number to total

print(f"Sum: {total}")
# Output: Sum: 55
```

**How It Works:**
```
Iteration 1: total = 0 + 1 = 1
Iteration 2: total = 1 + 2 = 3
Iteration 3: total = 3 + 3 = 6
Iteration 4: total = 6 + 4 = 10
Iteration 5: total = 10 + 5 = 15
Iteration 6: total = 15 + 6 = 21
Iteration 7: total = 21 + 7 = 28
Iteration 8: total = 28 + 8 = 36
Iteration 9: total = 36 + 9 = 45
Iteration 10: total = 45 + 10 = 55
```

### Example 2: Sum of Even Numbers

```python
total = 0

for i in range(2, 21, 2):
    total += i

print(f"Sum of even numbers 2-20: {total}")
# Output: Sum of even numbers 2-20: 110
```

**Step-by-Step:**
- Adds 2 + 4 + 6 + 8 + 10 + 12 + 14 + 16 + 18 + 20
- Final total: 110

### Example 3: Sum of Odd Numbers Below 50

```python
total = 0

for i in range(1, 51, 2):
    total += i

print(f"Sum of odd numbers below 50: {total}")
# Output: Sum of odd numbers below 50: 625
```

**Math Check:** Sum of first N odd numbers = N²
- 25 odd numbers from 1 to 49
- 25² = 625 ✓

### Example 4: Building a String

```python
message = ""  # Empty string accumulator

for i in range(1, 6):
    message += f"{i} "

print(message)
# Output: 1 2 3 4 5
```

**Use Case:** Constructing formatted output, building CSV rows, concatenating results.

### Example 5: Counting Specific Items

```python
count = 0

for i in range(1, 101):
    if i % 10 == 0:  # Numbers divisible by 10
        count += 1

print(f"Numbers divisible by 10 (1-100): {count}")
# Output: Numbers divisible by 10 (1-100): 10
```

**Analysis:** Counts 10, 20, 30, 40, 50, 60, 70, 80, 90, 100 = 10 numbers.

### Example 6: Product Accumulator

```python
product = 1  # Initialize to 1 (not 0!) for multiplication

for i in range(1, 6):
    product *= i

print(f"Factorial of 5: {product}")
# Output: Factorial of 5: 120
```

**Why Start at 1?** Multiplying by 0 would make everything 0. For multiplication, always initialize to 1.

**Calculation:** 1 × 2 × 3 × 4 × 5 = 120

---

## Common Patterns with `range()`

### Pattern 1: Repeat an Action N Times

```python
# Print message 5 times
for i in range(5):
    print("Processing...")
```

**When to Use:** Fixed number of repetitions, countdown timers, batch operations.

### Pattern 2: Generate Sequences

```python
# Multiples of 3
for i in range(0, 31, 3):
    print(i, end=" ")
# Output: 0 3 6 9 12 15 18 21 24 27 30
```

**When to Use:** Mathematical sequences, scheduling intervals, data sampling.

### Pattern 3: Index Iteration

```python
names = ["Alice", "Bob", "Charlie"]

for i in range(len(names)):
    print(f"{i}: {names[i]}")
```

**Output:**
```
0: Alice
1: Bob
2: Charlie
```

**When to Use:** Need both index and value, modifying list items, parallel list processing.

**Better Alternative:** Use `enumerate()` when you don't need to modify:
```python
for i, name in enumerate(names):
    print(f"{i}: {name}")
```

### Pattern 4: Reverse Iteration

```python
# Countdown from 5 to 1
for i in range(5, 0, -1):
    print(i)
```

**Output:**
```
5
4
3
2
1
```

**When to Use:** Countdown timers, processing in reverse order, decreasing values.

---

## Common Errors and Fixes

### Error 1: Off-By-One Mistakes

```python
# Wrong: Trying to get 1-10 inclusive
for i in range(1, 10):
    print(i)
# Output: 1 2 3 4 5 6 7 8 9 (missing 10!)
```

**Fix:** Remember stop is exclusive. Add 1 to your desired end value.

```python
# Correct
for i in range(1, 11):
    print(i)
# Output: 1 2 3 4 5 6 7 8 9 10
```

### Error 2: Forgetting to Initialize Accumulator

```python
# Wrong: total not defined
for i in range(1, 11):
    total += i  # NameError: name 'total' is not defined
```

**Fix:** Always initialize before the loop.

```python
# Correct
total = 0
for i in range(1, 11):
    total += i
```

### Error 3: Wrong Step Direction

```python
# Wrong: Trying to count down with positive step
for i in range(10, 0, 1):
    print(i)
# Output: (nothing - empty range)
```

**Why This Fails:** Starting at 10, incrementing by 1, trying to reach 0. Since 10 > 0 and we're counting up, the range is empty.

**Fix:** Use negative step for countdown.

```python
# Correct
for i in range(10, 0, -1):
    print(i)
# Output: 10 9 8 7 6 5 4 3 2 1
```

### Error 4: Step Value of Zero

```python
# Wrong: Step cannot be zero
for i in range(0, 10, 0):
    print(i)
# ValueError: range() arg 3 must not be zero
```

**Why?** Infinite loop potential. Python prevents this.

**Fix:** Use a non-zero step value.

### Error 5: Modifying Loop Variable Inside Loop

```python
# Bad Practice: Don't modify loop variable
for i in range(5):
    print(i)
    i += 10  # Has no effect on next iteration
```

**Output:**
```
0
1
2
3
4
```

**Explanation:** The loop variable `i` is reassigned at the start of each iteration. Modifying it inside the loop doesn't change the iteration sequence.

**Better Approach:** If you need custom iteration, use a while loop instead.

---

## Practice Exercises

### Exercise 1: Print First 10 Numbers

Print numbers 0 through 9.

<details>
<summary>Solution</summary>

```python
for i in range(10):
    print(i)
```

**Output:**
```
0
1
2
3
4
5
6
7
8
9
```
</details>

### Exercise 2: Count 5 to 15

Print numbers from 5 to 15 (inclusive).

<details>
<summary>Solution</summary>

```python
for i in range(5, 16):
    print(i)
```

**Output:**
```
5
6
7
8
9
10
11
12
13
14
15
```

**Key Point:** Use 16 as stop value to include 15.
</details>

### Exercise 3: Even Numbers 0 to 20

Print all even numbers from 0 to 20.

<details>
<summary>Solution</summary>

```python
for i in range(0, 21, 2):
    print(i)
```

**Output:**
```
0
2
4
6
8
10
12
14
16
18
20
```
</details>

### Exercise 4: Sum of First 100 Numbers

Calculate the sum of numbers 1 through 100.

<details>
<summary>Solution</summary>

```python
total = 0

for i in range(1, 101):
    total += i

print(f"Sum: {total}")
# Output: Sum: 5050
```

**Math Verification:** Formula for sum of 1 to N: N(N+1)/2
- 100(101)/2 = 5050 ✓
</details>

### Exercise 5: Countdown Timer

Create a countdown from 10 to 1, then print "Blast off!"

<details>
<summary>Solution</summary>

```python
for i in range(10, 0, -1):
    print(f"T-minus {i}")
print("Blast off!")
```

**Output:**
```
T-minus 10
T-minus 9
T-minus 8
T-minus 7
T-minus 6
T-minus 5
T-minus 4
T-minus 3
T-minus 2
T-minus 1
Blast off!
```
</details>

### Exercise 6: Multiples of 7

Print all multiples of 7 between 0 and 50.

<details>
<summary>Solution</summary>

```python
for i in range(0, 51, 7):
    print(i, end=" ")
# Output: 0 7 14 21 28 35 42 49
```

**Alternative Approach:**
```python
for i in range(8):  # 8 multiples: 0×7 through 7×7
    print(i * 7, end=" ")
# Output: 0 7 14 21 28 35 42 49
```
</details>

### Exercise 7: Sum of Squares

Calculate the sum of squares from 1² to 5² (1 + 4 + 9 + 16 + 25).

<details>
<summary>Solution</summary>

```python
total = 0

for i in range(1, 6):
    total += i ** 2

print(f"Sum of squares: {total}")
# Output: Sum of squares: 55
```

**Calculation:** 1 + 4 + 9 + 16 + 25 = 55
</details>

### Exercise 8: Build a String Pattern

Create a string with numbers 1-5 separated by dashes: "1-2-3-4-5"

<details>
<summary>Solution</summary>

```python
result = ""

for i in range(1, 6):
    result += str(i)
    if i < 5:  # Don't add dash after last number
        result += "-"

print(result)
# Output: 1-2-3-4-5
```

**Alternative (Cleaner):**
```python
numbers = [str(i) for i in range(1, 6)]
result = "-".join(numbers)
print(result)
# Output: 1-2-3-4-5
```
</details>

---

## Real-World Applications

### Progress Indicators

```python
total_files = 10

for i in range(1, total_files + 1):
    print(f"Processing file {i} of {total_files}...")
    # Simulate file processing
```

**Use Case:** Download managers, installation wizards, batch processors.

### Score Calculation

```python
scores = [85, 92, 78, 95, 88]
total = 0

for i in range(len(scores)):
    total += scores[i]

average = total / len(scores)
print(f"Average score: {average:.1f}")
# Output: Average score: 87.6
```

### Pagination

```python
items_per_page = 10
total_items = 47

# Calculate number of pages needed
num_pages = (total_items + items_per_page - 1) // items_per_page

for page in range(1, num_pages + 1):
    start = (page - 1) * items_per_page
    end = min(start + items_per_page, total_items)
    print(f"Page {page}: items {start+1} to {end}")
```

**Output:**
```
Page 1: items 1 to 10
Page 2: items 11 to 20
Page 3: items 21 to 30
Page 4: items 31 to 40
Page 5: items 41 to 47
```

### Scheduling Tasks

```python
print("Daily medication schedule:")

for hour in range(8, 21, 4):  # Every 4 hours from 8am to 8pm
    print(f"Take medication at {hour}:00")
```

**Output:**
```
Daily medication schedule:
Take medication at 8:00
Take medication at 12:00
Take medication at 16:00
Take medication at 20:00
```

---

## Comparing Loop Types

| Loop Type | When to Use | Example |
|-----------|-------------|---------|
| `for item in list` | Iterate through items | `for name in names:` |
| `for i in range(n)` | Repeat N times | `for i in range(5):` |
| `for i in range(start, stop)` | Custom number range | `for i in range(10, 20):` |
| `for i in range(start, stop, step)` | Skip values, count by N | `for i in range(0, 10, 2):` |
| `while condition` | Unknown iterations, complex conditions | `while game_running:` |

### Decision Matrix

**Use `for item in list` when:**
- Processing each item in a collection
- Don't need index positions
- Focus is on the items themselves

**Use `range()` when:**
- Need exact iteration count
- Working with numerical sequences
- Need index positions
- Generating patterns

---

## Key Takeaways

✅ **`range(stop)` counts from 0** - Generates numbers 0 to stop-1  
✅ **`range(start, stop)` sets boundaries** - Control where counting begins and ends  
✅ **`range(start, stop, step)` skips values** - Count by any increment  
✅ **Stop value is exclusive** - `range(1, 5)` gives 1, 2, 3, 4 (not 5)  
✅ **Accumulator pattern builds values** - Initialize before loop, update inside, use after  
✅ **Negative step counts down** - Start must be greater than stop  
✅ **`range()` is memory efficient** - Generates values on demand, doesn't store all in memory  
✅ **Use for precise iteration control** - When you know exactly how many times to loop

**Remember:** The stop value in `range()` is always exclusive. When you want numbers 1 through 10, use `range(1, 11)`. Think "stop before this number" and you'll avoid off-by-one errors.

---

**Last Updated:** October 29, 2025
