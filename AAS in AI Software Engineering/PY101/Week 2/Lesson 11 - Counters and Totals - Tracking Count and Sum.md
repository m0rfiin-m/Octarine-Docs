# Counters and Totals: Tracking Count and Sum

**Date:** October 30, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 2, Lesson 11

## What You'll Learn

This lesson covers two fundamental programming patterns: counters (tracking how many times something happens) and totals (accumulating sums). You'll learn when to use each pattern, how to initialize them correctly, combine both in a single loop, and avoid common pitfalls like resetting values inside loops.

---

## The Core Idea

Two essential patterns for tracking data during iteration:

**Counter:** A variable that increments by a fixed amount (usually 1) each time a condition is met.

**Total (Accumulator):** A variable that adds changing values to itself during each iteration.

### Key Questions They Answer

**Counter answers:** "How many?"
- How many positive numbers?
- How many times did this condition occur?
- How many items match the criteria?

**Total answers:** "How much?"
- What's the sum of all values?
- What's the total amount?
- What's the accumulated result?

### Critical Rule: Initialize Before the Loop

Both patterns require initialization outside and before the loop. Initializing inside the loop resets the value every iteration, destroying your accumulated data.

**Wrong Approach:**
```python
# BAD: Resets total every iteration
for i in range(5):
    total = 0  # This resets to 0 each time!
    total += i

print(total)
# Output: 4 (only the last value)
```

**Why This Fails:**
```
Iteration 1: total = 0, then total = 0 + 0 = 0
Iteration 2: total = 0, then total = 0 + 1 = 1
Iteration 3: total = 0, then total = 0 + 2 = 2
Iteration 4: total = 0, then total = 0 + 3 = 3
Iteration 5: total = 0, then total = 0 + 4 = 4
Final: 4 (should be 10!)
```

**Correct Approach:**
```python
# GOOD: Initialize once, outside the loop
total = 0
for i in range(5):
    total += i

print(total)
# Output: 10 (0 + 1 + 2 + 3 + 4)
```

**Why This Works:**
```
Before loop: total = 0
Iteration 1: total = 0 + 0 = 0
Iteration 2: total = 0 + 1 = 1
Iteration 3: total = 1 + 2 = 3
Iteration 4: total = 3 + 3 = 6
Iteration 5: total = 6 + 4 = 10
Final: 10 ✓
```

---

## Using a Counter

A counter tracks occurrences. Initialize to 0, increment by 1 when the condition is met.

### The Counter Pattern

```python
# 1. Initialize counter before loop
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

### Example 1: Counting Multiples of 3

```python
# Count how many numbers 1-50 are divisible by 3
count = 0

for i in range(1, 51):
    if i % 3 == 0:
        count += 1

print(f"There are {count} multiples of 3.")
# Output: There are 16 multiples of 3.
```

**Numbers Counted:** 3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48 = 16 numbers

### Example 2: Counting Even Numbers

```python
numbers = [5, 12, 7, 8, 3, 14, 9, 20]
count = 0

for num in numbers:
    if num % 2 == 0:
        count += 1

print(f"Even numbers: {count}")
# Output: Even numbers: 4
```

**Even Numbers Found:** 12, 8, 14, 20

### Example 3: Counting Vowels in a String

```python
text = "Hello World"
vowels = "aeiouAEIOU"
count = 0

for letter in text:
    if letter in vowels:
        count += 1

print(f"Vowels: {count}")
# Output: Vowels: 3
```

**Vowels Found:** e, o, o

### Example 4: Counting Within Range

```python
# Count numbers between 10 and 20 (inclusive)
numbers = [5, 12, 18, 3, 25, 15, 7, 20]
count = 0

for num in numbers:
    if 10 <= num <= 20:
        count += 1

print(f"Numbers in range [10-20]: {count}")
# Output: Numbers in range [10-20]: 4
```

**Numbers in Range:** 12, 18, 15, 20

### Example 5: Counting Negative Numbers

```python
temperatures = [72, -5, 80, -12, 65, -3, 75]
count = 0

for temp in temperatures:
    if temp < 0:
        count += 1

print(f"Below zero readings: {count}")
# Output: Below zero readings: 3
```

### When to Use Counters

**Frequency Counting:**
```python
# How many times does 'x' appear?
count = text.count('x')
```

**Condition Matching:**
```python
# How many items meet criteria?
for item in items:
    if meets_criteria(item):
        count += 1
```

**Category Counting:**
```python
# How many in each category?
positives = 0
negatives = 0
zeros = 0

