# While Loops: Repeating Until a Condition Changes

**Date:** October 29, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 2, Lesson 9

## What You'll Learn

This lesson introduces the `while` loop, a control structure that repeats code as long as a condition remains True. You'll learn the four essential parts of a `while` loop, understand when to use it instead of a `for` loop, recognize infinite loop dangers, and apply the accumulator pattern in uncertain iteration scenarios.

---

## What Is a `while` Loop?

A `while` loop repeats a block of code as long as a condition evaluates to True. Unlike `for` loops where you know the exact iteration count, `while` loops continue until a condition changes.

### Core Concept

**Decision Point:** At the start of each iteration, Python checks the condition.
- **True:** Execute the loop body, then check again
- **False:** Exit the loop and continue with code after it

### When to Use `while` Loops

**Use `while` when:**
- You don't know how many iterations you need in advance
- Repetition depends on user input or external conditions
- You need to continue until a specific state is reached
- The stopping point is determined by logic, not counting

**Examples:**
- "Keep asking until the user enters valid input"
- "Process data until the file ends"
- "Run the game until the player quits"
- "Search until you find the target"

---

## The Four Parts of a `while` Loop

Every properly functioning `while` loop requires these four components:

### 1. Initialization

Set up the variable(s) that control the loop before it starts.

```python
n = 0  # Initialize counter
```

**Purpose:** Establish the starting state for the condition to evaluate.

### 2. Condition

The boolean expression checked at the beginning of each iteration.

```python
while n < 3:  # Condition
```

**Purpose:** Determine whether to execute the loop body or exit.

### 3. Body

The code that executes repeatedly while the condition is True.

```python
    print(n)  # Body
```

**Purpose:** Perform the repeated action.

### 4. Update

Modify the variable(s) used in the condition to eventually make it False.

```python
    n += 1  # Update
```

**Purpose:** Progress toward the stopping condition to prevent infinite loops.

### Complete Example: Counting Up

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

**Output:**
```
0
1
2
```

**How It Works:**
```
Before loop: n = 0
Iteration 1: n < 3 is True (0 < 3) → print 0, n becomes 1
Iteration 2: n < 3 is True (1 < 3) → print 1, n becomes 2
Iteration 3: n < 3 is True (2 < 3) → print 2, n becomes 3
After iteration 3: n < 3 is False (3 < 3) → exit loop
```

---

## Counting Up with `while`

The most basic pattern: start at a number and count up until reaching a limit.

### Example 1: Count 0 to 4

```python
n = 0

while n <= 4:
    print(n)
    n += 1
```

**Output:**
```
0
1
2
3
4
```

**Key Point:** The condition `n <= 4` includes 4 in the output. Change to `n < 4` to exclude it.

### Example 2: Count from 10 to 15

```python
n = 10

while n <= 15:
    print(f"Number: {n}")
    n += 1
```

**Output:**
```
Number: 10
Number: 11
Number: 12
Number: 13
Number: 14
Number: 15
```

### Example 3: Repeat a Message

```python
count = 0

while count < 5:
    print("Processing...")
    count += 1

print("Done!")
```

**Output:**
```
Processing...
Processing...
Processing...
Processing...
Processing...
Done!
```

**Use Case:** Progress indicators, loading screens, retry mechanisms.

---

## Counting Down with `while`

Reverse the direction by starting high and decreasing until reaching a limit.

### Example 1: Countdown 5 to 0

```python
n = 5

while n >= 0:
    print(n)
    n -= 1
```

**Output:**
```
5
4
3
2
1
0
```

**Key Changes:**
- Initialize higher: `n = 5`
- Condition uses `>=`: `while n >= 0`
- Update decreases: `n -= 1`

### Example 2: Countdown with Message

```python
n = 10

while n > 0:
    print(f"T-minus {n}")
    n -= 1

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

**Note:** Using `n > 0` stops at 1, excluding 0 from the countdown.

### Example 3: Lives System in Games

```python
lives = 3

while lives > 0:
    print(f"You have {lives} lives remaining")
    lives -= 1
    # Game logic would go here

print("Game Over")
```

**Output:**
```
You have 3 lives remaining
You have 2 lives remaining
You have 1 lives remaining
Game Over
```

---

## The Accumulator Pattern with `while`

Build up values incrementally when you don't know the iteration count in advance.

### Pattern Structure

```python
# Initialize accumulator and control variable
accumulator = starting_value
control_variable = initial_value

# Loop until condition changes
while condition:
    # Update accumulator
    accumulator += value
    
    # Update control variable
    control_variable = new_value

# Use accumulated result
print(accumulator)
```

### Example 1: Sum of Numbers 1 to 5

```python
n = 1
total = 0

