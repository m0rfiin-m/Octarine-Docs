
# **Creating Test Tables for Pseudocode Plans**

Date: Saturday, November 22, 2025

Course: CS101 – AAS in AI Software Engineering

Week: 2, Lesson 12

**What You’re Building**

A test table lists inputs and expected outputs before any code runs. It validates logic quickly and catches mistakes early.

**Core Concepts**

- **Pseudocode hierarchy:** high-level steps → sub-steps → details.
- **Tables cover cases:** normal, edge, invalid.
- **Safe dictionary lookups:** use ‎⁠.get(key, default)⁠ to avoid errors.
- **Floor division:** use ‎⁠//⁠ for bucket calculations.

**Bucket Years Example**

High-level steps:

```python
# 1. Calculate which bucket (0, 1, 2, …)

# 2. Figure out the age label from a dictionary

# 3. Return label (or “invalid” if not found)

Table:

Input (years) | Expected bucket | Expected label

7             | 1               | kid

15            | 3               | adult

20            | 4               | legend

-3            | invalid         | invalid
```

Notes:

- Bucket rule: years // 5.
- Use labels.get(bucket, “invalid”).

**Clip Function Example**

Spec:

- Return value if lower ≤ value ≤ upper.
- Return lower if value &lt; lower.
- Return upper if value &gt; upper.

```python
Table:

value | lower | upper | expected result

5     | 2     | 8     | 5      # inside

3     | 1     | 5     | 3      # inside, upper edge

2     | 2     | 8     | 2      # lower edge

-1    | invalid | invalid | invalid
```

Notes:

- Treat bad bounds (lower &gt; upper), non-numeric, or missing values as invalid.

**How to Design a Test Table**

1. Define inputs and outputs clearly.
2. Add rows for:
   - Normal: typical values.
   - Edge: boundaries and exact multiples.
   - Invalid: negatives, strings, bad ranges.
3. Annotate any assumptions (e.g., bucket size is 5).
4. Keep it minimal but complete.

**Dry-Run Workflow**

- Trace each row manually against pseudocode.
- Compare actual trace with expected output.
- Fix logic before writing code.

**Common Pitfalls**

- **Off-by-one:** inclusive vs exclusive bounds.
- **Floor division mistakes:** remember ‎⁠//⁠ truncates down.
- **Dictionary misses:** use ‎⁠.get()⁠ with a default.
- **Ambiguous invalids:** explicitly define what “invalid” means.

**Quick Templates**

```python
Headers:
Input | Expected output

Bucket years:
Input (years) | Expected bucket | Expected label

Clip:
value | lower | upper | expected result
```

**Practice Checklist**

- Covers normal, edge, invalid.
- Uses floor division correctly.
- Uses ‎⁠.get(..., "invalid")⁠ for lookups.
- Notes assumptions and rules.