for num in numbers:
    if num > 0:
        positives += 1
    elif num < 0:
        negatives += 1
    else:
        zeros += 1
```

---

## Using a Total (Accumulator)

A total accumulates the sum of values. Initialize to 0, add each relevant value during iteration.

### The Total Pattern

```python
# 1. Initialize total before loop
total = 0

# 2. Loop through items
for item in collection:
    # 3. Add value to total
    total += value

# 4. Use total after loop
print(total)
```

### Example 1: Summing User Input

```python
# Ask for numbers until user enters -1
total = 0

while True:
    num_input = input("Enter a number (-1 to stop): ")
    num = int(num_input)
    
    if num == -1:
        break
    
    total += num

print(f"The sum of all numbers is: {total}")
```

**Example Session:**
```
Enter a number (-1 to stop): 10
Enter a number (-1 to stop): 5
Enter a number (-1 to stop): 8
Enter a number (-1 to stop): -1
The sum of all numbers is: 23
```

### Example 2: Summing List Values

```python
numbers = [10, 5, 15, 3, 7]
total = 0

for num in numbers:
    total += num

print(f"Total: {total}")
# Output: Total: 40
```

**Calculation:** 10 + 5 + 15 + 3 + 7 = 40

### Example 3: Summing Even Numbers Only

```python
numbers = [5, 12, 7, 8, 3, 14, 9, 20]
total = 0

for num in numbers:
    if num % 2 == 0:
        total += num

print(f"Sum of even numbers: {total}")
# Output: Sum of even numbers: 54
```

**Calculation:** 12 + 8 + 14 + 20 = 54

### Example 4: Summing Squares

```python
# Sum of squares from 1 to 5
total = 0

for i in range(1, 6):
    total += i ** 2

print(f"Sum of squares: {total}")
# Output: Sum of squares: 55
```

**Calculation:** 1² + 2² + 3² + 4² + 5² = 1 + 4 + 9 + 16 + 25 = 55

### Example 5: Calculating Running Total

```python
prices = [29.99, 15.50, 8.75, 42.00]
total = 0

print("Running total:")
for price in prices:
    total += price
    print(f"  After ${price:.2f}: ${total:.2f}")

print(f"\nFinal total: ${total:.2f}")
```

**Output:**
```
Running total:
  After $29.99: $29.99
  After $15.50: $45.49
  After $8.75: $54.24
  After $42.00: $96.24

Final total: $96.24
```

### When to Use Totals

**Sum Calculations:**
```python
# Add all values
for value in values:
    total += value
```

**Filtered Sums:**
```python
# Sum only items meeting condition
for item in items:
    if condition:
        total += item.value
```

**Weighted Sums:**
```python
# Sum with multipliers
for item, weight in zip(items, weights):
    total += item * weight
```

---

## Combining Counters and Totals

The real power emerges when using both patterns together in a single loop.

### Combined Pattern

```python
# Initialize both before loop
count = 0
total = 0

# Loop and update both
for item in collection:
    if condition:
        count += 1
        total += value

# Use both after loop
print(f"Count: {count}")
print(f"Total: {total}")
print(f"Average: {total / count if count > 0 else 0}")
```

### Example 1: Positive Numbers Only

```python
# Count and sum only positive numbers
count = 0
total = 0

while True:
    num = int(input("Enter a number (0 to stop): "))
    
    if num == 0:
        break
    
    if num > 0:
        print(f"Adding {num}...")
        count += 1
        total += num

print(f"You entered {count} positive numbers.")
print(f"Their total sum is {total}.")
```

**Example Session:**
```
Enter a number (0 to stop): 10
Adding 10...
Enter a number (0 to stop): 5
Adding 5...
Enter a number (0 to stop): -3
Enter a number (0 to stop): 2
Adding 2...
Enter a number (0 to stop): 0
You entered 3 positive numbers.
Their total sum is 17.
```

**Analysis:** Counted 3 positive numbers (10, 5, 2), summed them to 17, ignored -3.

### Example 2: Calculating Average

```python
# Count and sum to calculate average
numbers = [85, 92, 78, 95, 88, 76, 90]
count = 0
total = 0

for num in numbers:
    count += 1
    total += num

average = total / count
print(f"Count: {count}")
print(f"Total: {total}")
print(f"Average: {average:.1f}")
```

**Output:**
```
Count: 7
Total: 604
Average: 86.3
```

### Example 3: Pass/Fail Statistics

```python
# Track passing grades
scores = [85, 62, 95, 58, 78, 90, 45, 88]
pass_count = 0
total_passing = 0
passing_threshold = 70

