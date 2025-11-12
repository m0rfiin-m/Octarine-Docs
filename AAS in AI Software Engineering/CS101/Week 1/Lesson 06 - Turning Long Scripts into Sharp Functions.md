# Turning Long Scripts into Sharp Functions

**Date:** November 2, 2025  
**Course:** CS101 - Computer Science Fundamentals  
**Week:** 1, Lesson 06

## What You'll Learn

This lesson teaches you to break up long scripts into focused functions. You'll learn when and how to extract code into reusable functions, practice the refactoring process, and understand the benefits of modular code design.

---

## Why Break Up Scripts

Long, single-block scripts get brittle and hard to maintain. Functions give you three wins:

1. **Focus** - Each function does one thing well
2. **Reuse** - Call the same logic from multiple places
3. **Testability** - Verify each piece works independently

---

## The Refactoring Process

### Step 1: Identify Coherent Blocks

Look for sections that perform a single task:
- Calculation loops
- Data formatting
- Decision logic
- Output generation

### Step 2: Extract to Function

```python
# Before: Inline calculation
points = [10, 5, 7, 12, 8]
total = 0
for p in points:
    total += p

# After: Extracted function
def calc_total(points):
    """Return the sum of numbers in points."""
    total = 0
    for p in points:
        total += p
    return total

points = [10, 5, 7, 12, 8]
total = calc_total(points)
```

### Step 3: Replace with Function Call

Move the logic into the function, then call it where the original code was.

---

## Core Extraction Patterns

### Pattern 1: Extract Calculation

```python
def calc_total(points):
    """Return the sum of numbers in points."""
    total = 0
    for p in points:
        total += p
    return total
```

### Pattern 2: Extract Reporting

```python
def format_report(name, total):
    """Display formatted statistics report."""
    print("Stats for", name)
    print("-----")
    print("Total:", total)
```

### Pattern 3: Extract Decision Logic

```python
def performance_message(total):
    """Return performance evaluation based on total score."""
    return "Good job!" if total > 30 else "Keep going!"
```

---

## Complete Refactored Example

### Before: Long Script

```python
points = [10, 5, 7, 12, 8]
name = "Marco"

total = 0
for p in points:
    total += p

print("Stats for", name)
print("-----")
print("Total:", total)

if total > 30:
    print("Good job!")
else:
    print("Keep going!")
```

### After: Modular Functions

```python
def calc_total(points):
    """Return the sum of numbers in points."""
    total = 0
    for p in points:
        total += p
    return total

def format_report(name, total):
    """Display formatted statistics report."""
    print("Stats for", name)
    print("-----")
    print("Total:", total)

def performance_message(total):
    """Return performance evaluation based on total score."""
    return "Good job!" if total > 30 else "Keep going!"

# Main script - clean and readable
points = [10, 5, 7, 12, 8]
name = "Marco"

total = calc_total(points)
format_report(name, total)
print(performance_message(total))

# Output:
# Stats for Marco
# -----
# Total: 42
# Good job!
```

---

## Rules That Keep You Safe

### Rule 1: Function Bodies Are Indented

```python
def my_function():
    # Body indented 4 spaces
    result = 10 + 5
    return result
```

### Rule 2: Return vs Print

Use `return` to send data back; use `print` for display only.

```python
# Return for data
def calculate(x):
    return x * 2

# Print for display
def show_result(value):
    print(f"Result: {value}")
```

### Rule 3: No Self-Calls

Never call a function from inside its own definition unless you intend recursion.

```python
# Bad: Accidental recursion
def format_report(name, total):
    print("Stats for", name)
    format_report(name, total)  # Infinite loop!

# Good: No self-call
def format_report(name, total):
    print("Stats for", name)
    print("Total:", total)
```

### Rule 4: Clear Scope

Function parameters are local. The name you pass must exist where you call it.

```python
def greet(username):
    print(f"Hello, {username}")

# username must be defined before calling
name = "Marco"
greet(name)  # Works
```

---

## Common Refactoring Mistakes

### Mistake 1: Missing Indentation

