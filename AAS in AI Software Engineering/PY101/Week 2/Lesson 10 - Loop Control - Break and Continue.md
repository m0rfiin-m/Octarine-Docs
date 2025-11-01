# Loop Control: Break and Continue

**Date:** October 29, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 2, Lesson 10

## What You'll Learn

This lesson covers two essential loop control keywords in Python: `break` and `continue`. You'll learn how to exit loops early with `break`, skip specific iterations with `continue`, understand when to use each statement, and apply both to solve common programming patterns like searches, filtering, and validation.

---

## Loop Control Overview

Python provides two keywords that give you fine-grained control over loop execution beyond the standard condition checks:

**`break`:** Exit the loop immediately and permanently.

**`continue`:** Skip the rest of the current iteration and move to the next one.

### Why Loop Control Matters

**Early Exit:** Stop processing when you've found what you need (search patterns).

**Filtering:** Skip unwanted values without nested conditionals (cleaner code).

**Efficiency:** Avoid unnecessary iterations once conditions are met.

**Validation:** Handle invalid input without complex logic structures.

---

## The `break` Statement

The `break` statement terminates the loop immediately, regardless of the loop's condition. Execution continues at the first line after the loop.

### Core Concept

**What It Does:** Immediately exits the current loop (innermost loop if nested).

**Where It Goes:** Almost always inside an `if` statement.

**Effect:** The loop ends, and Python continues with the code after the loop.

**Analogy:** Emergency exit that gets you out of the loop right now.

### Basic Syntax

```python
for item in collection:
    if condition:
        break  # Exit loop immediately
    # Rest of loop body
```

### Example 1: Basic Break in For Loop

```python
for i in range(10):
    print(i)
    if i == 5:
        break
```

**Output:**
```
0
1
2
3
4
5
```

**Analysis:** Loop prints 0 through 5, then breaks when `i == 5`. Numbers 6-9 never print.

### Example 2: Breaking Out of While Loop

```python
while True:
    num = int(input("Enter a number: "))
    if num < 0:
        break  # Exit when negative number entered
    print(f"You entered: {num}")

print("Loop ended!")
```

**Example Session:**
```
Enter a number: 5
You entered: 5
Enter a number: 10
You entered: 10
Enter a number: -1
Loop ended!
```

**Key Point:** `while True` creates an infinite loop. `break` provides the only exit path.

### Example 3: Search Pattern

```python
names = ["Alice", "Bob", "Charlie", "Diana", "Eve"]
target = "Charlie"
found = False

for name in names:
    if name == target:
        print(f"Found {target}!")
        found = True
        break

if not found:
    print(f"{target} not found")
```

**Output:**
```
Found Charlie!
```

**Efficiency:** Once "Charlie" is found, loop stops. No need to check "Diana" or "Eve".

### Example 4: Password Validator with Max Attempts

```python
max_attempts = 3
attempts = 0

while attempts < max_attempts:
    password = input("Enter password: ")
    
    if password == "secret123":
        print("Access granted!")
        break
    
    attempts += 1
    if attempts < max_attempts:
        print(f"Incorrect. {max_attempts - attempts} attempts remaining.")

if attempts == max_attempts:
    print("Account locked.")
```

**Behavior:**
- Correct password: Breaks out immediately, "Access granted"
- Wrong password: Continues until max attempts, then "Account locked"

### When to Use `break`

**Search Operations:**
```python
# Find first even number
for num in [1, 3, 5, 8, 9, 10]:
    if num % 2 == 0:
        print(f"First even: {num}")
        break
# Output: First even: 8
```

**User Input Validation:**
```python
while True:
    age = int(input("Enter age: "))
    if 0 < age < 120:
        break  # Valid input, exit loop
    print("Invalid age")
```

**Early Termination:**
```python
# Stop processing when threshold reached
total = 0
for i in range(1, 100):
    total += i
    if total > 1000:
        print(f"Stopped at {i}, total: {total}")
        break
```

**Sentinel Values:**
```python
while True:
    command = input("Enter command: ")
    if command == "quit":
        break
    print(f"Processing: {command}")
```

---

## The `continue` Statement

The `continue` statement skips the rest of the current iteration and immediately jumps to the next iteration of the loop.

### Core Concept

**What It Does:** Skips remaining code in current iteration, moves to next loop cycle.

**Where It Goes:** Usually inside an `if` statement.

**Effect:** Current iteration ends early, but the loop continues running.

**Analogy:** "Skip this turn" card that moves you to the next round.

### Basic Syntax

```python
for item in collection:
    if condition:
        continue  # Skip rest of this iteration
    # This code is skipped when continue executes
    process(item)
```