while n <= 5:
    total += n
    n += 1

print(f"Sum: {total}")
# Output: Sum: 15
```

**Calculation:** 1 + 2 + 3 + 4 + 5 = 15

### Example 2: Sum of Odd Numbers Below 20

```python
n = 1
total = 0

while n < 20:
    total += n  # Add current odd number
    n += 2      # Jump to next odd number

print(f"Sum: {total}")
# Output: Sum: 100
```

**How It Works:**
- Starts at 1 (first odd number)
- Adds each odd number to total
- Increments by 2 to get next odd number (1, 3, 5, 7, 9, 11, 13, 15, 17, 19)
- Stops when n reaches 21 (which is >= 20)

**Verification:** 1 + 3 + 5 + 7 + 9 + 11 + 13 + 15 + 17 + 19 = 100

### Example 3: Sum of Even Numbers Below 15

```python
n = 0
total = 0

while n < 15:
    total += n
    n += 2

print(f"Sum of even numbers: {total}")
# Output: Sum of even numbers: 56
```

**Numbers Added:** 0 + 2 + 4 + 6 + 8 + 10 + 12 + 14 = 56

### Example 4: Building a String

```python
n = 1
message = ""

while n <= 5:
    message += f"{n} "
    n += 1

print(message.strip())  # Remove trailing space
# Output: 1 2 3 4 5
```

### Example 5: Factorial Calculation

```python
n = 5
factorial = 1
current = 1

while current <= n:
    factorial *= current
    current += 1

print(f"Factorial of {n}: {factorial}")
# Output: Factorial of 5: 120
```

**Calculation:** 1 × 2 × 3 × 4 × 5 = 120

---

## The Danger of Infinite Loops

An infinite loop occurs when the condition never becomes False, causing the program to run forever.

### Common Cause: Missing Update

```python
# DANGER: This will run forever!
n = 0

while n < 3:
    print(n)
    # Missing: n += 1

# n stays 0, condition always True
```

**What Happens:**
```
0
0
0
0
0
(continues forever...)
```

**How to Stop:** Press `Ctrl + C` in your terminal or stop the program through your IDE.

### Example 2: Wrong Update Direction

```python
# DANGER: Infinite loop
n = 0

while n < 10:
    print(n)
    n -= 1  # Wrong direction! Makes n more negative

# Condition n < 10 stays True forever
```

### Example 3: Update Outside Loop

```python
# DANGER: Infinite loop
n = 0

while n < 5:
    print(n)
n += 1  # Wrong indentation - outside the loop!

# n never increases inside the loop
```

### How to Prevent Infinite Loops

**Check 1: Initialization**
- Is the control variable set before the loop?
- Does it start with a value that makes the condition work?

**Check 2: Condition**
- Can the condition eventually become False?
- Is the logic correct (`<` vs `<=`, `>` vs `>=`)?

**Check 3: Update**
- Is the update statement inside the loop body?
- Does it move the control variable toward the stopping condition?
- Is the direction correct (increment for counting up, decrement for counting down)?

**Check 4: Progress**
- Add print statements to track variable values
- Verify the control variable changes each iteration

### Debug Pattern

```python
n = 0
iterations = 0  # Safety counter

while n < 3 and iterations < 100:  # Add safety limit
    print(f"n = {n}, iteration = {iterations}")
    n += 1
    iterations += 1

if iterations >= 100:
    print("Warning: Hit safety limit!")
```

---

## For Loop vs While Loop

Understanding when to use each loop type is crucial for writing clean, readable code.

### Key Differences

| Feature | `for` Loop | `while` Loop |
|---------|-----------|--------------|
| **Iteration Count** | Known in advance | Unknown until condition changes |
| **Best For** | Fixed repetitions | Conditional repetitions |
| **Structure** | Automatic iteration | Manual control variable management |
| **Infinite Loop Risk** | Low (automatic) | Higher (manual update required) |
| **Readability** | Clearer for counting | Clearer for conditions |

### When to Use `for`

**Use `for` when you know:**
- Exact number of iterations
- Processing every item in a collection
- Counting within a specific range

**Examples:**

```python
# Print numbers 0 to 4 (you know it's 5 times)
for i in range(5):
    print(i)

# Process each item in a list
names = ["Alice", "Bob", "Charlie"]
for name in names:
    print(name)

# Generate multiplication table
for i in range(1, 11):
    print(f"7 x {i} = {7 * i}")
```

### When to Use `while`

**Use `while` when:**
- Repetition depends on a condition, not a count
- You don't know how many iterations you'll need
- Waiting for user input or external events
- Searching until finding a result

**Examples:**

```python
# Keep asking until valid input
password = ""
while password != "secret":
    password = input("Enter password: ")