```python
# Bad: No indentation
def calculate(x):
return x * 2

# Good: Proper 4-space indent
def calculate(x):
    return x * 2
```

### Mistake 2: Forgetting to Replace Original Code

```python
# Bad: Function defined but original code still inline
def calc_total(points):
    total = 0
    for p in points:
        total += p
    return total

# Original calculation still here!
total = 0
for p in points:
    total += p
```

### Mistake 3: Parameter Name Mismatch

```python
# Bad: Call uses different name than defined
points = [10, 5, 7]
total = calc_total(scores)  # NameError: scores not defined

# Good: Names match
points = [10, 5, 7]
total = calc_total(points)
```

---

## Practice Exercises

**Exercise 1: Extract Calculation**

Extract the average calculation into a function.

```python
scores = [85, 90, 78, 92]
total = sum(scores)
average = total / len(scores)
print(f"Average: {average}")
```

<details>
<summary>Solution</summary>

```python
def calculate_average(scores):
    """Calculate the arithmetic mean of a list of scores."""
    total = sum(scores)
    average = total / len(scores)
    return average

scores = [85, 90, 78, 92]
average = calculate_average(scores)
print(f"Average: {average}")
# Output: Average: 86.25
```

**Explanation:** Extracted calculation logic into focused function with clear name and docstring. Main code now calls the function.

</details>

**Exercise 2: Extract Formatting**

Extract the price display logic into a function.

```python
price = 19.99
tax = price * 0.08
total = price + tax
print(f"Price: ${price:.2f}")
print(f"Tax: ${tax:.2f}")
print(f"Total: ${total:.2f}")
```

<details>
<summary>Solution</summary>

```python
def display_price_breakdown(price):
    """Display price, tax, and total with formatting."""
    tax = price * 0.08
    total = price + tax
    print(f"Price: ${price:.2f}")
    print(f"Tax: ${tax:.2f}")
    print(f"Total: ${total:.2f}")

price = 19.99
display_price_breakdown(price)
# Output:
# Price: $19.99
# Tax: $1.60
# Total: $21.59
```

**Explanation:** Formatting logic extracted into function that calculates and displays. Function name clearly indicates it's for display, not calculation.

</details>

**Exercise 3: Full Refactor**

Refactor this script into three functions: calculation, formatting, and evaluation.

```python
sales = [100, 250, 175, 300]
total = 0
for sale in sales:
    total += sale

print("Sales Report")
print("-" * 20)
print(f"Total: ${total}")

if total > 500:
    print("Exceeds target!")
else:
    print("Below target")
```

<details>
<summary>Solution</summary>

```python
def calculate_total_sales(sales):
    """Calculate total from list of sales amounts."""
    total = 0
    for sale in sales:
        total += sale
    return total

def display_sales_report(total):
    """Display formatted sales report."""
    print("Sales Report")
    print("-" * 20)
    print(f"Total: ${total}")

def evaluate_performance(total):
    """Return performance message based on sales target."""
    return "Exceeds target!" if total > 500 else "Below target"

# Main script
sales = [100, 250, 175, 300]
total = calculate_total_sales(sales)
display_sales_report(total)
print(evaluate_performance(total))

# Output:
# Sales Report
# --------------------
# Total: $825
# Exceeds target!
```

**Explanation:** Three focused functions each handle one responsibility: calculation, display, and evaluation. Main script is now clear and readable.

</details>

---

## Key Takeaways

✅ **Functions isolate responsibilities** - Each does one thing well  
✅ **Use return to send data back** - Print is for display only  
✅ **Indent function bodies 4 spaces** - Standard Python structure  
✅ **Extract coherent blocks** - Calculations, formatting, decisions  
✅ **One job per function** - Names should clearly state purpose  
✅ **Run after each refactor** - Verify behavior stays consistent  
✅ **Replace original code** - Don't leave duplicate logic inline

**Remember:** Functions are about organization and reuse. When code does one thing well, you can understand it, test it, and reuse it. Start by identifying natural boundaries in your script, then extract each section into a focused function.

---

**Last Updated:** November 12, 2025
