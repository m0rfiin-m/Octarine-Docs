# Expressions and Operator Precedence

**Date:** October 22, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 1, Lesson 3

## What You'll Learn

This lesson covers how Python evaluates mathematical expressions, the order of operations (operator precedence), and how to control evaluation order using parentheses. You'll also learn how operators work differently with strings versus numbers.

---

## Understanding Expressions

An **expression** is any combination of values, variables, and operators that Python can evaluate to produce a result.

```python
# Simple expressions
5 + 3           # Evaluates to 8
price * quantity  # Evaluates to calculated total
"Hello" + " World"  # Evaluates to "Hello World"
```

---

## Operator Precedence: The Order of Operations

Python follows the same order of operations you learned in math class (PEMDAS):

**P**arentheses  
**E**xponents  
**M**ultiplication  
**D**ivision  
**A**ddition  
**S**ubtraction

### Rule: Multiplication and Division Before Addition and Subtraction

```python
print(7 + 6 * 3)
# Output: 25
```

**Why 25, not 39?**
1. Python evaluates `6 * 3` first (multiplication) → `18`
2. Then adds `7 + 18` → `25`

If Python went left to right, it would calculate `7 + 6 = 13`, then `13 * 3 = 39`. But multiplication always happens before addition.

### Same Priority: Left to Right

When operators have the same priority (like `+` and `-`, or `*` and `/`), Python evaluates left to right.

```python
print(10 - 3 + 2)
# Output: 9
# Calculation: (10 - 3) + 2 → 7 + 2 → 9

print(20 / 4 * 2)
# Output: 10.0
# Calculation: (20 / 4) * 2 → 5.0 * 2 → 10.0
```

---

## Using Parentheses to Control Order

Parentheses override the default order of operations. Whatever is inside parentheses gets evaluated first.

### Example: Shopping Cart Calculation

```python
price = 3
tax = 2
qty = 4

# With parentheses: add first, then multiply
total = (price + tax) * qty
print(total)
# Output: 20
# Calculation: (3 + 2) * 4 → 5 * 4 → 20

# Without parentheses: multiply first, then add
total = price + tax * qty
print(total)
# Output: 11
# Calculation: 3 + (2 * 4) → 3 + 8 → 11
```

**Key Insight:** The placement of parentheses completely changes the result!

### More Precedence Examples

```python
# Example 1
print(2 + 3 * 4)
# Output: 14
# Calculation: 2 + (3 * 4) → 2 + 12 → 14

print((2 + 3) * 4)
# Output: 20
# Calculation: (2 + 3) * 4 → 5 * 4 → 20

# Example 2
print(10 - 2 * 3)
# Output: 4
# Calculation: 10 - (2 * 3) → 10 - 6 → 4

print((10 - 2) * 3)
# Output: 24
# Calculation: (10 - 2) * 3 → 8 * 3 → 24
```

---

## String Operations with Operators

Operators behave differently when used with strings versus numbers.

### The `+` Operator: Concatenation

With strings, `+` joins (concatenates) them together.

```python
print("Hello" + " " + "World")
# Output: Hello World

print("ha" * 2 + "!")
# Output: haha!
# First: "ha" * 2 → "haha"
# Then: "haha" + "!" → "haha!"
```

### The `*` Operator: Repetition

With strings, `*` repeats the string a specified number of times.

```python
print("=" * 10)
# Output: ==========

print("Python " * 3)
# Output: Python Python Python 
```

**Critical Rule:** You can only multiply a string by an **integer**, not by another string or a float.

---

## Common String Operator Errors

### Error 1: Adding String and Number

```python
# Bad: Trying to add string and integer
print("ha" + 2)

# Error:
# Traceback (most recent call last):
# TypeError: can only concatenate str (not "int") to str
```

**Why This Fails:**  
Python doesn't know if you want `"ha2"` (concatenation) or some mathematical operation. You must be explicit.

**Fixes:**

```python
# Fix 1: Convert number to string for concatenation
print("ha" + str(2))
# Output: ha2

# Fix 2: Use repetition if that's what you meant
print("ha" * 2)
# Output: haha
```

### Error 2: Multiplying String by String