# Process until reaching a threshold
total = 0
n = 1
while total < 100:
    total += n
    n += 1

# Game loop
game_running = True
while game_running:
    # Game logic
    user_choice = input("Continue? (y/n): ")
    if user_choice == "n":
        game_running = False
```

### Conversion Example

**Using `for`:**
```python
for i in range(5):
    print(i)
```

**Equivalent `while`:**
```python
i = 0
while i < 5:
    print(i)
    i += 1
```

**Observation:** The `for` loop is cleaner when you know the count. The `while` loop gives more control but requires manual management.

---

## Common Patterns with `while`

### Pattern 1: Sentinel-Controlled Loop

Continue until a specific value (sentinel) is encountered.

```python
user_input = ""

while user_input != "quit":
    user_input = input("Enter command (or 'quit' to exit): ")
    if user_input != "quit":
        print(f"You entered: {user_input}")

print("Goodbye!")
```

**Use Case:** Menu systems, data entry, command processors.

### Pattern 2: Condition-Based Accumulation

Keep adding until reaching a target.

```python
total = 0
n = 1

while total < 50:
    total += n
    n += 1

print(f"Stopped at n={n-1}, total={total}")
# Output: Stopped at n=10, total=55
```

**Analysis:** Adds 1+2+3+4+5+6+7+8+9+10 = 55, which is the first sum exceeding 50.

### Pattern 3: Validation Loop

Repeat until valid input is provided.

```python
age = -1

while age < 0 or age > 120:
    age = int(input("Enter your age (0-120): "))
    if age < 0 or age > 120:
        print("Invalid age. Try again.")

print(f"Age recorded: {age}")
```

### Pattern 4: Countdown Timer

```python
seconds = 10

while seconds > 0:
    print(f"Time remaining: {seconds} seconds")
    seconds -= 1
    # In real code, add: time.sleep(1)

print("Time's up!")
```

### Pattern 5: Search Pattern

```python
numbers = [5, 12, 8, 3, 19, 7]
target = 19
index = 0
found = False

while index < len(numbers) and not found:
    if numbers[index] == target:
        found = True
        print(f"Found {target} at index {index}")
    index += 1

if not found:
    print(f"{target} not found")
```

---

## Common Errors and Fixes

### Error 1: Uninitialized Variable

```python
# Wrong: n not initialized
while n < 5:  # NameError: name 'n' is not defined
    print(n)
    n += 1
```

**Fix:** Always initialize before the loop.

```python
# Correct
n = 0
while n < 5:
    print(n)
    n += 1
```

### Error 2: Condition Never Becomes False

```python
# Wrong: condition always True
n = 0
while n != 5:
    print(n)
    n += 2  # Goes 0, 2, 4, 6, 8... skips 5!
```

**Output:** 0, 2, 4, 6, 8, 10... (infinite)

**Fix:** Use condition that will eventually be satisfied.

```python
# Correct
n = 0
while n < 5:  # Will eventually be False when n >= 5
    print(n)
    n += 2
# Output: 0 2 4
```

### Error 3: Update Outside Loop

```python
# Wrong: indentation error
n = 0
while n < 3:
    print(n)
n += 1  # Outside loop - n never increases in loop
```

**Fix:** Indent update statement properly.

```python
# Correct
n = 0
while n < 3:
    print(n)
    n += 1  # Inside loop body
```

### Error 4: Wrong Comparison Operator

```python
# Wrong: wants 1-5 but uses wrong operator
n = 1
while n < 5:  # Stops before 5
    print(n)
    n += 1
# Output: 1 2 3 4 (missing 5)
```

**Fix:** Use `<=` to include the upper bound.

```python
# Correct
n = 1
while n <= 5:
    print(n)
    n += 1
# Output: 1 2 3 4 5
```

---

## Practice Exercises

### Exercise 1: Count 1 to 10

Write a `while` loop that prints numbers 1 through 10.

<details>
<summary>Solution</summary>

```python
n = 1

while n <= 10:
    print(n)
    n += 1
```

**Output:**
```
1
2
3
4
5
6
7
8
9
10
```
</details>

### Exercise 2: Countdown from 20 to 10

Create a countdown that prints numbers from 20 down to 10 (inclusive).

<details>
<summary>Solution</summary>

```python
n = 20

while n >= 10:
    print(n)
    n -= 1
```

**Output:**
```
20
19
18
17
16
15
14
13
12
11
10
```
</details>

### Exercise 3: Sum Until Threshold

Calculate how many numbers you need to add (starting from 1) to exceed 100.

<details>
<summary>Solution</summary>

```python
total = 0
n = 1

while total <= 100:
    total += n
    n += 1

