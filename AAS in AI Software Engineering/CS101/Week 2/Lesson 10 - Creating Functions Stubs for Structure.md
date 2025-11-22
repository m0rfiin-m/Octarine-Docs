
# **Creating function stubs for structure**

Date: Saturday, November 22, 2025

Course: CS101 – AAS in AI Software Engineering

Week: 2, Lesson 10

**Purpose**

Define the skeleton of your program up front with function stubs. This keeps your plan modular, makes refactors safer, and lets you build logic incrementally without losing structure.

**Learning Objectives**

- Write clean function stubs with def lines, colons, and proper indentation.
- Pair each stub with a comment that states intent clearly.
- Call stubs in a simple “main” flow to validate structure before filling logic.
- Keep names consistent across comments, stubs, and calls.
- Understand that empty stubs return None by default.

**Prerequisites**

- Basic Python syntax: functions, indentation, calling order, print.
- Comments and pseudocode alignment from the previous lesson.
- Loops and conditionals familiarity (no test tables or advanced topics here).

**Core Idea**

Split the problem into named sections first. Write a comment that describes the intent, then a stub that matches the name. Wire all stubs together in a top-to-bottom “main” call order. Only after the structure is solid do you fill in logic line by line.

**Reference Pattern (worked example)**

```python
# read years

def read_years():

pass

# bucket years

def bucket_years():

pass

# show message

def show_message():

pass

# main

read_years()

bucket_years()

show_message()
```

Notes:

- Colons at the end of def lines.
- pass is indented exactly one level inside the function body.
- With only pass (or no return), each function returns None; printing calls will show None.

**Process**

**Step 1: Plan as comments**

Write short, intent-first comments for each section you need (read input, compute, show output). No code yet; confirm order is correct.

**Step 2: Create stubs**

Under each comment, write a matching def line and pass. Keep names tight and consistent with comments. Run once—no output is expected.

**Step 3: Wire the flow**

Add a simple “# main” comment and call your stubs in order. Run again; printing their return values should show None three times.

**Step 4: Optional placeholders**

Inside stubs, add commented pseudocode lines to mark future logic (e.g., “# bucket = years // 5”). Don’t execute yet.

**Step 5: Fill logic incrementally**

Replace pass with one line at a time (conditions, loops, lookups), re-run after each change, and keep comments aligned with intent.

**Common Mistakes and Fixes**

- Missing colon on def: add “:” at the end of the function signature.
- Bad indentation: ensure pass is indented exactly inside the function (4 spaces or a tab).
- Name drift: comment says bucket_years but def is bucketYear or buckets; standardize and grep for mismatches.
- Premature logic: stuffing multiple lines into a stub before the skeleton is validated; return to pass and build incrementally.
- Out-of-order calls: main calls don’t match the declared sequence; reorder calls to mirror the comment plan.

**Drills**

**Drill A: Stub alignment**

```python
Create three stubs: 
read_years, 
bucket_years, 
show_message. 
Add # main and call them. 


Print each call’s result and confirm None, None, None.
print(read_years())
print(bucket_years())
print(show_message())
```

**Drill B: Add a guard stub**

Insert a new step after read_years:

- Comment: “# guard negative years”
- Stub:

```python
def guard_negative_years():

pass
```

Renumber comments and call it second in main. Keep structure intact.

**Drill C: Pseudocode placeholders**

Inside bucket_years, add:

```python
# bucket = years // 5  # floor

# bucket = min(bucket, 3)
```

Leave them as comments. Confirm the plan reads top-to-bottom cleanly.

**Self-Check**

- Structure: Every comment has a matching stub directly below it; “# main” calls mirror the same order.
- Syntax: def lines have colons; pass is correctly indented.
- Behavior: Printing stub calls yields None until logic is implemented.
- Consistency: Names are identical across comments, stubs, and calls.
- Incrementality: Logic is added one line at a time, with a run after each edit.

**Notes for Your System**

Capture each exercise in Obsidian with the lesson name, a “Final Stub Skeleton” code block, and a short “Change Log” noting insertions, renumbering, and naming fixes. Keep it brief and searchable.