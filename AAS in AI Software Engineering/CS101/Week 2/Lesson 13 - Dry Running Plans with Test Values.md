
# **Dry Running Plans with Test Values**

**Why it matters**

Dry runs catch logic bugs fast without writing or running code. It’s lightweight and practical—use it to validate your plan before you implement.

**How to Dry Run**

- Pick a row from your test table.
- Walk through each pseudocode step using that row’s inputs.
- Track intermediate variables in a simple table.
- Compare the final result to the expected output.

**Bucket Years (uses floor division and a dictionary)**

Pseudocode steps:

	1. Compute bucket = years // 5

	2. label = labels.get(bucket, “invalid”)

	3. return label

Dry run row: years = 7

| step |  | variable |  | value |  |
| --- | --- | --- | --- | --- | --- |
| 1 |  | years |  | 7 |  |
| 2 |  | bucket |  | 7 // 5 = 1 |  |
| 3 |  | label |  | labels.get(1) = “child” |  |
| Result: “child” → matches expected. |  |  |  |  |  |

Edge check: years = 15 → 15 // 5 = **3**. If 3 isn’t in the dictionary, ‎⁠.get(3, "invalid")⁠ returns **“invalid”**.

Invalid check: years &lt; 0 → return **“invalid”** immediately.

**Clip(value, lower, upper)**

Rules:

- If value &lt; lower → return lower
- Else if value &gt; upper → return upper
- Else → return value

Dry run row: 8, 5, 12

- 8 &lt; 5 → false
- 8 &gt; 12 → false
- Return **8**

Edge row: 5, 5, 12 → 5 &lt; 5 false; 5 &gt; 12 false → return **5**

Invalid bounds: lower &gt; upper (e.g., 7, 10, 4)

- 7 &lt; 10 → true → would return 10, but the plan is invalid. Flag the row as **invalid** before checks.

**Common Pitfalls**

- **Off-by-one:** confirm boundary inclusivity.
- **Floor division:** a // b truncates down.
- **Missing keys:** always use ‎⁠.get(..., "invalid")⁠.
- **Bad inputs:** define invalid early (negative years, non-numeric, lower &gt; upper).

**Minimal Templates**

Test table headers:

```python

Input (years) | Expected bucket | Expected label

value | lower | upper | expected result
```

Dry run tracker:

```python
step | variable | value
```

**What to do**

- Dry run one normal, one edge, one invalid per function.
- Stop as soon as you hit an invalid condition.
- If expected ≠ result, fix the pseudocode before coding.