### Example 1: Printing Odd Numbers

```python
for i in range(10):
    if i % 2 == 0:
        continue  # Skip even numbers
    print(i)
```

**Output:**
```
1
3
5
7
9
```

**How It Works:**
- When `i` is even (0, 2, 4, 6, 8), `continue` skips the `print()` statement
- When `i` is odd (1, 3, 5, 7, 9), no `continue` is hit, so `print()` executes

### Example 2: Filtering Invalid Input

```python
numbers = [5, -2, 10, 0, -7, 15, 3]

for num in numbers:
    if num <= 0:
        continue  # Skip non-positive numbers
    print(f"Processing: {num}")
```

**Output:**
```
Processing: 5
Processing: 10
Processing: 15
Processing: 3
```

**Analysis:** Negative numbers and zero are skipped. Only positive numbers are processed.

### Example 3: Skipping Certain Values

```python
for i in range(1, 11):
    if i == 5:
        continue  # Skip 5
    print(i)
```

**Output:**
```
1
2
3
4
6
7
8
9
10
```

**Key Point:** Number 5 is skipped, but the loop continues through all other values.

### Example 4: Processing with Exceptions

```python
words = ["hello", "", "world", "", "python"]

for word in words:
    if word == "":
        continue  # Skip empty strings
    print(word.upper())
```

**Output:**
```
HELLO
WORLD
PYTHON
```

### Example 5: Summing Only Multiples

```python
total = 0

for i in range(1, 21):
    if i % 3 != 0:
        continue  # Skip if not divisible by 3
    total += i

print(f"Sum of multiples of 3: {total}")
# Output: Sum of multiples of 3: 63
```

**Numbers Added:** 3 + 6 + 9 + 12 + 15 + 18 = 63

### When to Use `continue`

**Filtering:**
```python
# Process only valid items
for item in items:
    if not is_valid(item):
        continue
    process(item)
```

**Skipping Exceptions:**
```python
# Skip specific values
for num in numbers:
    if num == 0:
        continue  # Avoid division by zero
    result = 100 / num
    print(result)
```

**Conditional Processing:**
```python
# Only process items meeting criteria
for student in students:
    if student.grade < 70:
        continue  # Skip failing students
    print(f"{student.name} passed")
```

**Avoiding Nested Ifs:**
```python
# Without continue (nested)
for i in range(10):
    if i % 2 == 0:
        if i % 3 == 0:
            print(i)

# With continue (flatter)
for i in range(10):
    if i % 2 != 0:
        continue
    if i % 3 != 0:
        continue
    print(i)
```

---

## Break vs Continue: Side by Side

Understanding when to use each statement is crucial for writing clear, efficient code.

### Comparison Table

| Feature | `break` | `continue` |
|---------|---------|------------|
| **Action** | Exits loop completely | Skips to next iteration |
| **Loop Status** | Terminated | Continues running |
| **Use Case** | Found target, stop searching | Skip invalid items, keep processing |
| **Execution After** | Code after loop | Next loop iteration |
| **Condition Check** | Not evaluated again | Evaluated again for next iteration |

### Visual Comparison

**Using `break`:**
```python
for i in range(5):
    print(f"Start of iteration {i}")
    if i == 2:
        print("Breaking!")
        break
    print(f"End of iteration {i}")
print("After loop")
```

**Output:**
```
Start of iteration 0
End of iteration 0
Start of iteration 1
End of iteration 1
Start of iteration 2
Breaking!
After loop
```

**Using `continue`:**
```python
for i in range(5):
    print(f"Start of iteration {i}")
    if i == 2:
        print("Continuing!")
        continue
    print(f"End of iteration {i}")
print("After loop")
```

**Output:**
```
Start of iteration 0
End of iteration 0
Start of iteration 1
End of iteration 1
Start of iteration 2
Continuing!
Start of iteration 3
End of iteration 3
Start of iteration 4
End of iteration 4
After loop
```

**Key Difference:** `break` stops the loop entirely at iteration 2. `continue` skips the rest of iteration 2 but continues with iterations 3 and 4.

### Decision Guide

**Use `break` when:**
- You've found what you're looking for
- A critical condition is met (error, limit reached)
- No need to process remaining items
- Implementing search or validation with exit condition

**Use `continue` when:**
- Skipping certain values but processing others
- Filtering out unwanted items
- Avoiding nested conditionals
- All items should be checked, but some skipped

---

## Common Patterns and Examples

### Pattern 1: Search and Stop

```python
# Find first number divisible by 7
for i in range(1, 51):
    if i % 7 == 0:
        print(f"First multiple of 7: {i}")
        break
# Output: First multiple of 7: 7
```

