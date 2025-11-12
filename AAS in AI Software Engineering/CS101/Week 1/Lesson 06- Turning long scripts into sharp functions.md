
**Why Break Up Scripts**

Long, single-block scripts get brittle. Functions give you three wins: **focus**, **reuse**, and **testability**. You isolate work (calculations, formatting, decisions) into named chunks you can call anywhere.

**Core Moves You Practiced**

- **Extract calculation into a function**:

  ```python
  def calc_total(points):
  
      """Return the sum of numbers in points."""
  
      total = 0
  
      for p in points:
  
      total += p
  
  return total
  
  # Use the function instead of inline logic:
  points = [10, 5, 7, 12, 8]
  
  total = calc_total(points)
  
  Extract reporting into a function:def format_report(name, total):
  
  print("Stats for", name)
  
  print("-----")
  
  print("Total:", total)
  
  Clean Main Script Patternpoints = [10, 5, 7, 12, 8]
  
  name = "Marco"
  
  total = calc_total(points)
  
  format_report(name, total)
  
  if total > 30:
  
  print("Good job!")
  
  else:
  
  print("Keep going!")
  
  
  ```

**Rules That Keep You Safe**

- **Indentation:** Function bodies are indented 4 spaces.
- **Return vs print:** Use **return** to send data back; print is for display.
- **No self-calls:** Never call a function from inside its own definition unless you intend recursion.
- **Scope clarity:** Function parameters are local. The name you pass (e.g., **points**) must exist where you call it.
- **One job per function:** Names should state intent; bodies should do exactly that.

**Refactor Checklist**

- Identify a coherent block (calc loop, output block, decision block).
- Create a function with a clear name and parameters.
- Move the block inside; replace with a function call.
- Return values, don’t rely on globals.
- Run after each change to confirm behavior didn’t drift.

**Common Pitfalls You Saw**

- Missing indentation inside ‎⁠def⁠.
- Calling ‎⁠format_report⁠ inside itself (accidental recursion).
- Forgetting to replace ‎⁠total = 0⁠ with ‎⁠total = calc_total(points)⁠.
- Renaming data in main code without updating function call arguments.

**Mini Drills**

- Extract a decision function:def performance_message(total):

  ```python
  return "Good job!" if total > 30 else "Keep going!"
  
  Use:print(performance_message(total))
  ```
- Add a summary formatter:def format_points(points):

```python
print("Points:", points)

Call it before ‎⁠format_report⁠.
```

**Final Refactor Example**

```python
def calc_total(points):

"""Return the sum of numbers in points."""

total = 0

for p in points:

total += p

return total

def format_report(name, total):

print("Stats for", name)

print("-----")

print("Total:", total)

def performance_message(total):

return "Good job!" if total > 30 else "Keep going!"

points = [10, 5, 7, 12, 8]

name = "Marco"

total = calc_total(points)

format_report(name, total)

print(performance_message(total))
```

**Quick Review Questions**

- When should you use return vs print?
- Where do function docstrings live?
- What breaks if you rename a variable in main but not in the function call?
- What’s the benefit of one job per function?