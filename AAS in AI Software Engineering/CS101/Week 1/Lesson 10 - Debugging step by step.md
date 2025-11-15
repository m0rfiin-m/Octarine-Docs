
**Core idea:** Use a consistent checklist to isolate, verify, fix, and clean up bugs fast.

**The 6-step checklist**

- **Reproduce:** Run the exact code path that breaks. No guessing.
- **Read output/errors:** Parse the message and the unexpected values.
- **Trace with prints:** Add one targeted ‎⁠print()⁠ to expose state.
- **Narrow scope:** Add more prints or a single ‎⁠assert⁠ to pinpoint the line.
- **Fix and test:** Change the minimal thing, re-run the failing path.
- **Clean up:** Remove debug prints/asserts once green.

**Demo bug: list aliasing vs copying**

```python
original = [1, 2, 3]

copied = original         # alias; same object

copied.append(4)

print("original:", original)  # -> [1, 2, 3, 4]

print("copied:", copied)      # -> [1, 2, 3, 4]

# Check identity:

print(id(original), id(copied))  # same IDs → aliasing

# Fix with a copy:

#copied = original[:]             # or original.copy()
```

**Patterns to trace and verify**

- **Accumulator sanity:** After a loop, ‎⁠assert total &gt;= 0⁠ or print intermediate totals.
- **Input/Output shape:** ‎⁠assert len(out) == len(inp)⁠ after transformations.
- **Identity vs equality:** Use ‎⁠is⁠ for identity, ‎⁠==⁠ for value equality; print ‎⁠id()⁠ when confused.
- **State changes:** Trace variable before/after mutation lines.

**Minimal debugging toolkit**

- ‎⁠print("x=", x)⁠ to expose values at key lines.
- ‎⁠assert condition⁠ to fail fast when invariants break.
- ‎⁠id(obj)⁠ to confirm aliasing.
- Small, repeatable inputs to reproduce quickly.

**Common pitfalls**

- Fixing symptoms instead of the root cause.
- Adding prints everywhere; focus on the suspected line.
- Leaving debug code in production.
- Confusing reassignment with copying for lists and dicts.
- Calling functions before they’re defined or returning inside loops unintentionally.

**Quick drills**

- Introduce a bug (double an update), confirm with assert, then fix.
- Trace a loop with an accumulator and verify final total with an assert.
- Show ‎⁠id(a) == id(b)⁠ for ‎⁠b = a⁠, then make them different with a copy and re-check.

**Obsidian notes (minimal)**

- Checklist: reproduce → read → trace → narrow → fix → clean.
- Aliasing bug: assignment shares objects; copy separates.
- Use targeted prints and asserts, then remove them.