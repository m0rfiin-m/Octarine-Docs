
**Lesson 5: Elif and Refactoring Nested Decisions**

**Course:** PY101 – Python Fundamentals
**Week:** 3
**Date:** October 30, 2025
**Status:** 📘 Completed

---

### **Overview**

This lesson focuses on simplifying complex decision structures in Python using the `elif` keyword. You’ll learn how to refactor nested `if/else` statements into clean, readable `if/elif/else` chains. This concept improves code clarity, reduces indentation depth, and prevents unreachable or redundant logic.

You’ll also reinforce:

- Condition ordering (from specific to general)

- The use of `not in` for membership checks

- Proper syntax and indentation

- Avoiding common errors like missing colons or unbalanced indentation

By the end of this lesson, you should be able to:

- Identify when a nested decision can be refactored

- Write flat decision chains that preserve the same logic

- Recognize and fix logical overlaps

---

### **Key Concepts**

#### **1. The Problem with Nested Decisions**

When decisions depend on multiple conditions, beginners often nest `if` statements like this:

```python
num = 7
if num > 5:
    if num % 2 == 1:
        print("odd and greater than 5")
    else:
        print("even and greater than 5")
else:
    print("5 or less")
```

Output:

```plaintext
odd and greater than 5
```

While this works, indentation increases with every condition. For longer programs, it becomes difficult to read and debug.

---

#### **2. The Role of** `elif`

`elif` means *else if*. It allows multiple conditions to be tested sequentially, reducing the need for deep nesting.

**Refactored Example:**

```python
num = 7
if num > 5 and num % 2 == 1:
    print("odd and greater than 5")
elif num > 5 and num % 2 == 0:
    print("even and greater than 5")
else:
    print("5 or less")
```

Output:

```plaintext
odd and greater than 5
```

**Benefits:**

- Cleaner structure

- Easier debugging

- Less indentation

- Each branch is mutually exclusive

---

#### **3. Ordering Conditions Correctly**

Condition order **matters**. Python checks from top to bottom and stops at the first `True` branch.

**Incorrect Example:**

```python
num = 2
if num > 5 and num % 2 == 1:
    print("odd and greater than 5")
elif num % 2 == 0:
    print("even and greater than 5")
elif num > 5 and num % 2 == 0:
    print("even and 5 or less")
else:
    print("odd and 5 or less")
```

Output:

```plaintext
even and greater than 5
```

This is wrong because the second `elif` catches even numbers before the specific condition is tested.

**Corrected Version:**

```python
num = 2
if num > 5 and num % 2 == 1:
    print("odd and greater than 5")
elif num > 5 and num % 2 == 0:
    print("even and greater than 5")
elif num % 2 == 0:
    print("even and 5 or less")
else:
    print("odd and 5 or less")
```

Output:

```plaintext
even and 5 or less
```

**Rule:**
Always order your conditions from **most specific → most general**.

---

#### **4. Using** `not in` **for Membership Tests**

`not in` checks whether an element is **absent** from a string or list.

**Example:**

```python
word = "lemon"
if "e" in word:
    print("'e' found")
elif "x" not in word:
    print("no 'x' found")
else:
    print("not sure")
```

Output:

```plaintext
'e' found
```

If we change the first condition:

```python
word = "lemon"
if "a" in word:
    print("'a' found")
elif "x" not in word:
    print("no 'x' found")
else:
    print("not sure")
```

Output:

```plaintext
no 'x' found
```

---

#### **5. Avoiding Common Errors**

| Error Type | Example | Explanation |
| --- | --- | --- |
| **Missing colon** | `if num > 5` | Every `if`, `elif`, and `else` must end with a colon (`:`). |
| **Indentation error** | `print("Hello")` not indented | The body of `if`, `elif`, and `else` must be indented (typically 4 spaces). |
| **Unreachable code** | General condition placed before specific | The interpreter stops checking once a `True` branch executes. |
| **Overlapping conditions** | `if num > 3`, then `elif num > 5` | The second condition will never run if the first already catches it. |

---

#### **6. Practice Example: Number Labels**

```python
num = 4
if num < 3:
    print("small")
elif num > 3:
    print("medium")
else:
    print("equal")
```

Output:

```plaintext
medium
```

Each number prints one label only. Always make conditions mutually exclusive.

---

#### **7. Refactoring Practice – Nested to Flat**

**Nested Version:**

```python
num = 5
if num % 2 == 0:
    if num > 3:
        print("even and big")
    else:
        print("even and small")
else:
    print("odd number")
```

**Flat (Refactored) Version:**

```python
num = 5
if num % 2 == 0 and num > 3:
    print("even and big")
elif num % 2 == 0 and num <= 3:
    print("even and small")
else:
    print("odd number")
```

Output:

```plaintext
odd number
```

---

### **Syntax Rules to Remember**

1. Each conditional line (`if`, `elif`, `else`) ends with `:`

2. Each block under a condition must be **indented** (typically 4 spaces)

3. Python evaluates conditions **top-down**

4. Use parentheses to group logical conditions if needed

5. Use `and`, `or`, and `not` to combine logic cleanly

---

### **Real-World Example**

Suppose you’re grading a test:

```python
score = 88

if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
elif score >= 60:
    print("D")
else:
    print("F")
```

Output:

```plaintext
B
```

Each condition runs in order. Once one matches, the rest are skipped.

---

### **Quick Reference: Conditional Operators**

| Operator | Meaning | Example | Result |
| --- | --- | --- | --- |
| `>` | Greater than | `5 > 3` | True |
| `<` | Less than | `5 < 3` | False |
| `>=` | Greater than or equal | `5 >= 5` | True |
| `<=` | Less than or equal | `2 <= 3` | True |
| `==` | Equal | `4 == 4` | True |
| `!=` | Not equal | `4 != 5` | True |
| `in` | Contains | `"e" in "lemon"` | True |
| `not in` | Does not contain | `"x" not in "lemon"` | True |

---

### **Tips for Mastery**

- Use **comments** to explain logic while learning.

- Write **simple print statements** after each branch to test flow.

- Refactor your old nested `if` code into `if/elif/else` chains.

- Always test edge cases (numbers at condition boundaries).

- Practice adding `not in`, `and`, and `or` in real scenarios.

---

### **Mini Practice Exercises**

**1. Temperature Check**

```python
temp = 72
if temp > 85:
    print("Hot")
elif temp > 60:
    print("Warm")
else:
    print("Cold")
```

**2. Login System**

```python
username = "Marco"
if username == "Admin":
    print("Welcome, Admin!")
elif username == "Guest":
    print("Welcome, Guest!")
else:
    print("Access Denied.")
```

**3. Fruit Check**

```python
fruit = "apple"
if "a" in fruit:
    print("Has an 'a'")
elif "z" not in fruit:
    print("No 'z' found")
else:
    print("Something else")
```

---

### **Summary**

- `elif` simplifies multiple conditions.

- Order conditions **from specific to general**.

- Avoid nested branches when one flat chain works.

- Always use proper **indentation and colons**.

- **Test every branch** to confirm logical equivalence.

---