### Pattern 2: Filter and Process

```python
# Sum only odd numbers under 31
total = 0
for i in range(31):
    if i % 2 == 0:
        continue  # Skip even numbers
    total += i

print(f"Sum: {total}")
# Output: Sum: 225
```

**Calculation:** 1 + 3 + 5 + ... + 27 + 29 = 225

### Pattern 3: Input Validation Loop

```python
while True:
    value = input("Enter a positive number: ")
    
    if not value.isdigit():
        print("That's not a number!")
        continue
    
    num = int(value)
    if num <= 0:
        print("Number must be positive!")
        continue
    
    # Valid input
    break

print(f"You entered: {num}")
```

### Pattern 4: Menu System

```python
while True:
    print("\n1. Start Game")
    print("2. Options")
    print("3. Quit")
    
    choice = input("Select: ")
    
    if choice == "1":
        print("Starting game...")
        # Game logic here
    elif choice == "2":
        print("Opening options...")
        # Options logic here
    elif choice == "3":
        print("Goodbye!")
        break
    else:
        print("Invalid choice")
        continue
```

### Pattern 5: Processing with Skip Conditions

```python
# Process files, skip hidden files and errors
files = [".hidden", "doc1.txt", "bad_file", "doc2.txt", ".config"]

for filename in files:
    if filename.startswith("."):
        print(f"Skipping hidden file: {filename}")
        continue
    
    if filename == "bad_file":
        print(f"Error reading {filename}, skipping")
        continue
    
    print(f"Processing: {filename}")
```

**Output:**
```
Skipping hidden file: .hidden
Processing: doc1.txt
Error reading bad_file, skipping
Processing: doc2.txt
Skipping hidden file: .config
```

---

## Common Errors and Fixes

### Error 1: Using Break/Continue Outside Loop

```python
# Wrong: break not in a loop
x = 5
if x > 3:
    break  # SyntaxError: 'break' outside loop
```

**Fix:** Only use `break` and `continue` inside loops.

```python
# Correct
for i in range(10):
    if i > 3:
        break
```

### Error 2: Breaking Wrong Loop in Nested Loops

```python
# Break only exits innermost loop
for i in range(3):
    print(f"Outer loop: {i}")
    for j in range(3):
        print(f"  Inner loop: {j}")
        if j == 1:
            break  # Only breaks inner loop
```

**Output:**
```
Outer loop: 0
  Inner loop: 0
  Inner loop: 1
Outer loop: 1
  Inner loop: 0
  Inner loop: 1
Outer loop: 2
  Inner loop: 0
  Inner loop: 1
```

**Fix:** Use a flag variable to break outer loop.

```python
should_exit = False

for i in range(3):
    for j in range(3):
        if condition:
            should_exit = True
            break
    if should_exit:
        break
```

### Error 3: Forgetting to Update Loop Variable with Continue

```python
# Wrong: infinite loop with while and continue
n = 0
while n < 5:
    if n == 2:
        continue  # Skips n += 1, n stays 2 forever!
    print(n)
    n += 1
```

**Fix:** Update variable before `continue` or restructure logic.

```python
# Correct
n = 0
while n < 5:
    n += 1  # Update first
    if n == 2:
        continue
    print(n)
```

### Error 4: Unnecessary Use of Continue

```python
# Overcomplicated with continue
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)

# Simpler without continue
for i in range(10):
    if i % 2 != 0:
        print(i)
```

**Best Practice:** If the entire loop body is one action, an `if` without `continue` is clearer.

---

## Practice Exercises

### Exercise 1: First Even Number

Find and print the first even number in the range 1 to 20, then stop.

<details>
<summary>Solution</summary>

```python
for i in range(1, 21):
    if i % 2 == 0:
        print(f"First even number: {i}")
        break
# Output: First even number: 2
```
</details>

### Exercise 2: Skip Multiples of 5

Print numbers 1 to 20, but skip any number divisible by 5.

<details>
<summary>Solution</summary>

```python
for i in range(1, 21):
    if i % 5 == 0:
        continue
    print(i)
```

**Output:**
```
1
2
3
4
6
7
8
9
11
12
13
14
16
17
18
19
```
</details>

### Exercise 3: Sum Until Threshold

Add numbers starting from 1 until the sum exceeds 100, then stop and print the sum.

<details>
<summary>Solution</summary>

```python
total = 0
n = 1

while True:
    total += n
    if total > 100:
        break
    n += 1

print(f"Sum: {total}, stopped at n={n}")
# Output: Sum: 105, stopped at n=14
```
</details>

