
# Keeping it clean

**Date:** October 28, 2025

**Course**: CS101 - Computer Science Fundamentals

**Week**: 1, Lesson 04

## What You’ll Learn

This lesson tightens up code formatting so it reads smoothly and avoids silly errors. The focus is consistent indentation (4 spaces), clean spacing around operators and commas, sensible blank lines between sections, and predictable print behavior. You practiced fixing messy code line by line and saw how strict formatting makes your logic clearer.

**Core rules**

- **Indentation:** Always 4 spaces per level; never mix tabs.
- **Inline spacing:** One space around ‎⁠=⁠, ‎⁠+⁠, ‎⁠-⁠, ‎⁠*⁠, ‎⁠/⁠ and one space after commas.
- **Vertical spacing:** A single blank line between top-level sections (e.g., between functions and main code), not sprinkled inside simple loops.
- **Printing:** ‎⁠print()⁠ adds a newline by default; use ‎⁠end=" "⁠ to keep prints on the same line, and a blank ‎⁠print()⁠ to visually separate output blocks.

**Indentation: 4 spaces, every time**

“Bad indent” demo (worked in your environment but violates the style):

```python
if True:

print("bad indent!")   # 2 spaces

Correct style:if True:

print("bad indent!")  # 4 spaces
```

Multi-line fix exercise—cleaned loop and conditional:

```python
for i in range(2):

print("hello")

if i == 1:

print("done")
```

Why this matters: mixing widths or tabs eventually leads to ‎⁠IndentationError⁠, mis-scoped blocks, and painful debugging. Standardizing on 4 spaces keeps the structure obvious.

**Inline whitespace: operators and commas**

Ugly:total=2+3,4

Clean:total = 2 + 3, 4

Exercise line you corrected:result = 7 + 8, 9

Principle: if the code reads like a sentence, the reader won’t have to decode it.

**Vertical spacing: blank lines for structure**

Target layout (functions separated; loop not inside any function):

```python
def add(a, b):

return a + b

def mult(a, b):

return a * b

for i in range(2):

print(i)
```

Your final fix matched this: one blank line after each function; the loop sits at the left margin (top-level), and loop body is indented exactly 4 spaces.

**Printing behavior: newline vs inline**

Default (two lines):print("one")

print("two")

Inline with spacing:print("one", end=" ")

print("two")

Add a visible gap between output sections:print()  # blank line to separate output groups

You used this to separate loop output from the “one two” print, producing cleaner terminal logs.

**Full clean-up: temperature conversion block**

Messy starting point:

```python
def f_to_c(f):

return (f-32)*5/9

temps=[32,68,100]

for t in temps:

print(f"F:{t},C:{round(f_to_c(t),1)}" )
```

Step-by-step cleaned version:

```python
def f_to_c(f):

return (f - 32) * 5 / 9

temps = [32, 68, 100]

for t in temps:

print(f"F: {t}, C: {round(f_to_c(t), 1)}")

Observed output:
F:32, C:0.0

F:68, C:20.0

F:100, C:37.8
```

What improved:

- Consistent 4-space indents inside function and loop.
- Spaces around operators and after commas.
- One blank line between function and data setup.
- Legible f-string with spaces after labels (“F: ” and “C: ”).

**Pitfalls to avoid**

- **Tabs vs spaces:** mixing causes hidden bugs; standardize on spaces (4).
- **Under/over-indenting:** misaligns blocks, moving code into functions or out of loops accidentally.
- **Random blank lines:** only insert between logical sections; avoid gaps that fragment simple blocks.
- **Tight operators/commas:** ‎⁠a=1+2,3⁠ slows reading; use ‎⁠a = 1 + 2, 3⁠.
- **Inconsistent print formatting:** learn ‎⁠end=" "⁠ and blank ‎⁠print()⁠ for clean output.

**Quick reference (copy/paste)**# Functions separated by exactly one blank line

```python
def add(a, b):

return a + b

def mult(a, b):

return a * b

# Top-level code aligned left; loop body indented 4 spaces

for i in range(2):

print(i)

# Inline spacing style

total = 2 + 3, 4

nums = [1, 2, 3]

# Print formatting

print("one", end=" ")

print("two")

print()  # visual gap
```

Clean code is about reducing friction: fast scanning, fewer formatting bugs, and zero surprises when you come back later.