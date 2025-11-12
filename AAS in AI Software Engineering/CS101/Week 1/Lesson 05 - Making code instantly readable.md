
Making code instantly readable,” with examples and a checklist.

**What “Readable Code” Means**

Readable code is code another developer can understand fast. You’ll use consistent structure, clear naming, and minimal friction so scanning and editing feel effortless.

**Readability Checklist (6 Checks)**

- **Indentation: 4 spaces** per level; no tabs mixing.
- **Blank lines:** Separate major blocks (docstring, comments, loops, conditionals).
- **Spacing:** Spaces after commas; around operators (=, +, &gt;); inside f-strings where it helps readability.
- **Names:** Use **descriptive variables** (avoid single letters when context isn’t obvious).
- **Comments:** Write **purposeful “why”** comments; avoid narrating the obvious “what.”
- **Docstring:** Add a short, top-level docstring for scripts or function docstrings inside defs.

**Core Patterns From the Lesson**

- Top-level docstring:"""

Prints numbers 0 to 4, separated by commas.

"""

- Purposeful comment (explains intent):# Loop intended to show the number range from 0–4

- Clean loop and print:for count in range(5):

print(count, end=",")

- Clean f-string spacing:print(f"val: {i}")   # prefer space after colon for clarity

- Clean conditional blocks:if x &gt; 5:

print("done")

**Common Fixes You Practiced**

- Move one line at a time; run after each change.
- Add spaces: ‎⁠x = 10⁠, ‎⁠range(0, x + 1)⁠, `end=”,”
- Rename variables for clarity: ‎⁠i⁠ → ‎⁠count⁠, ‎⁠a⁠ → ‎⁠index⁠
- Split cramped lines: ‎⁠if y &lt; 10: print("small")⁠ → two lines with proper indent.
- Close quotes in f-strings and keep formatting consistent.

**Mini Drills**

- Drill 1: Rewrite ‎⁠for i in range(5):print(i,end=",")⁠ using all six checks.
- Drill 2: Convert ‎⁠if y&gt;2:print("big")⁠ to a clean two-line block.
- Drill 3: Add a top-level docstring, then one blank line, then code. No functions needed for a file-level docstring.

**Pitfalls to Avoid**

- Mixing tabs and spaces
- Missing closing quotes in f-strings
- Commenting the obvious (“prints i”) instead of explaining intent
- Docstring placed inside the wrong scope or floating mid-file
- Overusing single-letter names that hide meaning

**Quick Self-Review Routine**

- Scan indentation visually.
- Check spacing around commas/operators.
- Read variable names out loud—do they explain themselves?
- Ensure at least one “why” comment per non-trivial block.
- Docstring present and concise.
- Run the code after each single-line fix to catch errors early.

**Final Example (Clean and Passes All 6)**"""

Demo: print labeled values and simple size checks.

"""

# Print 0–10 labeled values

```python
x = 10

for i in range(0, x + 1):

print(f"val: {i}")

print()

```

# Range demo 1–(y + 1)

```python
y = 5

for index in range(1, y + 2):

print(f"Y: {index}")

if y > 2:

print("big")

if y < 10:

print("small")
```