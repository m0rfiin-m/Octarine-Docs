
# Making sure nothing breaks

**Date:** Sunday, November 16, 2025
**Course:** CS101 - AAS in AI Software Engineering
**Week:** 1,  Lesson 16 
**Lesson:** Making sure nothing breaks

**What You’ll Learn**

- **Regression mindset:** After a refactor, re-run tests to confirm behavior didn’t change.
- **Mini test suite:** Use simple ‎⁠assert⁠ lines as lightweight tests.
- **Green runs:** If asserts don’t raise errors and output matches, your refactor is safe.
- **Refactor discipline:** Rename variables and clean code without touching logic.
- **Coverage basics:** Test normal cases and common pitfalls (length, types).

**Core Ideas**

- Keep tests close to code. Place ‎⁠assert⁠ checks at the bottom for sanity.
- A “green” run means all asserts pass; no exceptions thrown.
- Regression tests ensure old behavior still works after changes.
- Cosmetic changes (like renaming ‎⁠row⁠ to ‎⁠record⁠) shouldn’t alter results.

**Reference Snippet**

```python
def format_line(record):

    assert len(record) == 3

    print(record[0], "-", record[1], record[2])



record1 = ["Sam", "30", "A+"]

b = ["Pat", "45", "B"]

x = [record1, b]



for record in x:

    format_line(record)



assert record1 == ["Sam", "30", "A+"]
```

**Common Pitfalls**

- Asserting the wrong thing: ‎⁠assert len(record1) == ["Sam", "30", "A+"]⁠ is invalid.
- Shadowing loop variables: final ‎⁠record⁠ equals the last item from the loop.
- Missing rename spots: ensure all ‎⁠row⁠ → ‎⁠record⁠ changes are complete.
- Skipping the re-run: tests only prove safety if you execute them after changes.

**Quick Practice**

- Add one more assert: verify ‎⁠b == ["Pat", "45", "B"]⁠.
- Break it intentionally (change one value) and confirm an ‎⁠AssertionError⁠ fires.
- Revert the change; confirm a green run.

**Why Good Naming Matters**

- Clear names reduce mental overhead and mistakes during refactors.
- Consistent naming keeps tests readable and catches mismatches fast.
- Better names make “cosmetic” refactors safer by minimizing logic risk.