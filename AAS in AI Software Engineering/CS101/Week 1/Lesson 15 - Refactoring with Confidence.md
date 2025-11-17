
# Refactoring with confidence

**Date:** Sunday, November 16, 2025
**Course:** CS101
**Week:** 1, Lesson 15

You cleaned code safely by making small, testable moves and checking output after each change. You practiced consistent renaming, extracting a function, deleting dead code, and adding guard asserts to protect assumptions. The goal: keep behavior identical while improving readability and reliability.

**Why good naming matters**

Clear, specific names reduce mental load and mistakes. Renaming ‎⁠a⁠ to ‎⁠row1⁠ and using ‎⁠row⁠ in loops makes intent obvious, which makes refactors safer and faster.

**Key concepts**

- Safe refactor rhythm: change one thing, run, verify output (green line).
- Systematic rename: update every reference, avoid NameError.
- Extract function: move a behavior into a well‑named function, then call it.
- Delete dead code: remove unused blocks after confirming no behavior change.
- Guard asserts: enforce assumptions early (like row length) to catch bad states.

**Reference patterns**

```python
# Before

a = ["Sam", "30", "A+"]

b = ["Pat", "45", "B"]

x = [a, b]

for q in x:

    print(q[0], "-", q[1], q[2])



# After: rename + extract + guard

def format_line(row):

    assert len(row) == 3

    print(row[0], "-", row[1], row[2])



row1 = ["Sam", "30", "A+"]

b = ["Pat", "45", "B"]

x = [row1, b]

for row in x:

    format_line(row)

```

**Safe refactor checklist**

- Rename everywhere, then run.
- Extract function, place definition above use, then run.
- Delete unused code, then run.
- Add asserts to protect invariants, then run with bad input to confirm failure.

**Common fixes you nailed**

- Removed unreachable returns and stray prints.
- Replaced direct prints in loops with a single function call.
- Caught invalid rows with an assert on length.