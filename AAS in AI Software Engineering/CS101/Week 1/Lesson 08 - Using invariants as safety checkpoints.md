
**Study Guide: Using invariants as safety checkpoints**

**Core idea:** An invariant is a fact in your program that must always be true while the code runs. You use ‎⁠assert⁠immediately after the code that could break it to catch bugs early.

**Key patterns from the lesson**

- **Running sum invariant:** After adding i to total, ‎⁠assert total == (i * (i + 1)) // 2⁠. This matches the closed-form for 1 + … + i.
- **Placement matters:** Put ‎⁠assert⁠ right after the mutation (e.g., the ‎⁠total += i⁠ line).
- **Fail fast:** A wrong update (like ‎⁠total += i * 2⁠) triggers an ‎⁠AssertionError⁠, proving the invariant broke.
- **Function-level invariant:** In ‎⁠square_list(numbers)⁠, after building ‎⁠squares⁠:
  - ‎⁠assert len(squares) == len(numbers)⁠ ensures one output per input.
  - ‎⁠assert sum(squares) &gt; 0⁠ adds a semantic check for positive totals in the given example.
- **Clean up:** Remove asserts when you’re done testing, or keep them guarded for dev-only runs.

**Code you should remember**

```python
# Loop invariant

total = 0

for i in range(1, 6):

    total += i

    assert total == (i * (i + 1)) // 2

    print("i =", i, "total =", total)



# Function invariants

def square_list(numbers):

    squares = []

    for n in numbers:

        squares.append(n * n)

    assert len(squares) == len(numbers)

    assert sum(squares) > 0

    return squares



print(square_list([2, 3, 4]))

```

**Common pitfalls**

- Wrong formula: ‎⁠(i * 1) // 2⁠ or extra parentheses causes false checks or syntax errors.
- Misplaced commas or string formatting in ‎⁠print⁠.
- Changing update logic without updating the invariant (e.g., doubling values but keeping the single-sum formula).

**How to use invariants in your own code**

- After every state change, ask: “What must still be true?” Then assert it.
- Prefer simple, cheap checks tied directly to the mutation you just made.
- In collections:
  - Length relationships: ‎⁠assert len(outs) == len(ins)⁠
  - Membership/ordering constraints
  - Aggregate rules: ‎⁠assert sum(...)⁠, ‎⁠assert all(...)⁠
- In numeric algorithms:
  - Range bounds: ‎⁠assert 0 &lt;= x &lt;= 1⁠
  - Monotonicity: ‎⁠assert prev &lt;= curr⁠
  - Conservation: totals or counts remain consistent

**Practice drills (quick reps)**

- Change the ‎⁠range(1, 6)⁠ to ‎⁠range(1, n+1)⁠ and keep the invariant working for any n.
- Intentionally break the update (multiply by 3) and confirm the assert fires.
- Add ‎⁠assert all(s &gt;= 0 for s in squares)⁠ to the function and test with negatives.

**Obsidian notes (minimal)**

- Definition: invariant = must-always-true program fact.
- Rule: place assert immediately after mutation.
- Loop sum formula: i(i+1)/2 as integer division.
- Function checks: size parity, aggregate sanity.
- Remove asserts post-testing or guard them.