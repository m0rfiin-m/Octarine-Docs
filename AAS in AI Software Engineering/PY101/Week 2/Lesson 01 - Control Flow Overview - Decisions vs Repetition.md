# Control Flow Overview: Decisions vs Repetition

**Date:** October 27, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 2, Lesson 1

## What You'll Learn

This lesson introduces the two fundamental types of control flow in programming: decisions (branching) and repetition (loops). You'll understand when to use each pattern and how they work together to create powerful programs.

---

## Understanding Control Flow

**Control flow** determines the order in which your code executes. Instead of running line by line from top to bottom, you can make your program:
- **Make decisions** (run different code based on conditions)
- **Repeat actions** (run the same code multiple times)

Think of control flow as traffic patterns: sometimes you choose which road to take (decision), and sometimes you circle a block multiple times (repetition).

---

## Type 1: Decisions (Branching)

### What Is It?

A decision is when your program checks a condition **one time** and picks a path based on whether the condition is True or False.

**Python Keywords:** `if`, `else`

### When to Use It

Use `if/else` when you need to check something once and execute one of two possible code blocks.

### Real-Life Example

"If it is raining, bring an umbrella. Otherwise, don't."

This is a single check that results in one action.

### Code Example: Even or Odd

```python
number = 5

# This check runs one time
if number % 2 == 0:
    print("even")
else:
    print("odd")

# Output: odd
```

**Breakdown:**
1. Python checks: "Is `number % 2` equal to 0?"
2. If True: print "even"
3. If False: print "odd"
4. Continue with rest of program

**Key Point:** The condition is evaluated **once**, and then the program moves on.

---

## Type 2: Repetition (Loops)

### What Is It?

Repetition is when your program runs the same block of code **multiple times**, typically once for each item in a collection.

**Python Keywords:** `for ... in ...`

### When to Use It

Use a `for` loop when you need to perform the same action repeatedly, especially when working with lists or collections.

### Real-Life Example

"Stack 20 plates."

You repeat the action "stack one plate" exactly 20 times.

### Code Example: Print Stars

```python
# This loop runs 3 times (once for each item in the list)
for i in [1, 2, 3]:
    print("⭐")

# Output:
# ⭐
# ⭐
# ⭐
```

**Breakdown:**
1. Python looks at the list `[1, 2, 3]`
2. For each number in the list:
   - Assign that number to variable `i`
   - Execute the indented code block (print "⭐")
3. Repeat until all items are processed

**Key Point:** The same code block runs **multiple times**, once per item in the list.

---

## Combining Loops and Decisions

The most powerful pattern in programming combines both concepts: use a loop to go through a collection, and inside the loop, use a decision to handle each item differently.

### The Pattern

```python
for item in collection:
    if condition:
        # Do this for items that match
    else:
        # Do this for items that don't match
```

**Step by Step:**
1. `for` each item in a list...
2. ...`if` that item meets a condition...
3. ...do one thing.
4. ...`else`...
5. ...do something else.

### Example 1: Weather Decision

```python
temperatures = [72, 60, 85, 51]

# 1. Loop through every temperature
for temp in temperatures:

    # 2. Make a decision about that one temperature
    if temp < 65:
        print("wear jacket")
    else:
        print("t-shirt")

# Output:
# t-shirt
# wear jacket
# t-shirt
# wear jacket
```

**Breakdown:**
- First iteration: `temp = 72` → not less than 65 → print "t-shirt"
- Second iteration: `temp = 60` → less than 65 → print "wear jacket"
- Third iteration: `temp = 85` → not less than 65 → print "t-shirt"
- Fourth iteration: `temp = 51` → less than 65 → print "wear jacket"

### Example 2: Positive or Negative

```python
numbers = [1, 200, -43]

for num in numbers:
    if num > 0:
        print("positive")
    else:
        print("negative")

# Output:
# positive
# positive
# negative
```

**Key Insight:** The decision is made **separately for each item** in the list. The loop ensures we check every item; the if/else determines what to do with each one.

---

## Decision Tree: Which Control Flow Do I Need?

Use this guide to determine which pattern fits your problem:

### Question 1: Do I need to check something one time?
**→ Use `if/else`**

**Example:** "Is the user old enough to vote?"

```python
age = 17

if age >= 18:
    print("You can vote")
else:
    print("Not yet")

# Output: Not yet
```

### Question 2: Do I need to do the same action many times?
**→ Use a `for` loop**

**Example:** "Print 'Hello' 5 times"

```python
for i in [1, 2, 3, 4, 5]:
    print("Hello")

# Output: (5 lines of "Hello")
```

### Question 3: Do I need to check every item in a list and make a different decision for each one?
**→ Use a `for` loop with an `if/else` inside it**

**Example:** "For each grade, print 'pass' or 'fail'"

