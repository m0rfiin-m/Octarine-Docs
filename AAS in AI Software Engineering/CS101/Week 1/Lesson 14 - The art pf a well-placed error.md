
# The art of a well‑placed error

**Date:** Sunday, November 16, 2025

**Course :** CS101

**Week:** 1, Lesson 14

## What You’ll Learn

You built guard checks that validate inputs early, used ‎⁠assert⁠ to stop on bad states, and compared that to returning **None** as a sentinel to keep programs running. You practiced cleaning text, numeric checks, range checks, and parsing floats that include a leading minus or decimal.

**Why Good Naming Matters**

Clear variable names make rules readable and debugging faster. When code says ‎⁠0 &lt;= num &lt;= 100⁠ or ‎⁠value = float(txt)⁠, the intent is obvious and errors are easier to trace.

**Key Concepts**

- Guard checks placed immediately after input cleanup.
- Assert stops execution when a rule fails.
- Sentinel return (None) signals invalid input without crashing.
- ‎⁠strip()⁠ before checks and conversions.
- ‎⁠isdigit()⁠ rejects ‎⁠-⁠ and ‎⁠.⁠, so use float parsing or shape cleaning.
- Chained comparisons for ranges: ‎⁠0 &lt;= num &lt;= 100⁠.

**Reference Patterns**

```python
# Percent in [0, 100], string input

def safe_percent(txt):

    txt = txt.strip()

    if txt.isdigit():

        num = int(txt)

        if 0 <= num and num <= 100:

            return num

    return None
```

```python
# Divide with an assert guard

def divide(a, b):

    assert b != 0

    return a / b
```

```python
# Age with two asserts (numeric shape, then range)

def read_age(text):

    text = text.strip()

    assert text.isdigit()

    num = int(text)

    assert 0 <= num <= 120

    return num
```

```python
# Temperature as float with asserts

def parse_temperature(txt):

    txt = txt.strip()

    cleaned = txt.replace('-', '', 1).replace('.', '', 1)

    assert cleaned.isdigit()

    value = float(txt)

    assert -90.0 <= value <= 60.0

    return value
```

**Assert vs. Sentinel**

- Assert: fail fast during development or when invalid input must stop.
- Sentinel (None): keep running and handle invalid input downstream.

**Common Fixes You Nailed**

- Corrected range logic to ‎⁠0 &lt;= num and num &lt;= 100⁠.
- Tested with strings, not integers, since integers don’t have ‎⁠strip()⁠.
- Allowed decimals/negatives by cleaning ‎⁠-⁠ and ‎⁠.⁠ before checks or by using ‎⁠float()⁠.