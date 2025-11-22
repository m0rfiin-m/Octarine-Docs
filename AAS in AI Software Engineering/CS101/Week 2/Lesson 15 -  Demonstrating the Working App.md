
**Demonstrating the Working App**

**Objective**

Prove your app works across multiple inputs using a simple test harness: functions, loops, asserts, and clear output. No advanced topics.

**What to Demonstrate**

- Validates input correctly (0–120, digits only after strip).
- Buckets with floor division and maps via dictionary.
- Formats output cleanly.
- Runs multiple test cases automatically and reports pass/fail.

**Core Functions**

```python
def read_years(txt):

s = txt.strip()

if s == "" or not s.isdigit():

return None

years = int(s)

return years if 0 <= years <= 120 else None

def bucket_years(years):

lookup = {0:"infant", 1:"child", 2:"teen", 3:"adult", 4:"legend"}

return lookup.get(years // 5, "invalid")

def format_message(years, label):

return f"{years}-year-old → {label}"
```

**Test Harness (Loop + Asserts**)

```python
tests    = ["0", "7", "15", "25", "-2", " 8 ", "121", ""]

expected = [0,    7,   15,   25,  None,   8,    None, None]

for raw, want in zip(tests, expected):

got = read_years(raw)

assert got == want, f"{raw} → {got} (expected {want})"

print("read_years: all tests passed")
```

**End-to-End Demo Loop**cases = ["7", "15", "20", "40", "-3"]

for raw in cases:

yrs = read_years(raw)

if yrs is None:

print(f"{raw} → invalid")

else:

print(format_message(yrs, bucket_years(yrs)))

**Categories to Cover**

- Normal: inside bounds (e.g., 7 → child).
- Edge: boundaries and exact multiples of 5 (e.g., 15 → adult).
- Invalid: negatives, blanks, non-digits, &gt;120.

**Rules to Remember**

- Floor division: years // 5 truncates down.
- Safe dictionary lookup: ‎⁠.get(bucket, "invalid")⁠.
- Use asserts to auto-check expected vs. actual.

**Common Pitfalls**

- Off-by-one on bounds (make 0 and 120 inclusive).
- Forgetting ‎⁠strip()⁠ before digit check.
- Mapping ages beyond defined buckets → expect “invalid”.
- Mismatched test and expected list lengths in harness.

**Minimal Driver**raw = input("age in years: ")

yrs = read_years(raw)

if yrs is None:

print("invalid age")

else:

print(format_message(yrs, bucket_years(yrs)))