for score in scores:
    if score >= passing_threshold:
        pass_count += 1
        total_passing += score

if pass_count > 0:
    avg_passing = total_passing / pass_count
    print(f"Passing students: {pass_count}")
    print(f"Average passing score: {avg_passing:.1f}")
else:
    print("No passing scores")
```

**Output:**
```
Passing students: 5
Average passing score: 87.2
```

**Passing Scores:** 85, 95, 78, 90, 88 (total: 436, average: 87.2)

### Example 4: Multiple Categories

```python
# Track multiple counters and totals
numbers = [12, -5, 8, -3, 15, 0, -7, 20]

positive_count = 0
negative_count = 0
zero_count = 0

positive_sum = 0
negative_sum = 0

for num in numbers:
    if num > 0:
        positive_count += 1
        positive_sum += num
    elif num < 0:
        negative_count += 1
        negative_sum += num
    else:
        zero_count += 1

print(f"Positive: {positive_count} numbers, sum = {positive_sum}")
print(f"Negative: {negative_count} numbers, sum = {negative_sum}")
print(f"Zero: {zero_count} numbers")
```

**Output:**
```
Positive: 4 numbers, sum = 55
Negative: 3 numbers, sum = -15
Zero: 1 numbers
```

### Example 5: Sales Analysis

```python
# Analyze sales data
sales = [120, 85, 200, 45, 150, 95, 175]
target = 100

above_target_count = 0
above_target_sum = 0
below_target_count = 0
below_target_sum = 0

for sale in sales:
    if sale >= target:
        above_target_count += 1
        above_target_sum += sale
    else:
        below_target_count += 1
        below_target_sum += sale

print(f"Above target: {above_target_count} sales, total = ${above_target_sum}")
print(f"Below target: {below_target_count} sales, total = ${below_target_sum}")
```

**Output:**
```
Above target: 4 sales, total = $645
Below target: 3 sales, total = $225
```

---

## Common Patterns and Use Cases

### Pattern 1: Average Calculation

```python
# Calculate average of a list
numbers = [10, 20, 30, 40, 50]
count = 0
total = 0

for num in numbers:
    count += 1
    total += num

average = total / count if count > 0 else 0
print(f"Average: {average}")
# Output: Average: 30.0
```

**Note:** Division by zero protection with `if count > 0`.

### Pattern 2: Percentage Calculation

```python
# What percentage are even?
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
total_count = 0
even_count = 0

for num in numbers:
    total_count += 1
    if num % 2 == 0:
        even_count += 1

percentage = (even_count / total_count) * 100
print(f"{percentage:.1f}% are even")
# Output: 50.0% are even
```

### Pattern 3: Conditional Statistics

```python
# Stats for numbers above threshold
data = [45, 78, 23, 89, 56, 92, 34, 67]
threshold = 60
count = 0
total = 0

for value in data:
    if value > threshold:
        count += 1
        total += value

if count > 0:
    print(f"Above {threshold}: {count} values")
    print(f"Sum: {total}")
    print(f"Average: {total / count:.1f}")
```

**Output:**
```
Above 60: 4 values
Sum: 326
Average: 81.5
```

### Pattern 4: Finding Maximum While Counting

```python
# Find max and count how many equal max
numbers = [5, 12, 3, 12, 7, 12, 8]
max_value = numbers[0]
max_count = 0

for num in numbers:
    if num > max_value:
        max_value = num
        max_count = 1  # Reset count
    elif num == max_value:
        max_count += 1

print(f"Max: {max_value}")
print(f"Occurs: {max_count} times")
```

**Output:**
```
Max: 12
Occurs: 3 times
```

---

## Common Errors and Fixes

### Error 1: Initializing Inside Loop

```python
# Wrong: Resets every iteration
for i in range(5):
    total = 0  # BAD: Resets to 0 each time
    total += i
print(total)
# Output: 4 (should be 10)
```

**Fix:** Initialize before the loop.

```python
# Correct
total = 0
for i in range(5):
    total += i
print(total)
# Output: 10
```

### Error 2: Forgetting to Initialize

```python
# Wrong: count not defined
for i in range(5):
    count += 1  # NameError: name 'count' is not defined
```

**Fix:** Always initialize before using.

```python
# Correct
count = 0
for i in range(5):
    count += 1
```

### Error 3: Wrong Indentation

```python
# Wrong: Updates outside loop
total = 0
for i in range(5):
    pass
total += i  # BAD: Outside loop, only adds last value
print(total)
# Output: 4 (should be 10)
```

**Fix:** Indent accumulation inside loop.

```python
# Correct
total = 0
for i in range(5):
    total += i
