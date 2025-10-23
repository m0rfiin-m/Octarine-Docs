# Lesson: Modeling Real-World Calculations

## Overview
This lesson focuses on translating **real-world word problems** into **arithmetic expressions** and printing results clearly in Python.  
You practiced using the `print()` function, arithmetic operators, and variable expressions to represent small real-life scenarios.

---

## Key Concepts

### 1. Operator Precedence
Python follows standard math order:
```python
print(4 + 2 * 3)  # Output: 10
```
Multiplication runs before addition.

---

### 2. Translating Word Problems
You can model real situations with arithmetic directly.

**Example:**
> You have $20, buy a snack for $3, and a drink for $2.

```python
print("money left:", 20 - 3 - 2)
# Output: money left: 15
```

---

### 3. Using `print()` for Output
The `print()` function displays results in readable form.

**Two styles:**
```python
# a) Variable method
cost = 12 + 5
print("total cost:", cost)

# b) Direct method
print("total cost:", 12 + 5)
```
Both work.  
Use **style (b)** for simple one-off calculations.

---

### 4. String Formatting
You can include expressions inside text using **f-strings**:
```python
print(f"total number of tickets: {50 - 7 + 15}")
# Output: total number of tickets: 58
```
No commas are used inside f-strings.  
Everything stays inside the quotes.

---

### 5. Arithmetic Practice Examples
**Book cost:**
```python
print("total cost:", 12 + 5)
# Output: total cost: 17
```

**Game points:**
```python
print("total points:", 30 + 18)
# Output: total points: 48
```

**Tickets:**
```python
print(f"total number of tickets: {50 - 7 + 15}")
# Output: total number of tickets: 58
```

---

## Style Tips
- Keep code clean: delete old lines between tasks.
- For small scripts, inline expressions make code shorter and easier to read.
- Use f-strings when including variables or more complex messages.

---

## Quick Quiz Recap
1. **Operator joining two subtractions:** `-`  
2. **Spaces in** `print("a", 4+1, "b")` → **2 spaces**

---

## Summary
You learned to:
- Convert everyday problems into arithmetic code.  
- Apply correct operator precedence.  
- Use `print()` effectively.  
- Format output with f-strings.  
- Compare clarity between variable and inline expressions.

This lesson built a strong base for modeling real-world data and preparing for more advanced Python logic.

---

**Next Lesson:** Division modes: `/` vs `//` (quotient and remainder)
