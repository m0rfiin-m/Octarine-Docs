# Modulo in Practice: Parity, Cycles, and Positions

**Date:** October 24, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 1, Lesson 7

## Overview
This lesson focuses on practical uses of the **modulo operator (%)** in Python.  
You learned how `%` helps determine if numbers are **even or odd (parity)** and how to calculate **positions in repeating cycles**, like seats or days.  
Modulo tells you the **remainder** when dividing two numbers.

---

## Key Concepts

### 1. The Modulo Operator `%`
The modulo operator gives the **remainder** after division.

```python
print(14 % 5)
# Output: 4
```
14 divided by 5 gives a quotient of 2 with a remainder of 4.  
That remainder is what `%` returns.

---

### 2. Checking for Even or Odd (Parity)
When dividing any number by 2, there are only two possible remainders: **0 or 1**.

- If the remainder is 0 → the number is **even**.  
- If the remainder is 1 → the number is **odd**.

```python
num = 14
print(num % 2)  # Output: 0 → even

num = 17
print(num % 2)  # Output: 1 → odd
```

You can print results clearly using f-strings:

```python
num = 18
print(f"The remainder when {num} is divided by 2 is {num % 2}")
# Output: The remainder when 18 is divided by 2 is 0
```

---

### 3. Understanding Why `% 2` Gives Only 0 or 1
When dividing by 2, there are only two possible outcomes:
- Numbers divisible by 2 leave **no remainder (0)**.
- Numbers that are not divisible by 2 leave **1** as remainder.

This works because `%` always returns a value between **0 and (divisor - 1)**.

Example with `% 5`:
```python
print(40 % 5)  # Output: 0 → divides evenly
print(42 % 5)  # Output: 2 → remainder is 2
```
So `% 5` can only give results in `{0, 1, 2, 3, 4}`.

---

### 4. Using Modulo for Cycles (Positions)
Modulo can track **positions in repeating cycles**, such as seats arranged in a circle.

Example: 10 seats labeled 0–9.  
You move forward 17 steps starting from seat 0.

```python
start = 0
steps = 17
print((start + steps) % 10)
# Output: 7
```
After 17 steps, you land on seat 7.

**Why this works:** `%` wraps numbers back to 0 once they exceed the cycle size.

Try with different values:
```python
start = 0
steps = 23
print((start + steps) % 10)  # Output: 3

steps = 38
print((start + steps) % 10)  # Output: 8
```

The number after `%` (in this case 10) defines the **cycle length**.  
If you have 8 seats, use `% 8`. If 12 months, use `% 12`.

---

## Quick Recap
| Operator | Purpose | Example | Output |
|-----------|----------|----------|---------|
| `%` | Gives remainder | `14 % 5` | `4` |
| `% 2` | Parity check | `17 % 2` | `1` (odd) |
| `% 10` | Cyclic wrap-around | `(start + steps) % 10` | Seat position |

---

## Practice Examples

### Even/Odd Check
```python
num = 29
print(num % 2)
# Output: 1 → odd
```

### Cycle Example
```python
start = 0
steps = 57
print((start + steps) % 8)
# Output: 1 → seat 1 on an 8-seat circle
```

### Exact Division Example
```python
print(40 % 5)
# Output: 0 → divides evenly (no remainder)
```

---

## Common Pitfalls
- Using the wrong divisor (the number after `%`) for your cycle.  
- Forgetting parentheses in expressions like `(start + steps) % size`.  
- Expecting negative remainders (Python always returns non-negative remainders).

---

## Summary
You learned to:
- Use `%` to find remainders.  
- Use `% 2` to detect even or odd numbers.  
- Apply `%` for cyclic or repeating patterns.  
- Understand that `% n` always returns a value from `0` to `n-1`.

The modulo operator is a small but powerful tool in Python's arithmetic system, essential for **pattern detection, rotations, and step-based calculations**.

---

**Next Lesson:** Rounding and Money Format
