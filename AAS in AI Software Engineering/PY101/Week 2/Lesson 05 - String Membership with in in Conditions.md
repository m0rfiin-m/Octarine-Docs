
## Lesson 5: String Membership with `in` in Conditions

**Course:** PY101 – Python Fundamentals
**Week:** 2
**Date:** October 29, 2025
**Status:** 📘 Study Guide

---

### Overview

This lesson explains how to test if one string exists inside another using the `in` and `not in` operators.
These operators return `True` or `False` and are often used inside `if` statements to make decisions.

---

### Key Concepts

**1. Membership Operators**

- `in` → Checks if a substring exists inside a string.

- `not in` → Checks if a substring does *not* exist inside a string.

**2. Boolean Return Values**

- Both operators return `True` or `False`, not an index or position.

**3. Case Sensitivity**

- String comparisons in Python are case-sensitive.
  `"A" in "abc"` → `False` because "A" ≠ "a"

**4. Use in Conditions**

```python
if "cat" in "concatenate":
    print("Found cat")
```

**5. Use with** `not in`

```python
if "dog" not in "concatenate":
    print("No dog found")
```

---

### Code Examples

**Example 1 – Basic Membership**

```python
phrase = "python rocks"
print("rock" in phrase)     # True
print("Rock" in phrase)     # False (case-sensitive)
```

**Example 2 – Using** `in` **in an If Statement**

```python
secret = "open sesame"
if "sesame" in secret:
    print("door opens")
else:
    print("stay closed")
```

**Example 3 – Case Sensitivity Check**

```python
secret = "open sesame"
print("Sesame" in secret)   # False
```

**Example 4 – Using** `not in`

```python
text = "hello world"
if "bye" not in text:
    print("no goodbye found")
```

**Example 5 – Combined Example**

```python
message = "python 3.12"
has_digit = "3" in message
no_dash = "-" not in message
print(has_digit, no_dash)   # True True
```

---

### Common Pitfalls

- Confusing `in` with `find()` (which returns an index, not a Boolean).

- Forgetting that string membership is case-sensitive.

- Using `in` on numbers instead of strings.
  Example: `3 in 123` is invalid; convert to string first.

---

### Practice Exercises

1. Check if the word `"code"` is in the string `"learn to code in python"`.

2. Write an if statement that prints `"no match"` if `"x"` is not in `"abc"`.

3. Create a variable `password = "Secure123"`.
   Print `"valid"` if `"123"` is in the password, else print `"invalid"`.

4. Test if `"PY"` is in `"python"`. Then test `"py"` in `"python"`.
   Explain the difference.

---

### Summary Notes

- `in` → checks presence.

- `not in` → checks absence.

- Returns Boolean (`True` or `False`).

- Case-sensitive comparisons.

- Useful in `if` conditions for string validation and filtering.

---

Would you like me to make a **PDF or DOCX version** formatted for upload into your Maestro project folder?