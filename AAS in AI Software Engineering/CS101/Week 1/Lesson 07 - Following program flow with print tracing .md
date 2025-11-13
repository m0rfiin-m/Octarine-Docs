

**Why Print Tracing Matters**

When a program gives a wrong result, tracing turns the “black box” into a **step-by-step timeline**. Entry and exit prints show where data changes and which function returns first.

**Core Technique: Entry/Exit Traces**

- Entry trace:print("&gt;&gt;&gt; enter add_three")

- Exit trace with value:print("&lt;&lt;&lt; exit add_three:", total)

Use these at the start and just before return in functions.

**Patterns You Practiced**

- Simple function trace:def add_three(a, b, c):

print("&gt;&gt;&gt; enter add_three")

total = a + b + c

print("&lt;&lt;&lt; exit add_three:", total)

return total

- Loop trace to catch logic bugs:total = 0

for i in range(1, 10):

if i % 2 == 1:

total += i

print("i =", i, "total =", total)

print(total)  # final check

- Chained functions with traces:def bonus(points):

print("&gt;&gt;&gt; enter bonus")

result = points + 5

print("&lt;&lt;&lt; exit bonus:", result)

return result

def calc_points(x, y):

print("&gt;&gt;&gt; enter calc_points")

total = x * y

print("&lt;&lt;&lt; exit calc_points:", total)

return bonus(total)

**Fixing Real Bugs**

- Index vs value error:
  - Bug: ‎⁠squares.append(i * i)⁠
  - Fix: ‎⁠squares.append(numbers[i] * numbers[i])⁠
- No-op branches:
  - Bug: ‎⁠pass⁠ inside ‎⁠if⁠ with no update
  - Fix: update state, then trace:total += i

print("i =", i, "total =", total)

**Golden Rules**

- Trace at function boundaries, not random lines.
- Exit traces must show the computed value.
- Keep indentation clean; traces live inside the function body.
- Delete or comment traces after the fix to keep output clean.
- One trace line per step; avoid spam.

**Quick Drills**

- Add traces to any function you suspect, confirm inputs and outputs, then remove.
- In loops, print the changing state right after you update it.
- For nested calls, ensure you see the order: caller enter → callee enter → callee exit → caller exit.

**Final Clean Example**def square_list(numbers):

squares = []

for i in range(len(numbers)):

squares.append(numbers[i] * numbers[i])

return squares

def report(squares):

for s in squares:

print(s)

nums = [2, 4, 7]

result = square_list(nums)

report(result)

Keep this in your Obsidian as a “Trace then Clean” checklist: add entry/exit traces, fix the bug, remove traces, rerun.