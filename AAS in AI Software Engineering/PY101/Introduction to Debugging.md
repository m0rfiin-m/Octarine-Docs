# Introduction to Debugging

**Date:** October 25, 2025  
**Course:** PY101 - Introduction to Python

## What is Debugging?

Debugging is the systematic process of finding and fixing mistakes (bugs) in your code. Think of it like being a detective investigating why something isn't working as expected.

**Real-World Analogy:**  
Imagine a flashlight that won't turn on. Debugging is checking each component step-by-step: Are the batteries installed correctly? Is the bulb working? Is the switch functioning? You isolate each part until you find what's broken, then fix it.

### Types of Bugs

**1. Crash Errors (Tracebacks)**  
These bugs stop your program completely. Python tells you exactly where the problem occurred.

```python
# NameError: Using a variable that doesn't exist
print(my_name)  # Crashes if my_name was never defined

# ZeroDivisionError: Dividing by zero
result = 10 / 0  # Crashes immediately
```

**2. Logical Errors (Silent Bugs)**  
The program runs successfully but produces incorrect results. These are harder to catch because Python won't warn you. The code is valid, but the logic is wrong.

```python
# This runs without crashing, but gives the wrong answer
def calculate_average(a, b):
    return a + b  # Should divide by 2, but doesn't

print(calculate_average(10, 20))  # Outputs: 30 (Expected: 15)
```

Logical errors are what we'll focus on because they require detective work to find.

---

## Core Debugging Technique: The `print()` Statement

The most powerful debugging tool is the humble `print()` statement. It lets you "see inside" your code while it runs.

**The Strategy: Trace the Data**  
Add temporary `print()` statements to display variable values at different points in your code. This reveals exactly where the logic breaks down.

### The 4-Step Debugging Process

**1. Observe the Problem**  
Run your code and identify the incorrect output.

```python
result = add_three_numbers(3, 4, 5)
print(result)  # Outputs: 5 (Expected: 12)
```

**2. Add Print Statements**  
Insert `print()` calls to trace the variables you suspect are causing issues.

```python
def add_three_numbers(a, b, c):
    total = 0
    print("Starting total:", total)  # Track initial value
    total = a
    print("After adding a:", total)  # Track after first operation
    # ... continue tracking
```

**3. Find and Fix**  
Run the code again. Read the debug output to pinpoint the exact line where values deviate from expectations. Fix that specific line.

**4. Clean Up**  
Once the code works correctly, remove or comment out your debug `print()` statements to keep the final code clean.

```python
# Remove these after debugging:
# print("Starting total:", total)
# print("After adding a:", total)
```

---

## Example 1: The Addition Bug

### 🐞 The Broken Code

**Goal:** Add three numbers together.  
**Problem:** The code overwrites the `total` variable instead of accumulating values.

```python
def add_three_numbers(a, b, c):
    total = 0   # Start at 0
    total = a   # Now total = 3 (overwrites 0)
    total = b   # Now total = 4 (overwrites 3)
    total = c   # Now total = 5 (overwrites 4)
    return total

result = add_three_numbers(3, 4, 5)
print("The total is:", result)

# Output: The total is: 5
# Expected: The total is: 12
```

**Why It's Wrong:**  
Each line replaces `total` with a new value instead of adding to it. We're using assignment (`=`) when we should be using addition (`+=`).

### 🛠️ Debugging with Print Statements

Let's trace `total` at each step to see what's happening:

```python
def add_three_numbers(a, b, c):
    total = 0
    print("1. total starts at:", total)
    
    total = a
    print("2. After total = a:", total)
    
    total = b
    print("3. After total = b:", total)
    
    total = c
    print("4. After total = c:", total)
    
    return total

result = add_three_numbers(3, 4, 5)
print("Final result:", result)

# --- Debug Output ---
# 1. total starts at: 0
# 2. After total = a: 3
# 3. After total = b: 4
# 4. After total = c: 5
# Final result: 5
```

**The Discovery:**  
The debug output shows that `total` never accumulates. Each assignment replaces the previous value. The variable isn't growing, it's just being overwritten.

### ✅ The Fixed Code

```python
def add_three_numbers(a, b, c):
    # Fix: Add all three numbers in one operation
    total = a + b + c
    return total

result = add_three_numbers(3, 4, 5)
print("The total is:", result)

# Output: The total is: 12 ✓
```

**Alternative Fix (If you need to build up the total):**

```python
def add_three_numbers(a, b, c):
    total = 0
    total += a  # Same as: total = total + a
    total += b  # Same as: total = total + b
    total += c  # Same as: total = total + c
    return total

result = add_three_numbers(3, 4, 5)
print("The total is:", result)

# Output: The total is: 12 ✓
```

---

## Example 2: The Restaurant Bill Bug

### 🐞 The Broken Code

**Goal:** Calculate a restaurant bill including a tip.  
**Problem:** The code forgets to add the original price to the total.

```python
def cafe_total(price, tip):
    tip_amount = price * tip  # Calculate tip: 10 * 0.2 = 2.0
    total = 0                  # Start total at 0
    total = tip_amount         # Set total to 2.0
    return total               # Return 2.0

bill = cafe_total(10, 0.2)
print("The total is:", bill)

# Output: The total is: 2.0
# Expected: The total is: 12.0 (10 + 2)
```

