
**Study Guide: Pushing the limits**

**Core idea:** Define strict input/output boundaries and test the extremes. Clamp when necessary. Prove behavior with asserts. Verify copy vs alias to avoid hidden mutations.

**What you’ll learn**

- **Boundary design:** Functions should specify output limits (e.g., 0–100) and enforce them.
- **Three-case coverage:** Test **normal**, **edge**, and **invalid** inputs; errors in invalid paths are expected behavior.
- **Assertions as guardrails:** Place asserts right after the code that could break the contract.
- **Equality vs identity:** ‎⁠==⁠ compares values; ‎⁠is⁠ checks same object. Slicing makes copies; assignment makes aliases.

**Canonical examples**

```python
```

# Clamp to [0, 100]

def bounded_percent(x):

    if x &lt; 0: return 0

    if x &gt; 100: return 100

    return x

tests = [0, 50, 100, -5, 105]

for x in tests:

    y = bounded_percent(x)

    if x in (0, 50, 100):

        assert y == x

    else:

        assert y == (0 if x &lt; 0 else 100)

# Copy vs alias

a = [1, 2, 3]

b = a[:]      # copy

c = a         # alias

b.append(99)

assert a  ==[1, 2, 3] and b==  [1, 2, 3, 99]

c.append(42)

assert a == [1, 2, 3, 42] and c is a

**Edge inputs to include**

- Numbers: **0**, negatives, exact bounds, very large values.
- Collections: empty list, single-item, duplicates.
- Strings: empty “”, whitespace, long/non-ASCII.

**Debugging and tests workflow**

- Reproduce → read output/errors → add a targeted print/assert → narrow → fix → clean up.
- Keep tests small and isolate boundary checks with asserts.
- Document expected errors for invalid inputs.

**Common pitfalls**

- Only testing happy paths.
- Forgetting exact-bound equality checks.
- Mixing up ‎⁠==⁠ and ‎⁠is⁠, causing copy/alias bugs.
- Leaving debug prints and asserts in final code unintentionally.

**Obsidian notes (minimal)**

- Boundaries: define and clamp outputs.
- Coverage: normal • edge • invalid.
- Identity vs equality: slicing copy vs assignment alias.
- Assert after mutation; clean up when done.