```python
grades = [85, 55, 92, 68, 40]

for grade in grades:
    if grade >= 60:
        print("pass")
    else:
        print("fail")

# Output:
# pass
# fail
# pass
# pass
# fail
```

---

## Visual Comparison

### Decision (If/Else)
```
Start
  │
  ├─→ Check condition
  │       ├─→ True path (do A)
  │       └─→ False path (do B)
  │
Continue program
```

**One check → One path chosen → Move on**

### Repetition (Loop)
```
Start
  │
  ├─→ For each item:
  │   ├─→ Do action
  │   ├─→ Do action
  │   └─→ Do action
  │
Continue program
```

**Multiple iterations → Same action repeated → Move on**

### Combined (Loop + Decision)
```
Start
  │
  ├─→ For each item:
  │   ├─→ Check condition for this item
  │   │     ├─→ True: do A
  │   │     └─→ False: do B
  │   │
  │   ├─→ Next item
  │   └─→ Check condition for this item...
  │
Continue program
```

**Multiple iterations → Different action per item → Move on**

---

## Common Patterns You'll Use

### Pattern 1: Simple Validation
Check one thing, give one response.

```python
password = "secret123"

if len(password) >= 8:
    print("Strong password")
else:
    print("Password too short")
```

### Pattern 2: Batch Processing
Do the same thing to many items.

```python
prices = [10, 25, 5, 40]

for price in prices:
    discounted = price * 0.8
    print(discounted)
```

### Pattern 3: Filtering with Decisions
Process many items, handle each differently based on criteria.

```python
ages = [12, 25, 17, 30, 8]

for age in ages:
    if age >= 18:
        print(f"{age}: adult")
    else:
        print(f"{age}: minor")
```

---

## Practice Exercises

**Exercise 1: Identify the Pattern**

For each scenario, identify whether you need: (A) Decision only, (B) Loop only, or (C) Loop + Decision

1. Check if a username is available
2. Print numbers 1 through 10
3. For each email in a list, check if it's valid
4. Calculate tax on a single purchase

<details>
<summary>Solution</summary>

1. **(A) Decision only** - Single check: is username taken?
2. **(B) Loop only** - Repeat the same print action 10 times
3. **(C) Loop + Decision** - Process each email (loop) and validate it (decision)
4. **(A) Decision only** - Single calculation on one purchase

</details>

**Exercise 2: Fix the Logic**

This code should print "hot" for temps above 80 and "mild" for temps 80 or below. What's wrong?

```python
temp = 75
for i in [1]:
    if temp > 80:
        print("hot")
    else:
        print("mild")
```

<details>
<summary>Solution</summary>

The loop is unnecessary! We're only checking one temperature, so we don't need to repeat anything.

**Fixed:**
```python
temp = 75
if temp > 80:
    print("hot")
else:
    print("mild")

# Output: mild
```

**Key Point:** Don't use a loop when you only need to check or process one item.

</details>

**Exercise 3: Build the Pattern**

Write code that prints "big" for numbers greater than 50 and "small" for numbers 50 or less, for this list: `[30, 75, 50, 90, 10]`

<details>
<summary>Solution</summary>

```python
numbers = [30, 75, 50, 90, 10]

for num in numbers:
    if num > 50:
        print("big")
    else:
        print("small")

# Output:
# small
# big
# small
# big
# small
```

**Explanation:** We need both a loop (process every number) and a decision (classify each number).

</details>

**Exercise 4: Choose Your Tool**

A teacher has a list of 30 students and wants to print "Attendance complete" after marking them all present. Should they use:
- (A) Just `if/else`
- (B) Just a `for` loop
- (C) Loop + `if/else`

<details>
<summary>Solution</summary>

**(B) Just a `for` loop**

```python
students = ["Alice", "Bob", "Charlie"]  # ... (30 students total)

for student in students:
    print(f"{student}: present")

print("Attendance complete")

# Output:
# Alice: present
# Bob: present
# Charlie: present
# Attendance complete
```

**Why not if/else?** We're doing the same action (mark present) for every student. There's no condition that changes what we do.

</details>

---

## Key Takeaways

✅ **Decision (if/else) = check once, choose path** - Use when you need to make a single determination  
✅ **Repetition (for loop) = repeat action** - Use when you need to do the same thing multiple times  
✅ **Combined = process many items differently** - Loop through collection, decide what to do with each item  
✅ **One check? Just if/else** - Don't loop if you're only checking one thing  
✅ **Same action repeated? Just loop** - Don't add if/else if you're doing the same thing to every item  
✅ **Different actions per item? Loop + if/else** - Process collection with decisions for each element

**Remember:** Control flow is about routing your program's execution. Decisions branch your code into different paths. Loops repeat code blocks. Together, they give you the power to handle any collection of data with custom logic.

---

**Last Updated:** October 27, 2025