### Exercise 4: Skip Negatives

Calculate the sum of numbers in the list, but skip negative numbers.

```python
numbers = [5, -2, 10, -7, 15, 3, -1, 8]
```

<details>
<summary>Solution</summary>

```python
numbers = [5, -2, 10, -7, 15, 3, -1, 8]
total = 0

for num in numbers:
    if num < 0:
        continue
    total += num

print(f"Sum: {total}")
# Output: Sum: 41
```

**Calculation:** 5 + 10 + 15 + 3 + 8 = 41
</details>

### Exercise 5: Password Checker

Create a login system that allows 3 attempts. Break on correct password, continue on incorrect.

<details>
<summary>Solution</summary>

```python
correct_password = "python123"
max_attempts = 3

for attempt in range(1, max_attempts + 1):
    password = input(f"Attempt {attempt}: Enter password: ")
    
    if password == correct_password:
        print("Access granted!")
        break
    
    if attempt < max_attempts:
        print("Incorrect. Try again.")
    else:
        print("Account locked.")
```
</details>

### Exercise 6: Print Non-Vowels

Print all letters in a word except vowels.

<details>
<summary>Solution</summary>

```python
word = "programming"
vowels = "aeiou"

for letter in word:
    if letter in vowels:
        continue
    print(letter, end="")
# Output: prgrmmng
```
</details>

### Exercise 7: Find Target in List

Search for a specific value in a list. Print "Found" and stop if found.

```python
numbers = [3, 7, 12, 5, 19, 8, 15]
target = 19
```

<details>
<summary>Solution</summary>

```python
numbers = [3, 7, 12, 5, 19, 8, 15]
target = 19
found = False

for num in numbers:
    if num == target:
        print(f"Found {target}!")
        found = True
        break

if not found:
    print(f"{target} not found")
# Output: Found 19!
```
</details>

### Exercise 8: Skip Range

Print numbers 1 to 30, but skip the range 10-20 (inclusive).

<details>
<summary>Solution</summary>

```python
for i in range(1, 31):
    if 10 <= i <= 20:
        continue
    print(i, end=" ")
# Output: 1 2 3 4 5 6 7 8 9 21 22 23 24 25 26 27 28 29 30
```
</details>

---

## Real-World Applications

### Data Validation

```python
def validate_inputs(data):
    """Process only valid data entries."""
    for entry in data:
        if entry is None:
            continue  # Skip null entries
        
        if not isinstance(entry, int):
            continue  # Skip non-integers
        
        if entry < 0:
            continue  # Skip negative values
        
        process_data(entry)
```

### File Processing

```python
def process_files(filenames):
    """Process files until error encountered."""
    for filename in filenames:
        try:
            with open(filename) as f:
                content = f.read()
                process(content)
        except FileNotFoundError:
            print(f"File not found: {filename}")
            break  # Stop on first missing file
        except PermissionError:
            print(f"Cannot read: {filename}")
            continue  # Skip and try next file
```

### Game Loop

```python
def game_loop():
    """Main game loop with quit condition."""
    while True:
        action = get_player_action()
        
        if action == "quit":
            print("Thanks for playing!")
            break
        
        if not is_valid_action(action):
            print("Invalid action!")
            continue
        
        execute_action(action)
        update_game_state()
```

### User Menu

```python
def display_menu():
    """Interactive menu system."""
    while True:
        print("\nMenu:")
        print("1. View Data")
        print("2. Add Entry")
        print("3. Exit")
        
        choice = input("Choose option: ")
        
        if choice == "1":
            view_data()
        elif choice == "2":
            add_entry()
        elif choice == "3":
            break
        else:
            print("Invalid option")
            continue
```

---

## Key Takeaways

✅ **`break` exits the loop immediately** - No more iterations, execution continues after loop  
✅ **`continue` skips current iteration** - Moves to next iteration, loop keeps running  
✅ **Both require a loop context** - Using outside loops causes SyntaxError  
✅ **`break` for searches** - Stop when target is found or condition is met  
✅ **`continue` for filtering** - Skip unwanted values, process rest  
✅ **Affects only innermost loop** - In nested loops, only exits/skips current level  
✅ **Common with `if` statements** - Almost always used conditionally  
✅ **Watch for infinite loops** - With `continue` in `while` loops, ensure variable updates

**Remember:** Think of `break` as an emergency exit that gets you out of the loop entirely, and `continue` as a "skip" button that jumps to the next iteration. Choose `break` when you're done processing (found what you need), and choose `continue` when you want to skip specific items but keep processing others.

---

**Last Updated:** October 29, 2025
