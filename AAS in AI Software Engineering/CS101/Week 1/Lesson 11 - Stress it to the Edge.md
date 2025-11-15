
**Study Guide: Stress it to the edge**

**Core idea:** Test beyond “normal.” Cover typical inputs, edge boundaries, and clearly invalid inputs to expose hidden bugs fast.

**Three-point test coverage**

- **Normal case:** Typical, expected input produces expected output.
- **Edge case:** Boundary values that sit on the limits, like **0**, empty lists/strings, min/max numbers, exact equals to bounds.
- **Invalid input:** Types or values your function isn’t meant to handle (strings where numbers are expected, None, zero as a divisor). Errors here are still valid test results.

**Demo patterns from the lesson**

```python
def clip(value, lower, upper):

    if value < lower: return lower

    if value > upper: return upper

    return value



# Normal + edges

print(clip(5, 0, 10))   # 5

print(clip(0, 0, 10))   # lower bound → 0

print(clip(10, 0, 10))  # upper bound → 10



# Invalid (type mismatch)

print(clip("hi", 0, 10))  # TypeError by design

# Equality vs identity (for list tests)

nums = [1, 2, 3]

clone = nums[:]

print(nums == clone)  # True (same contents)

print(nums is clone)  # False (different objects)

def safe_divide(a, b):

    return a / b



print(safe_divide(10, 2))  # 5.0 normal

print(safe_divide(10, 0))  # ZeroDivisionError edge

print(safe_divide(None, 5))# TypeError invalid
```

**Checklist you can reuse**

- Define the function’s contract (inputs, outputs, boundaries).
- Write one test per category: **normal**, **edge**, **invalid**.
- Run, read outputs/errors, and keep tests small and isolated.
- Clean up prints when done; keep failing cases documented.

**Edge inputs to remember**

- Numbers: **0**, negatives, very large, exact bounds (lower/upper).
- Collections: empty list, single-item list, duplicates, large list.
- Strings: empty “”, whitespace-only, very long, non-ASCII.

**Common pitfalls**

- Only testing happy paths.
- Assuming equality implies identity; use ‎⁠is⁠ only for identity checks.
- Treating errors as failures rather than expected results for invalid inputs.
- Forgetting boundary equality checks (value == lower/upper).

**Quick drills**

- Add edge tests to any function you write: exact bounds, empty input, zero.
- For list-processing functions, test empty list and verify output shape.
- For math functions, include zero and negative numbers; confirm behavior.
- Capture and note the exact error message for invalid inputs.

**Obsidian notes (minimal)**

- Rule of three: normal • edge • invalid.
- Boundaries matter: test equals at lower/upper.
- Equality vs identity: ‎⁠==⁠ vs ‎⁠is⁠.
- Errors on invalid input = covered behavior.