print(f"Needed {n-1} numbers to exceed 100")
print(f"Final total: {total}")
```

**Output:**
```
Needed 14 numbers to exceed 100
Final total: 105
```

**Explanation:** 1+2+3+4+5+6+7+8+9+10+11+12+13+14 = 105
</details>

### Exercise 4: Even Numbers Below 30

Print all even numbers from 0 to 30 (exclusive) using a `while` loop.

<details>
<summary>Solution</summary>

```python
n = 0

while n < 30:
    print(n)
    n += 2
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
22
24
26
28
```
</details>

### Exercise 5: Password Validator

Create a simple password checker that keeps asking until the user enters "python123".

<details>
<summary>Solution</summary>

```python
password = ""

while password != "python123":
    password = input("Enter password: ")
    if password != "python123":
        print("Incorrect. Try again.")

print("Access granted!")
```

**Example Session:**
```
Enter password: hello
Incorrect. Try again.
Enter password: test
Incorrect. Try again.
Enter password: python123
Access granted!
```
</details>

### Exercise 6: Multiplication Table

Generate a multiplication table for 7 (from 7×1 to 7×10) using a `while` loop.

<details>
<summary>Solution</summary>

```python
n = 1

while n <= 10:
    print(f"7 x {n} = {7 * n}")
    n += 1
```

**Output:**
```
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
7 x 4 = 28
7 x 5 = 35
7 x 6 = 42
7 x 7 = 49
7 x 8 = 56
7 x 9 = 63
7 x 10 = 70
```
</details>

### Exercise 7: Sum of Multiples of 5

Calculate the sum of all multiples of 5 below 100.

<details>
<summary>Solution</summary>

```python
n = 0
total = 0

while n < 100:
    total += n
    n += 5

print(f"Sum: {total}")
# Output: Sum: 950
```

**Verification:** 0 + 5 + 10 + 15 + ... + 90 + 95 = 950
</details>

### Exercise 8: Factorial Calculator

Calculate the factorial of 6 (6! = 6 × 5 × 4 × 3 × 2 × 1) using a `while` loop.

<details>
<summary>Solution</summary>

```python
n = 6
factorial = 1
current = 1

while current <= n:
    factorial *= current
    current += 1

print(f"{n}! = {factorial}")
# Output: 6! = 720
```

**Calculation:** 1 × 2 × 3 × 4 × 5 × 6 = 720
</details>

---

## Real-World Applications

### User Authentication

```python
max_attempts = 3
attempts = 0
authenticated = False

while attempts < max_attempts and not authenticated:
    password = input("Enter password: ")
    if password == "secret123":
        authenticated = True
        print("Login successful!")
    else:
        attempts += 1
        remaining = max_attempts - attempts
        if remaining > 0:
            print(f"Incorrect. {remaining} attempts remaining.")

if not authenticated:
    print("Account locked. Too many failed attempts.")
```

### Data Processing Until End of File

```python
# Simulating reading lines from a file
lines = ["data1", "data2", "data3", "END"]
index = 0

while index < len(lines) and lines[index] != "END":
    print(f"Processing: {lines[index]}")
    index += 1

print("File processing complete")
```

### Game Score System

```python
score = 0
target_score = 100

while score < target_score:
    points = int(input("Points earned this round: "))
    score += points
    print(f"Current score: {score}")

print(f"You win! Final score: {score}")
```

### Network Retry Logic

```python
max_retries = 5
retries = 0
connected = False

while retries < max_retries and not connected:
    print(f"Attempting connection... (Attempt {retries + 1})")
    # Simulate connection attempt
    success = input("Connection successful? (y/n): ")
    
    if success == "y":
        connected = True
        print("Connected!")
    else:
        retries += 1
        if retries < max_retries:
            print("Retrying...")

if not connected:
    print("Connection failed after maximum retries")
```

---

## Key Takeaways

✅ **`while` loops repeat until a condition becomes False** - Use when iteration count is unknown  
✅ **Four parts required** - Initialization, condition, body, update  
✅ **Condition checked at start** - Loop may never execute if initially False  
✅ **Update inside the loop** - Must progress toward stopping condition  
✅ **Infinite loops are dangerous** - Always verify your update moves toward exit  
✅ **Choose `for` for known counts** - Use `while` for conditional repetition  
✅ **Accumulator pattern works with `while`** - Initialize before loop, update inside  
✅ **Add safety limits during development** - Prevent infinite loops while debugging

**Remember:** The most common `while` loop error is forgetting to update the control variable inside the loop. Always ask yourself: "Does this loop have a clear path to the exit condition?" If you can't trace how the condition will eventually become False, you likely have an infinite loop.

---

**Last Updated:** October 29, 2025
