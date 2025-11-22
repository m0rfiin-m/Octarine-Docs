
# **Integrating Logic into a Full App**

**Goal**

Connect validated inputs, business logic, and clean output into a single, runnable flow. Use the pieces you already built: input validation, bucketing with floor division, dictionary lookups, and formatted messages.

**What You’ll Build**

- Read and validate an age string.
- Compute a bucket with years // 5.
- Map bucket to a label using a dictionary.
- Print a formatted message.

**Allowed vs. Forbidden**

- Allowed: functions, input validation, loops, dictionary lookups, dry runs, test tables, formatted output.
- Forbidden: classes, files, pipelines, subproblem sequencing, anything beyond this unit.

**Core Functions**

```python
# 1) Validate input into an int age or None

def read_years(txt):

    s = txt.strip()

    if s == "":

        return None

    if not s.isdigit():  # reject negatives/letters

        return None

    years = int(s)

    if 0 <= years <= 120:

        return years

    return None
```

```python
# 2) Bucket years to a label via floor division and dictionary

def bucket_years(years):

    lookup = {

        0: "infant",  # 0-4

        1: "child",   # 5-9

        2: "teen",    # 10-14

        3: "adult",   # 15-19

        4: "legend",  # 20-24

    }

    bucket = years // 5

    return lookup.get(bucket, "invalid")

```

```python
# 3) Pretty output

def format_message(years, label):

    return f"{years}-year-old → {label}"

```

**The Driver (App Flow)**

```python
raw = input("age in years: ")

years = read_years(raw)

if years is None:

    print("invalid age")

else:

    label = bucket_years(years)

    print(format_message(years, label))
```

**Quick Test Sweep**

Dry-run first, then run code. Cover normal, edge, invalid.

```python
tests = ["7", "15", "-2", " 20 ", "121", ""]

for raw in tests:

    years = read_years(raw)

    if years is None:

        print(raw, "→ invalid")

    else:

        print(format_message(years, bucket_years(years)))
```

Expected vibes:

- Normal: 7 → child
- Edge: 15 → adult (since 15 // 5 = 3)
- Legend example: 20 → legend
- Invalid inputs: blanks, negatives, &gt;120, non-digits → “invalid age”

**Dry Run Reminder**

- Floor division: years // 5 truncates down.
- Safe lookup: ‎⁠.get(bucket, "invalid")⁠ prevents KeyErrors.
- Early exit on invalid input keeps the flow clean.

**Common Pitfalls**

- Off-by-one on bounds (inclusive checks for 0–120).
- Forgetting to ‎⁠strip()⁠ before validating.
- Using the wrong variable for ‎⁠int()⁠ (convert the validated string).
- Mapping beyond defined buckets → expect “invalid”.

**Minimal Template (Copy/Paste Starter)**

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



def main():

    raw = input("age in years: ")

    years = read_years(raw)

    if years is None:

        print("invalid age")

        return

    label = bucket_years(years)

    print(format_message(years, label))



if name == "__main__":

    main()
```

**Study Plan**

- Build a small test table (normal, edge, invalid) and dry-run each row.
- Run your app with the same values; compare outputs to the table.
- Fix any mismatches in validation or bucketing before adding features.