**Why It's Wrong:**  
We calculate the tip correctly, but then only assign the tip to `total`. We never add the original price.

### 🛠️ Debugging with Print Statements

```python
def cafe_total(price, tip):
    tip_amount = price * tip
    print("Tip amount calculated:", tip_amount)
    
    total = 0
    total = tip_amount
    print("Total is now:", total)
    print("Original price was:", price)
    
    return total

bill = cafe_total(10, 0.2)
print("Final bill:", bill)

# --- Debug Output ---
# Tip amount calculated: 2.0
# Total is now: 2.0
# Original price was: 10
# Final bill: 2.0
```

**The Discovery:**  
The debug output reveals that `total` only holds the tip amount. The original price (10) is never added to it. We're missing a crucial addition step.

### ✅ The Fixed Code

```python
def cafe_total(price, tip):
    tip_amount = price * tip
    
    # Fix: Add the price AND the tip together
    total = price + tip_amount
    
    return total

bill = cafe_total(10, 0.2)
print(bill)

# Output: 12.0 ✓
```

**Alternative Approach (One-liner):**

```python
def cafe_total(price, tip):
    # Calculate and return in one step
    return price + (price * tip)

bill = cafe_total(10, 0.2)
print(bill)

# Output: 12.0 ✓
```

---

## Bonus: Understanding TypeError

While debugging, you might fix one bug and uncover another. This is normal.

### The Bug

```python
bill = 12.0
print("Banner: $", bill * "*")

# Error: TypeError: can't multiply sequence by non-int of type 'float'
```

### Why It Crashes

Python lets you repeat strings using multiplication, but only with integers:

```python
# This works (integer multiplication):
print("*" * 3)  # Output: ***

# This doesn't work (float multiplication):
print("*" * 3.5)  # TypeError!
print("*" * 12.0)  # TypeError! (even though 12.0 equals 12)
```

**The Rule:** String multiplication requires whole numbers (integers), not decimals (floats).

### The Fix

Convert the float to an integer if you need string repetition:

```python
bill = 12.0

# Option 1: Convert to integer
print("Banner: $", "*" * int(bill))
# Output: Banner: $ ************

# Option 2: Just print the bill (simpler)
print("Your bill:", bill)
# Output: Your bill: 12.0
```

---

## Debugging Best Practices

**1. Debug Incrementally**  
Don't write 100 lines of code and then debug. Test small sections as you go.

```python
# Bad: Write everything first, debug later
def complex_calculation(a, b, c, d, e):
    result = ((a + b) * c - d) / e
    return result

# Good: Test each step
def complex_calculation(a, b, c, d, e):
    step1 = a + b
    print("After addition:", step1)
    
    step2 = step1 * c
    print("After multiplication:", step2)
    
    step3 = step2 - d
    print("After subtraction:", step3)
    
    result = step3 / e
    print("Final result:", result)
    
    return result
```

**2. Use Descriptive Print Messages**

```python
# Bad: Unclear what you're printing
print(x)
print(y)

# Good: Clear labels
print("User input:", x)
print("Calculated total:", y)
```

**3. Print Before and After**  
Show values before and after operations to catch where things go wrong.

```python
def discount_price(price, discount):
    print("Original price:", price)
    print("Discount rate:", discount)
    
    discount_amount = price * discount
    print("Discount amount:", discount_amount)
    
    final_price = price - discount_amount
    print("Final price:", final_price)
    
    return final_price
```

**4. Comment Out, Don't Delete**  
Keep debug prints commented out for future reference.

```python
def calculate_tip(bill, tip_rate):
    # print("DEBUG: bill =", bill, "tip_rate =", tip_rate)
    tip = bill * tip_rate
    # print("DEBUG: calculated tip =", tip)
    return tip
```

---

## Practice Exercise

Try debugging this function yourself:

```python
def calculate_average(a, b, c):
    total = a + b
    average = total / 3
    return average

result = calculate_average(10, 20, 30)
print("Average:", result)

# Output: Average: 10.0
# Expected: Average: 20.0
```

**Your Task:**  
1. Add print statements to trace `total` and `average`
2. Find where the logic breaks
3. Fix the bug
4. Clean up your debug prints

**Solution:**

<details>
<summary>Click to reveal solution</summary>

```python
def calculate_average(a, b, c):
    total = a + b
    print("Total after adding a and b:", total)  # Debug: Shows 30
    print("We forgot to add c:", c)              # Debug: c is never added
    
    average = total / 3
    print("Average:", average)                   # Debug: 30 / 3 = 10
    
    return average

# The bug: We never added 'c' to total!

# Fixed version:
def calculate_average(a, b, c):
    total = a + b + c  # Fix: Add all three numbers
    average = total / 3
    return average

result = calculate_average(10, 20, 30)
print("Average:", result)
# Output: Average: 20.0 ✓
```

</details>

---

## Key Takeaways

✅ **Debugging is detective work** - You systematically track down where logic breaks  
✅ **Print statements are your X-ray vision** - They show what's happening inside your code  
✅ **Logical errors are silent** - The code runs but gives wrong answers  
✅ **Debug incrementally** - Test small sections instead of writing everything first  
✅ **Clean up after** - Remove or comment out debug prints in final code

**Remember:** Every programmer debugs constantly. Getting good at debugging makes you a better programmer than writing perfect code on the first try (which rarely happens anyway).

---

**Last Updated:** October 25, 2025