print(total)
# Output: 10
```

### Error 4: Division by Zero

```python
# Wrong: Dividing without checking count
numbers = []
count = 0
total = 0

for num in numbers:
    count += 1
    total += num

average = total / count  # ZeroDivisionError if list is empty
```

**Fix:** Check count before dividing.

```python
# Correct
if count > 0:
    average = total / count
    print(f"Average: {average}")
else:
    print("No data to average")
```

### Error 5: Incorrect Increment Location

```python
# Wrong: Counter increments always
count = 0
for num in [1, 2, 3, 4, 5]:
    count += 1  # Counts all, not just even
    if num % 2 == 0:
        pass

print(f"Even count: {count}")
# Output: Even count: 5 (should be 2)
```

**Fix:** Increment inside condition.

```python
# Correct
count = 0
for num in [1, 2, 3, 4, 5]:
    if num % 2 == 0:
        count += 1

print(f"Even count: {count}")
# Output: Even count: 2
```

---

## Practice Exercises

### Exercise 1: Count Odd Numbers

Count how many odd numbers are in the range 1 to 20.

<details>
<summary>Solution</summary>

```python
count = 0

for i in range(1, 21):
    if i % 2 != 0:
        count += 1

print(f"Odd numbers: {count}")
# Output: Odd numbers: 10
```
</details>

### Exercise 2: Sum of Multiples of 5

Calculate the sum of all multiples of 5 between 1 and 50.

<details>
<summary>Solution</summary>

```python
total = 0

for i in range(1, 51):
    if i % 5 == 0:
        total += i

print(f"Sum: {total}")
# Output: Sum: 275
```

**Numbers:** 5 + 10 + 15 + 20 + 25 + 30 + 35 + 40 + 45 + 50 = 275
</details>

### Exercise 3: Average of Positive Numbers

Given a list of numbers, calculate the average of only the positive numbers.

```python
numbers = [5, -2, 10, -7, 15, 3, -1, 8]
```

<details>
<summary>Solution</summary>

```python
numbers = [5, -2, 10, -7, 15, 3, -1, 8]
count = 0
total = 0

for num in numbers:
    if num > 0:
        count += 1
        total += num

if count > 0:
    average = total / count
    print(f"Average of positive numbers: {average:.1f}")
else:
    print("No positive numbers")
# Output: Average of positive numbers: 8.2
```

**Positive Numbers:** 5, 10, 15, 3, 8 (total: 41, count: 5, average: 8.2)
</details>

### Exercise 4: Count and Sum Evens

Count how many even numbers are in a list and calculate their sum.

```python
numbers = [3, 8, 15, 22, 7, 12, 5, 18]
```

<details>
<summary>Solution</summary>

```python
numbers = [3, 8, 15, 22, 7, 12, 5, 18]
count = 0
total = 0

for num in numbers:
    if num % 2 == 0:
        count += 1
        total += num

print(f"Even count: {count}")
print(f"Even sum: {total}")
```

**Output:**
```
Even count: 4
Even sum: 60
```

**Even Numbers:** 8, 22, 12, 18
</details>

### Exercise 5: Score Statistics

Calculate the number of passing scores (≥70) and their average.

```python
scores = [85, 62, 95, 58, 78, 90, 45, 88, 72]
```

<details>
<summary>Solution</summary>

```python
scores = [85, 62, 95, 58, 78, 90, 45, 88, 72]
passing_threshold = 70
count = 0
total = 0

for score in scores:
    if score >= passing_threshold:
        count += 1
        total += score

if count > 0:
    average = total / count
    print(f"Passing scores: {count}")
    print(f"Average: {average:.1f}")
else:
    print("No passing scores")
```

**Output:**
```
Passing scores: 6
Average: 84.7
```
</details>

### Exercise 6: Temperature Analysis

Count how many days were above freezing (>32°F) and calculate the average temperature for those days.

```python
temperatures = [28, 35, 42, 31, 38, 45, 29, 40]
```

<details>
<summary>Solution</summary>

```python
temperatures = [28, 35, 42, 31, 38, 45, 29, 40]
freezing_point = 32
count = 0
total = 0

for temp in temperatures:
    if temp > freezing_point:
        count += 1
        total += temp

if count > 0:
    average = total / count
    print(f"Days above freezing: {count}")
    print(f"Average temp: {average:.1f}°F")
