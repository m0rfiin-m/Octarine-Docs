
**Lesson 7: Decision Tables to Branching Logic**

**Course:** PY101 – Python Fundamentals
**Week:** 3
**Date:** October 30, 2025
**Status:** 📘 Completed

---

### **Overview**

This lesson teaches how to convert **decision tables** into **Python branching logic** using `if`, `elif`, and `else`.
Decision tables help organize multiple conditions clearly, showing all possible outcomes before you start coding.
You’ll learn how to translate each row into code, ensure **mutual exclusivity** (no overlapping conditions), and guarantee **completeness** (no missing cases).

By the end of this lesson, you will be able to:

- Read and interpret decision tables.

- Write clean `if/elif/else` chains that match table logic.

- Avoid unreachable or duplicate branches.

---

### **Key Concepts**

#### **1. Decision Tables**

A decision table lists all possible combinations of conditions and their results.
Each row represents a unique scenario that should map to one branch of code.

Example table:

| size | parity | label |
| --- | --- | --- |
| &gt;10 | even | Alpha |
| &gt;10 | odd | Beta |
| ≤10 | even | Gamma |
| ≤10 | odd | Delta |

Each row → one branch in your code.

---

#### **2. Translating Rows into Code**

Each row becomes a single condition in your `if/elif/else` chain.

```python
size = 12

if size > 10 and size % 2 == 0:
    print("Alpha")
elif size > 10 and size % 2 != 0:
    print("Beta")
elif size <= 10 and size % 2 == 0:
    print("Gamma")
else:
    print("Delta")
```

Output:

```plaintext
Alpha
```

---

#### **3. Mutual Exclusivity**

Each condition must be unique so only **one branch** runs per input.
If two conditions overlap, Python stops at the first match and skips the rest.

Example:

```python
if size > 10 and size % 2 == 0:
    print("Alpha")
elif size > 10 and size % 2 != 0:
    print("Beta")
```

Only one branch can run because both conditions cannot be true at the same time.

---

#### **4. Completeness**

Completeness means your logic covers every possible input.
If a value doesn’t match any condition, use `else:` as a catch-all.

```python
if size > 10 and size % 2 == 0:
    print("Alpha")
elif size > 10 and size % 2 != 0:
    print("Beta")
elif size <= 10 and size % 2 == 0:
    print("Gamma")
else:
    print("Delta")  # Handles anything not matched above
```

---

#### **5. Step-by-Step Translation**

1. Write the table.

2. Start with one condition.

3. Add each remaining row as an `elif`.

4. End with an `else` for completeness.

5. Test with different values.

Example:

```python
size = 8

if size > 10 and size % 2 == 0:
    print("Alpha")
elif size > 10 and size % 2 != 0:
    print("Beta")
elif size <= 10 and size % 2 == 0:
    print("Gamma")
else:
    print("Delta")
```

Output:

```plaintext
Gamma
```

---

#### **6. Common Errors**

| Error | Description | Fix |
| --- | --- | --- |
| Missing colon | Forgot `:` at end of condition | Add `:` after every `if`, `elif`, and `else` |
| Indentation error | Misaligned blocks | Use 4 spaces for indentation |
| Overlapping conditions | Two rows describe same case | Refine logic so each condition is unique |
| Missing case | Input not handled | Add an `else:` branch |

---

### **Practice Example**

Translate this decision table for **delivery fees**:

| distance (miles) | weight (kg) | fee label |
| --- | --- | --- |
| &lt;2 | &lt;5 | Mini |
| &lt;2 | ≥5 | Small |
| 2–10 | &lt;10 | Standard |
| 2–10 | ≥10 | Large |
| &gt;10 | any | Remote |

---

#### **Code Example**

```python
distance = 1
weight = 3

if distance < 2 and weight < 5:
    print("Mini")
elif distance < 2 and weight >= 5:
    print("Small")
elif 2 <= distance <= 10 and weight < 10:
    print("Standard")
elif 2 <= distance <= 10 and weight >= 10:
    print("Large")
elif distance > 10:
    print("Remote")
else:
    print("not there")
```

**Output:**

```plaintext
Mini
```

---

#### **Test the Logic**

| distance | weight | Expected Output |
| --- | --- | --- |
| 1 | 3 | Mini |
| 1 | 6 | Small |
| 5 | 7 | Standard |
| 5 | 15 | Large |
| 12 | 5 | Remote |

---

### **7. Debugging Incomplete Logic**

If you remove or miss a branch, some cases won’t run.
Example (missing “odd small” case):

```python
size = 1
if size > 10:
    print("Alpha")
elif size == 10:
    print("Beta")
```

Output: *(no output)*

Fix with an `else:`:

```python
else:
    print("No match")
```

---

### **8. Quick Syntax Rules**

- Every condition ends with a colon `:`

- Every code block is indented 4 spaces

- `elif` = “else if”

- Only one branch runs per input

- Use `and`, `or`, `not` for multiple checks

- Always test **edge cases**

---

### **9. Mini Challenge**

Create a table for grading:

| Score Range | Grade |
| --- | --- |
| 90–100 | A |
| 80–89 | B |
| 70–79 | C |
| 60–69 | D |
| &lt;60 | F |

Write code:

```python
score = 82

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

---

### **Summary**

- A decision table lists all conditions and their outcomes.

- Translate each row into one `if` or `elif`.

- Always keep logic **mutually exclusive** and **complete**.

- Order from **specific → general**.

- Test different values to verify all paths work.

- Use `else` as a safety net for missing conditions.

---

Would you like me to prepare **Lesson 8** in the same Markdown format once you unlock it?