# Division Modes: `/` vs `//` with Quotient and Remainder

**Date:** October 23, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 1, Lesson 6

## Overview
This lesson covers **division operations in Python** — how to calculate **float results**, **whole-number quotients**, and **remainders**.  
You learned how to use `/`, `//`, and `%` operators, and when each is useful in real-world problem modeling.

---

## Key Concepts

### 1. True Division `/`
Performs standard division and returns a **float** (decimal result).

```python
print("7/2 =", 7 / 2)
# Output: 7/2 = 3.5
```
Used when you need precise decimal results.

---

### 2. Floor Division `//`
Performs division but **truncates decimals**, returning the **integer quotient**.

```python
print("7//2 =", 7 // 2)
# Output: 7//2 = 3
```
Useful for counting full groups or "whole boxes" in real-world problems.

---

### 3. Modulo `%`
Finds the **remainder** after full groups are counted.

```python
print("7 % 2 =", 7 % 2)
# Output: 7 % 2 = 1
```
The modulo operator helps find what's **left over** after division.

---

## Example: Cupcake Boxes
You have 7 cupcakes and boxes that hold 2 each.

```python
print("full boxes:", 7 // 2)
print("leftover cupcakes:", 7 % 2)
```
**Output:**
```
full boxes: 3
leftover cupcakes: 1
```

---

## Example: Apples in Bags
```python
total = 23
size = 4
print("bags:", total // size, "left:", total % size)
```
**Output:**
```
bags: 5 left: 3
```

You can also format the same line with an f-string:
```python
print(f"bags: {total // size} left {total % size}")
```

---

## Example: Tickets and Prizes
You have 50 tickets, and each prize costs 6 tickets.

```python
tickets = 50
prize = 6
print(f"tickets: {tickets // prize} left {tickets % prize}")
```
**Output:**
```
tickets: 8 left 2
```

---

## Combining Division Operations
You can display both float and floor division together to compare results.

```python
print("7/2 =", 7 / 2, "   7//2 =", 7 // 2)
# Output: 7/2 = 3.5    7//2 = 3
```

---

## Practice Quick Quiz

**1.** What operator performs floor division in Python?  
`//`

**2.** What operator gives the remainder after division?  
`%`

**3.** What is the result of `19 % 5`?  
`4`

---

## Common Pitfalls
- Forgetting that `/` always gives a float, even if the result is a whole number.  
- Mixing up variable names (make sure all used variables are defined).  
- Misusing commas or missing quotes in f-strings.  

---

## Summary
You learned to:
- Use `/` for precise division results (floats).  
- Use `//` for integer division (whole-number quotients).  
- Use `%` to find remainders.  
- Combine them to solve real-world problems like packaging or grouping items.  

These three operators are key for modeling **distribution and remainder-based logic** in Python programs.

---

**Next Lesson:** Modulo in Practice — Parity, Cycles, and Positions
