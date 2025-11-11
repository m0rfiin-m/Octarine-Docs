
**Writing comments with real purpose**

This lesson teaches how to write comments that explain the why behind code, not restate the obvious. Comments are for humans, not the interpreter, and should reveal intent, constraints, and reasoning.

**Core principle**

Write comments that add insight. If a comment only repeats the code, it’s noise. Good comments explain the decision, tradeoff, or context so future you (or a teammate) understands why the code exists that way.

**Comments vs. Docstrings**

- **Docstrings:** Live inside triple quotes under a function; describe purpose, usage, parameters, returns. They’re visible via ‎⁠help()⁠ and used by tooling.
- **Comments:** Inline or above code; capture reasoning, context, assumptions, and non-obvious decisions.

Use docstrings for public API clarity; use comments to explain implementation choices.

**Example: Useless vs. Useful comments**

Original code with “useless” comments:

```python
def add_one(n):

# add 1

result = n + 1

# return value

return result

x = add_one(4)

# print result

print(x)
```

Better reasoning comment:

```python
def add_one(n):

# Off-by-one guard so a loop later hits the final index.

result = n + 1

return result

```

Why this works:

- **Explains intent** (avoiding off-by-one), not what ‎⁠+ 1⁠ does.

**Micro‑exercise: Border width reasoning**

```python
Prompt:title = "Welcome"

width = len(title) + 4

border = "=" * width

print(border)

print(title)

print(border)
```

Your improvement:

```python
title = "Welcome"

width = len(title) + 4

# Pad title with 2 spaces on each side; border must cover the full width.

border = "=" * width

print(border)

print(title)

print(border)
```

Key idea:

- Explain why the ‎⁠+4⁠ exists (formatting intent), not that it “extends width.”

**Mini‑project: Convert and round temperatures with reasoning**

```python
Fahrenheit = [78, 90, 60, 54]

# Copy original to avoid mutating source data during processing.

temps_copy = Fahrenheit[:]

def convert_f_to_c(f):

return (f - 32) * 5 / 9

Celsius = []

for temp in temps_copy:

c = convert_f_to_c(temp)

# Round to avoid distracting long decimals in UI/logs.

Celsius.append(round(c))

print(Celsius)
```

Goal: Copy the list, convert Fahrenheit to Celsius, round results, and explain decisions.

Your final run:

```python
Fahrenheit = [90, 100, 76, 77]

# copy list to avoid changing original data

temps_copy = Fahrenheit[:]

def convert_f_to_c(f):

return (f - 32) * 5 / 9

Celsius = []

for temp in temps_copy:

c = convert_f_to_c(temp)

# round to avoid unnecessary decimals in output

Celsius.append(round(c))

print(Celsius)

Observed output:[32, 38, 24, 25]
```

Why these comments work:

- **Copy reasoning:** Protects original data.
- **Round reasoning:** Matches display/UX expectations and avoids noise.

**Checklist for high‑signal comments**

- **Explains why:** Decision, constraint, or tradeoff behind the code.
- **Guides future readers:** Highlights assumptions or edge cases.
- **Shorter than code it clarifies:** If it’s longer, consider refactoring the code instead.
- **Non‑obvious:** Skip comments that restate plain operations.

**Common pitfalls surfaced in the lesson**

- **Repeating the obvious:** “# add 1,” “# return value,” “# print result.”
- **Confusing docstrings with comments:** Docstrings describe function purpose and usage; comments explain implementation decisions.
- **Commenting to compensate for unclear names:** Prefer renaming variables/functions first; comment only for remaining nuance.
- **Topic creep:** Stick to allowed basics—comments, inline comments, simple functions—skip advanced topics.
- **Syntax slips:** Ensure comment formatting and code stay valid; don’t overwrite function names with variables.

**Quick patterns to reuse**

Comment the intent:# Add buffer padding so titles align in UI boxes.

width = len(title) + 4

Comment data safety:# Work on a copy to keep the original list intact for audit.

temps_copy = temps[:]

Comment performance/precision tradeoff:# Round for readable output; raw floats not needed in user logs.

rounded = round(value)

Comment algorithmic choice:# Use stable sort so equal keys keep original order (important for display).

items = sorted(items, key=sort_key)

**The lesson in one line**

Write comments that reveal intent and decisions. If the code already says what, your comment should explain why.