
# Validating inputs before they break things

**Core idea:** Block bad input early. Check type, range, and membership; fail fast or return a safe value.

**What you’ll learn**

- **Guards with assert:** Stop execution when a precondition is violated. Example: ‎⁠assert b != 0⁠ before division.
- **Type checks:** Use ‎⁠str.isdigit()⁠ before ‎⁠int(...)⁠ to avoid crashes.
- **Range checks:** Enforce bounds like **0–120** for age or **0–100** for percent.
- **Membership checks:** Only allow known options, e.g., ‎⁠choice in {"y","n"}⁠.
- **Safe returns:** Return ‎⁠None⁠ for invalid data to handle it gracefully upstream.

**Canonical examples**

```python
# Guard before dangerous op

def divide(a, b):

    assert b != 0

    return a / b



# Validate age input

def read_age(text):

    text = text.strip()

    if text.isdigit():

        num = int(text)

        if 0 <= num <= 120:

            return num

    return None



# Percent validator

def safe_percent(txt):

    txt = txt.strip()

    if txt.isdigit():

        num = int(txt)

        if 0 <= num <= 100:

            assert 0 <= num <= 100

            return num

    return None
```

**Test coverage you should practice**

- **Normal:** valid number inside bounds.
- **Edge:** exact bounds (e.g., 0 and 100).
- **Invalid:** non-digits, negatives, out-of-range, floats in strings (“99.5”).

**Quick drill ideas**

- Add ‎⁠assert⁠ right after each validation to lock invariants.
- Accept ‎⁠"42%"⁠: ‎⁠txt.strip().rstrip("%").strip()⁠ then apply range.
- For choices, normalize: ‎⁠choice.strip().lower()⁠ before membership.

**Common pitfalls**

- Calling ‎⁠int(txt)⁠ without ‎⁠isdigit()⁠ first.
- Forgetting edge equality checks (0, max).
- Mixing printing with returning; prefer returning then print outside.
- Using ‎⁠is⁠ for value comparison; use ‎⁠==⁠ for equality.

**Obsidian notes (minimal)**

- Guards: assert preconditions early.
- Validation: digit → int → range → return or None.
- Coverage: normal • edge • invalid.
- Keep functions pure: validate + return, no prints inside.