```

**Output:**
```
Days above freezing: 5
Average temp: 40.0°F
```
</details>

### Exercise 7: Price Range Analysis

Count how many items are in the "premium" range ($50-$100) and calculate their total value.

```python
prices = [25.99, 75.50, 45.00, 85.00, 120.00, 65.50, 30.00, 95.00]
```

<details>
<summary>Solution</summary>

```python
prices = [25.99, 75.50, 45.00, 85.00, 120.00, 65.50, 30.00, 95.00]
count = 0
total = 0

for price in prices:
    if 50 <= price <= 100:
        count += 1
        total += price

print(f"Premium items: {count}")
print(f"Total value: ${total:.2f}")
```

**Output:**
```
Premium items: 4
Total value: $321.00
```

**Premium Prices:** 75.50, 85.00, 65.50, 95.00
</details>

### Exercise 8: Word Length Statistics

Count how many words are longer than 5 characters and calculate the total characters in those words.

```python
words = ["hello", "hi", "wonderful", "bye", "amazing", "ok", "fantastic"]
```

<details>
<summary>Solution</summary>

```python
words = ["hello", "hi", "wonderful", "bye", "amazing", "ok", "fantastic"]
count = 0
total_chars = 0

for word in words:
    if len(word) > 5:
        count += 1
        total_chars += len(word)

print(f"Long words: {count}")
print(f"Total characters: {total_chars}")

if count > 0:
    avg_length = total_chars / count
    print(f"Average length: {avg_length:.1f}")
```

**Output:**
```
Long words: 3
Total characters: 27
Average length: 9.0
```

**Long Words:** wonderful (9), amazing (7), fantastic (9)
</details>

---

## Real-World Applications

### Sales Performance Tracking

```python
def analyze_sales(daily_sales, target):
    """Analyze sales performance against target."""
    days_met_target = 0
    total_above_target = 0
    total_sales = 0
    days_count = 0
    
    for sale in daily_sales:
        days_count += 1
        total_sales += sale
        
        if sale >= target:
            days_met_target += 1
            total_above_target += sale - target
    
    success_rate = (days_met_target / days_count) * 100
    
    print(f"Total days: {days_count}")
    print(f"Days met target: {days_met_target} ({success_rate:.1f}%)")
    print(f"Total sales: ${total_sales}")
    print(f"Amount above target: ${total_above_target}")
```

### Student Grade Analysis

```python
def grade_statistics(scores):
    """Calculate comprehensive grade statistics."""
    total = 0
    count = 0
    
    a_count = 0  # 90+
    b_count = 0  # 80-89
    c_count = 0  # 70-79
    failing = 0  # <70
    
    for score in scores:
        count += 1
        total += score
        
        if score >= 90:
            a_count += 1
        elif score >= 80:
            b_count += 1
        elif score >= 70:
            c_count += 1
        else:
            failing += 1
    
    if count > 0:
        average = total / count
        print(f"Class average: {average:.1f}")
        print(f"A grades: {a_count}")
        print(f"B grades: {b_count}")
        print(f"C grades: {c_count}")
        print(f"Failing: {failing}")
```

### Inventory Management

```python
def analyze_inventory(items, reorder_level):
    """Check inventory and identify items needing reorder."""
    total_items = 0
    total_value = 0
    needs_reorder = 0
    reorder_value = 0
    
    for item in items:
        quantity = item['quantity']
        price = item['price']
        
        total_items += 1
        total_value += quantity * price
        
        if quantity < reorder_level:
            needs_reorder += 1
            reorder_value += (reorder_level - quantity) * price
    
    print(f"Total items: {total_items}")
    print(f"Total inventory value: ${total_value:.2f}")
    print(f"Items needing reorder: {needs_reorder}")
    print(f"Estimated reorder cost: ${reorder_value:.2f}")
```

---

## Key Takeaways

✅ **Initialize before the loop** - Both counters and totals must start outside the loop  
✅ **Counters track "how many"** - Increment by fixed amount (usually 1)  
✅ **Totals track "how much"** - Add varying values to accumulate sum  
✅ **Update inside the loop** - Modify values during each iteration  
✅ **Use after the loop** - Final values available after loop completes  
✅ **Combine for statistics** - Use both together to calculate averages, percentages  
✅ **Protect against division by zero** - Check count before dividing  
✅ **Multiple counters/totals allowed** - Track different categories simultaneously

**Remember:** The most critical rule for counters and totals is initialization location. Initialize before the loop, update inside the loop, use after the loop. Think "Set up outside, work inside, finish outside." If you initialize inside, you reset every iteration and lose your accumulated data.

---

**Last Updated:** October 30, 2025