```python
# Bad: Trying to multiply two strings
print("ha" * "ha")

# Error:
# Traceback (most recent call last):
# TypeError: can't multiply sequence by non-int of type 'str'
```

**Why This Fails:**  
Repetition requires an integer to specify how many times to repeat.

**Fix:**

```python
# Correct: Multiply string by integer
print("ha" * 2)
# Output: haha
```

### Error 3: Multiplying String by Float

```python
# Bad: Trying to multiply string by decimal
print("*" * 3.5)

# Error:
# TypeError: can't multiply sequence by non-int of type 'float'
```

**Fix:**

```python
# Convert float to integer first
print("*" * int(3.5))
# Output: ***
```

---

## Quick Reference: String Operators

| Operator | With Numbers | With Strings | Example | Result |
|----------|--------------|--------------|---------|--------|
| `+` | Addition | Concatenation | `"Hi" + "!"` | `"Hi!"` |
| `*` | Multiplication | Repetition | `"Go" * 3` | `"GoGoGo"` |
| `-` | Subtraction | ❌ Not allowed | `"Hi" - "i"` | TypeError |
| `/` | Division | ❌ Not allowed | `"Hi" / 2` | TypeError |

---

## Practice Exercises

**Exercise 1: Predict the Output**

What will each expression output?

```python
print(5 + 3 * 2)
print((5 + 3) * 2)
print(10 / 2 + 3)
```

<details>
<summary>Solution</summary>

```python
print(5 + 3 * 2)
# Output: 11
# Calculation: 5 + (3 * 2) → 5 + 6 → 11

print((5 + 3) * 2)
# Output: 16
# Calculation: (5 + 3) * 2 → 8 * 2 → 16

print(10 / 2 + 3)
# Output: 8.0
# Calculation: (10 / 2) + 3 → 5.0 + 3 → 8.0
```

</details>

**Exercise 2: Fix the Calculation**

A store charges $50 per item plus a $10 shipping fee, and you're buying 3 items. The total should be $160, but this code gives the wrong answer:

```python
item_price = 50
shipping = 10
quantity = 3

total = item_price + shipping * quantity
print(total)
# Output: 80 (Wrong! Should be 160)
```

<details>
<summary>Solution</summary>

```python
item_price = 50
shipping = 10
quantity = 3

# Add parentheses to calculate (price + shipping) first
total = (item_price + shipping) * quantity
print(total)
# Output: 180
# Wait, that's also wrong! We want: (price * quantity) + shipping

# Correct approach:
total = (item_price * quantity) + shipping
print(total)
# Output: 160 ✓
```

**Explanation:** We need to multiply the price by quantity first, then add the flat shipping fee.

</details>

**Exercise 3: String Operations**

Create a border for a message using string operators:

```python
# Create a line of 20 dashes
# Print "WELCOME"
# Create another line of 20 dashes
```

<details>
<summary>Solution</summary>

```python
border = "-" * 20
print(border)
print("WELCOME")
print(border)

# Output:
# --------------------
# WELCOME
# --------------------
```

</details>

**Exercise 4: Fix the TypeError**

This code has an error. Fix it:

```python
name = "Python"
version = 3
print("Welcome to " + name + version)
```

<details>
<summary>Solution</summary>

```python
name = "Python"
version = 3

# Fix 1: Convert number to string
print("Welcome to " + name + " " + str(version))
# Output: Welcome to Python 3

# Fix 2: Use f-string (cleaner)
print(f"Welcome to {name} {version}")
# Output: Welcome to Python 3
```

</details>

---

## Key Takeaways

✅ **Multiplication and division before addition and subtraction** - Follow PEMDAS order  
✅ **Same priority = left to right** - Operators of equal precedence evaluate left to right  
✅ **Parentheses override default order** - Use them to control evaluation  
✅ **`+` with strings = concatenation** - Joins strings together  
✅ **`*` with strings = repetition** - Repeats the string (integer only)  
✅ **Can't mix string and number operations** - Must convert types first  
✅ **String * integer only** - Can't multiply strings by floats or other strings

**Remember:** When in doubt about operator precedence, use parentheses to make your intentions explicit. It makes code clearer and prevents unexpected results.

---

**Last Updated:** October 25, 2025